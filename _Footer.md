`package com.hks.weixin.mp;

import java.io.IOException;
import java.util.Map;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import org.apache.commons.lang3.StringUtils;

import me.chanjar.weixin.common.error.WxErrorException;
import me.chanjar.weixin.common.session.WxSessionManager;
import me.chanjar.weixin.mp.api.WxMpInMemoryConfigStorage;
import me.chanjar.weixin.mp.api.WxMpMessageHandler;
import me.chanjar.weixin.mp.api.WxMpMessageRouter;
import me.chanjar.weixin.mp.api.WxMpService;
import me.chanjar.weixin.mp.api.impl.WxMpServiceImpl;
import me.chanjar.weixin.mp.bean.message.WxMpXmlMessage;
import me.chanjar.weixin.mp.bean.message.WxMpXmlOutMessage;
import me.chanjar.weixin.mp.bean.message.WxMpXmlOutTextMessage;

/**
 * 微信公众号示例
 * @author 范瑞丰
 * @since 2018年7月19日 上午10:28:35
 */
public class WxMpServlet extends HttpServlet {
	private static final long serialVersionUID = 164582614918821430L;
	protected WxMpInMemoryConfigStorage wxMpConfigStorage;
	protected WxMpService wxMpService;
	protected WxMpMessageRouter wxMpMessageRouter;

	@Override
	public void init() throws ServletException {
		super.init();

		wxMpConfigStorage = new WxMpInMemoryConfigStorage();
		wxMpConfigStorage.setAppId("..."); // 设置微信公众号的appid
		wxMpConfigStorage.setSecret("..."); // 设置微信公众号的app corpSecret
		wxMpConfigStorage.setToken("..."); // 设置微信公众号的token
		wxMpConfigStorage.setAesKey("..."); // 设置微信公众号的EncodingAESKey

		wxMpService = new WxMpServiceImpl();
		wxMpService.setWxMpConfigStorage(wxMpConfigStorage);

		WxMpMessageHandler handler = new WxMpMessageHandler() {
			@Override
			public WxMpXmlOutMessage handle(WxMpXmlMessage wxMessage, Map<String, Object> context,
					WxMpService wxMpService, WxSessionManager sessionManager) throws WxErrorException {
				WxMpXmlOutTextMessage m = WxMpXmlOutMessage.TEXT().content("测试加密消息").fromUser(wxMessage.getToUser())
						.toUser(wxMessage.getFromUser()).build();
				return m;
			}
		};

		wxMpMessageRouter = new WxMpMessageRouter(wxMpService);
		wxMpMessageRouter.rule().async(false).content("哈哈") // 拦截内容为“哈哈”的消息
				.handler(handler).end();

	}

	@Override
	protected void service(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException {

		response.setContentType("text/html;charset=utf-8");
		response.setStatus(HttpServletResponse.SC_OK);

		String signature = request.getParameter("signature");
		String nonce = request.getParameter("nonce");
		String timestamp = request.getParameter("timestamp");

		if (!wxMpService.checkSignature(timestamp, nonce, signature)) {
			// 消息签名不正确，说明不是公众平台发过来的消息
			response.getWriter().println("非法请求");
			return;
		}

		String echostr = request.getParameter("echostr");
		if (StringUtils.isNotBlank(echostr)) {
			// 说明是一个仅仅用来验证的请求，回显echostr
			response.getWriter().println(echostr);
			return;
		}

		String encryptType = StringUtils.isBlank(request.getParameter("encrypt_type")) ? "raw"
				: request.getParameter("encrypt_type");

		if ("raw".equals(encryptType)) {
			// 明文传输的消息
			WxMpXmlMessage inMessage = WxMpXmlMessage.fromXml(request.getInputStream());
			WxMpXmlOutMessage outMessage = wxMpMessageRouter.route(inMessage);
			response.getWriter().write(outMessage.toXml());
			return;
		}

		if ("aes".equals(encryptType)) {
			// 是aes加密的消息
			String msgSignature = request.getParameter("msg_signature");
			WxMpXmlMessage inMessage = WxMpXmlMessage.fromEncryptedXml(request.getInputStream(), wxMpConfigStorage,
					timestamp, nonce, msgSignature);
			WxMpXmlOutMessage outMessage = wxMpMessageRouter.route(inMessage);
			response.getWriter().write(outMessage.toEncryptedXml(wxMpConfigStorage));
			return;
		}

		response.getWriter().println("不可识别的加密类型");
		return;
	}
}
`