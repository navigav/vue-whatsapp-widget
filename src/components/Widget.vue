<script>
import Message from "./Message.vue";
export default {
  components: {
    Message,
  },
  data() {
    return {
      control: false,
      text: null,
    };
  },
  props: {
    companyName: {
      type: String,
      default: "Widget",
    },
    textReply: {
      type: String,
      default: "Typically replies within an hour",
    },
    messages: {
      type: Array,
      default: () => ["Hi there 👋 How can I help you ?"],
    },
    companyLogo: {
      type: String,
      default: "",
    },
    phoneNumber: {
      type: String,
      default: "",
    },
  },
  methods: {
    openLink() {
      let url = "https://web.whatsapp.com/send";
      if (
        /Android|webOS|iPhone|iPad|Mac|Macintosh|iPod|BlackBerry|IEMobile|Opera Mini/i.test(
          navigator.userAgent
        )
      ) {
        url = "whatsapp://send";
      }
      const all = url + "?phone=" + this.phoneNumber + `&text=${this.text}`;
      window.open(all, "_blank");
    },
  },
};
</script>
<template>
  <div id="wp-widget">
    <div v-if="control" id="whatsapp-chat" class="hidden">
      <div class="whatsapp-chat-header">
        <div class="whatsapp-chat-avatar">
          <img
            v-if="companyLogo"
            :src="companyLogo"
            :alt="companyName + ' ' + 'Logo'"
          />
          <div v-else class="companyLogo"></div>
        </div>
        <p class="whatsapp-chat-name-block">
          <span class="whatsapp-chat-name">{{ companyName }}</span
          ><br /><small>{{ textReply }}</small>
        </p>
      </div>

      <div class="start-chat">
        <div
          pattern="https://elfsight.com/assets/chats/patterns/whatsapp.png"
          class="WhatsappChat__Component-sc-Yvjha whatsapp-chat-body"
        >
          <Message :messages="messages" :companyName="companyName" />
        </div>

        <div class="blanter-msg">
          <textarea
            id="chat-input"
            placeholder="Write a response"
            maxlength="120"
            row="1"
            v-model="text"
          ></textarea>
          <button id="send-it" @click="openLink">
            <svg viewBox="0 0 448 448">
              <path d="M.213 32L0 181.333 320 224 0 266.667.213 416 448 224z" />
            </svg>
          </button>
        </div>
      </div>
      <a class="close-chat" @click="control = false">×</a>
    </div>
    <button
      class="blantershow-chat"
      title="Start Chat"
      @click="control = !control"
    >
      <svg width="30" viewBox="0 0 24 24">
        <defs />
        <path
          fill="#eceff1"
          d="M20.5 3.4A12.1 12.1 0 0012 0 12 12 0 001.7 17.8L0 24l6.3-1.7c2.8 1.5 5 1.4 5.8 1.5a12 12 0 008.4-20.3z"
        />
        <path
          fill="#4caf50"
          d="M12 21.8c-3.1 0-5.2-1.6-5.4-1.6l-3.7 1 1-3.7-.3-.4A9.9 9.9 0 012.1 12a10 10 0 0117-7 9.9 9.9 0 01-7 16.9z"
        />
        <path
          fill="#fafafa"
          d="M17.5 14.3c-.3 0-1.8-.8-2-.9-.7-.2-.5 0-1.7 1.3-.1.2-.3.2-.6.1s-1.3-.5-2.4-1.5a9 9 0 01-1.7-2c-.3-.6.4-.6 1-1.7l-.1-.5-1-2.2c-.2-.6-.4-.5-.6-.5-.6 0-1 0-1.4.3-1.6 1.8-1.2 3.6.2 5.6 2.7 3.5 4.2 4.2 6.8 5 .7.3 1.4.3 1.9.2.6 0 1.7-.7 2-1.4.3-.7.3-1.3.2-1.4-.1-.2-.3-.3-.6-.4z"
        />
      </svg>
    </button>
  </div>
