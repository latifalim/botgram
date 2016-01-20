# Botgram

Microframework to build Telegram bots.

~~~ js
var botgram = require("botgram");
var bot = botgram("<auth token>");

bot.command("start", "help", function (msg, reply, next) {
  reply.text("To schedule an alert, do: /alert <seconds> <text>");
});

bot.command("alert", function (msg, reply, next) {
  var args = msg.args(2);
  var seconds = parseInt(args[0]), text = args[1];
  if (seconds == NaN || !text) return next();

  setTimeout(function () {
    reply.text(text);
  }, seconds * 1000);
});

bot.command(function (msg, reply, next) {
  reply.text("Invalid command.");
});
~~~

Main features:

 - Simple, intuitive API.
 - Quick setup; just put your auth token and you're in business.
 - Powerful, [connect]-style message handling and filtering.
 - Exposes all functionality in the bots API, including custom keyboards,
   force reply, chat actions, deep linking...
 - Ability to stream downloads and uploads.

Follow the [tutorial], take a look at more [examples],
or consult the [documentation].



[connect]: https://github.com/senchalabs/connect

[tutorial]: https://github.com/jmendeth/botgram/blob/master/docs/tutorial.md
[examples]: https://github.com/jmendeth/botgram/tree/master/examples
[documentation]: https://github.com/jmendeth/botgram/blob/master/docs/index.md
