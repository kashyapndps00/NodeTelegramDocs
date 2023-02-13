# Filters in Telegraf
You can make `bot.on` listner with `message("text")` or any other filter
> **Note**<br>
> bot.on("message"|"other_type") has been deprecated. It may be removed in future versions. So prefer new filters.

# Available Types
You can see available types by your code editor like VISUAL STUDIO CODE (VS CODE) it will auto suggest you the types.
Here are commonly used types :
```
text
photo
message
```
# Example
Here is an example how to use filters
```js
const { Telegraf } = require("telegraf");
const { message } = require( "telegraf/filters" ); // import this
const bot = new Telegraf(process.env.BOT_TOKEN); // process.env.BOT_TOKEN means you have to add bot token or use env BOT_TOKEN

bot.on(message("text"),async (ctx,next)=>{
// next is added because other listners below this wont work if await next(); is not added
await next();
})
```

### More Details
Listners can be array. For instance :
```js
bot.on([message("text"),message("photo")],async (ctx)=>{
ctx.reply("Received Text or Photo");
// check if ctx has text
if(ctx.has(message("text")){
ctx.reply("It is text");
}
else if(ctx.has(message("photo")){
ctx.reply("It is photo");
}
})
```

Here `.has` check has been also used. `ctx.has(filter)` returns boolean (true or false) by checking if ctx has the filter.