</template>
<style>
#wp-widget .whatsapp-chat-avatar,#wp-widget .whatsapp-chat-body,.Yvjha,.dRvxoz,.ixsrax,.kAZgZq{position:relative}.kAZgZq,.vzZsj{opacity:0;box-shadow:0 1px .5px rgba(0,0,0,.13)}#wp-widget .whatsapp-chat-name-block,.bMIBDo,.iSpIQi{text-align:left}#wp-widget{font-family:--system-ui,Lato,sans-serif;background:#f1f1f1}#wp-widget button{outline:0}#wp-widget a:link,#wp-widget a:visited{color:#444;text-decoration:none;transition:.4s ease-in-out}#wp-widget h1{font-size:20px;text-align:center;display:block;background:linear-gradient(to right top,#6f96f3,#164ed2);padding:20px;color:#fff;border-radius:50px}#wp-widget #whatsapp-chat{box-sizing:border-box!important;outline:0!important;position:fixed;width:350px;border-radius:10px;box-shadow:0 1px 15px rgba(32,33,36,.28);bottom:90px;right:30px;overflow:hidden;z-index:99;-webkit-animation-name:showchat;animation-name:showchat;-webkit-animation-duration:1s;animation-duration:1s;transform:scale(1)}#wp-widget button.blantershow-chat{background:#fff;color:#404040;position:fixed;display:flex;font-weight:400;justify-content:space-between;z-index:98;bottom:25px;right:30px;font-size:15px;padding:15px;border-radius:50%;border:1px solid transparent;box-shadow:0 10px 10px rgba(32,33,36,.28);cursor:pointer}#wp-widget button.blantershow-chat svg{transform:scale(1.2)}#wp-widget .whatsapp-chat-header{background:#095e54;display:inline-flex;align-items:center;padding-left:10px;width:100%;height:100%;color:#fff}#wp-widget .companyLogo{border-radius:100%;width:50px;height:50px;float:left;margin:0 10px 0 0;border:1px solid rgba(0,0,0,.2)}#wp-widget .whatsapp-chat-avatar:after{content:"";bottom:0;right:0;width:12px;height:12px;box-sizing:border-box;background-color:#4ad504;display:block;position:relative;z-index:1;border-radius:50%;border:2px solid #095e54;left:40px;top:38px}.Yvjha,.vzZsj{display:flex}#wp-widget .whatsapp-chat-avatar img{border-radius:100%;width:50px;float:left;margin:0 10px 0 0}#wp-widget .info-chat span,#wp-widget span.my-number{display:block}#wp-widget #get-label,#wp-widget span.chat-label{font-size:12px;color:#888}#wp-widget #get-nama,#wp-widget span.chat-nama{margin:5px 0 0;font-size:15px;font-weight:700;color:#222}#wp-widget #get-label,#wp-widget #get-nama{color:#fff}#wp-widget textarea#chat-input{border:none;font-family:Arial,sans-serif;width:100%;outline:0;resize:none;padding:8px;font-size:14px}#wp-widget button#send-it{width:30px;font-weight:700;border-color:transparent;cursor:pointer;background:#eee}#wp-widget button#send-it svg{fill:#a6a6a6;height:20px;width:20px}#wp-widget .start-chat .blanter-msg{display:flex;height:35px}#wp-widget a.close-chat{position:absolute;top:5px;right:15px;color:#fff;font-size:30px;cursor:pointer}@-webkit-keyframes ZpjSY{0%,25%{background-color:#b6b5ba}15%{background-color:#111}}@keyframes ZpjSY{0%,25%{background-color:#b6b5ba}15%{background-color:#111}}@-webkit-keyframes hPhMsj{15%,35%{background-color:#b6b5ba}25%{background-color:#111}}@keyframes hPhMsj{15%,35%{background-color:#b6b5ba}25%{background-color:#111}}@-webkit-keyframes iUMejp{25%,45%{background-color:#b6b5ba}35%{background-color:#111}}@keyframes iUMejp{25%,45%{background-color:#b6b5ba}35%{background-color:#111}}@-webkit-keyframes showhidden{0%{transform:scale(.5);opacity:0}}@keyframes showhidden{0%{transform:scale(.5);opacity:0}}@-webkit-keyframes showchat{0%{transform:scale(0);opacity:0}}@keyframes showchat{0%{transform:scale(0);opacity:0}}@media screen and (max-width:480px){#whatsapp-chat{width:auto;left:5%;right:5%;font-size:80%}}#wp-widget .hidden,#wp-widget .show{display:block;-webkit-animation-duration:.5s;animation-duration:.5s;transform:scale(1);opacity:1}#wp-widget .show{-webkit-animation-name:showhidden;animation-name:showhidden}#wp-widget .whatsapp-chat-body{padding:20px 20px 20px 10px;background-color:#e6ddd4}#wp-widget .whatsapp-chat-body:before{display:block;position:absolute;content:"";left:0;top:0;height:100%;width:100%;z-index:0;opacity:.08;background-image:url(https://elfsight.com/assets/chats/patterns/whatsapp.png)}.quaMo,.vzZsj{z-index:1}.vzZsj{background-color:#fff;width:52.5px;border-radius:16px;justify-content:center;align-items:center;margin-left:10px;transition:.1s}.ixsrax{-webkit-animation-duration:1.2s;animation-duration:1.2s;-webkit-animation-iteration-count:infinite;animation-iteration-count:infinite;-webkit-animation-timing-function:linear;animation-timing-function:linear;background-color:#9e9da2;-webkit-animation-name:ZpjSY;animation-name:ZpjSY}.dRvxoz,.ixsrax{height:5px;width:5px;margin:0 2px;border-radius:50%;display:inline-block;top:0}.dRvxoz{background-color:#b6b5ba;-webkit-animation-duration:1.2s;animation-duration:1.2s;-webkit-animation-iteration-count:infinite;animation-iteration-count:infinite;-webkit-animation-timing-function:linear;animation-timing-function:linear;-webkit-animation-name:hPhMsj;animation-name:hPhMsj}.kAZgZq{padding:7px 14px 6px;background-color:#fff;border-radius:0 12px 12px;transition:.3s;transform-origin:center top 0;z-index:2;margin-top:20px;max-width:calc(100% - 66px)}.kAZgZq:before{position:absolute;background-image:url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAmCAMAAADp2asXAAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAACQUExURUxpccPDw9ra2m9vbwAAAAAAADExMf///wAAABoaGk9PT7q6uqurqwsLCycnJz4+PtDQ0JycnIyMjPf3915eXvz8/E9PT/39/RMTE4CAgAAAAJqamv////////r6+u/v7yUlJeXl5f///5ycnOXl5XNzc/Hx8f///xUVFf///+zs7P///+bm5gAAAM7Ozv///2fVensAAAAvdFJOUwCow1cBCCnqAhNAnY0WIDW2f2/hSeo99g1lBYT87vDXG8/6d8oL4sgM5szrkgl660OiZwAAAHRJREFUKM/ty7cSggAABNFVUQFzwizmjPz/39k4YuFWtm55bw7eHR6ny63+alnswT3/rIDzUSC7CrAziPYCJCsB+gbVkgDtVIDh+DsE9OTBpCtAbSBAZSEQNgWIygJ0RgJMDWYNAdYbAeKtAHODlkHIv997AkLqIVOXVU84AAAAAElFTkSuQmCC");background-position:50% 50%;background-repeat:no-repeat;background-size:contain;content:"";top:0;left:-12px;width:12px;height:19px}.bMIBDo{font-size:13px;font-weight:700;line-height:18px;color:rgba(0,0,0,.4)}.iSpIQi{font-size:14px;line-height:19px;margin-top:4px;color:#111}.cqCDVm{text-align:right;margin-top:4px;font-size:12px;line-height:16px;color:rgba(17,17,17,.5);margin-right:-8px;margin-bottom:-4px}
</style>
