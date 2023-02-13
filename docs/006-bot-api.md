# Bot API
### Information
Bot Connects to Telegram Server By HTTP Requests. The Bots made in Telegraf Works with Bot API. Here is [full api reference](https://core.telegram.org/bots/api).
Bot Connects to Telegram in This Way :
```
Bot >> Bot API >> MtProto API >> Telegram
```
You your bot sends any message it sends a HTTP request to `api.telegram.org` or [your locally hosted api](https://core.telegram.org/bots/api#using-a-local-bot-api-server).
Now the Bot API request is sent to MtProto API of Telegram which finally sends the message.

> <h1><b>File Size Limits on Bot API</b></h1>
> The Telegram backend allows your bot to send files up to 2000 MB. However, the Bot API server that is responsible for translating the requests to HTTP restricts the file size to 50 MB for downloads and 20 MB for uploads.<br>Hence, if you circumvent the Bot API server that Telegram runs for you, and simply host your own Bot API server, you can allow your bot to send files up to 2000 MB.

### Calling Bot API Methods with Telegraf
You can call all methods as given at https://core.telegram.org/bots/api in telegraf by using `bot.telegram.'method'`
Here is an example in JavaScript
```js
async function sendAndReturn(){
var apiResponse = await bot.telegram.sendMessage(123445666,"Hello",{
parse_mode:"markdown"
}); // note this requires await if you want to response value from this.
return apiResponse; // it will be an object
}
```
