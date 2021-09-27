# Mta-Ready

const Discord = require("discord.js");
const Gamedig = require("gamedig");
module.exports = client => {
  client.user.setStatus("idle");

  //idle bosta
  //dnd rahatsiz etmeyin
  //online online
  console.log(`${client.user.username} ismi ile giriş yapıldı!`);
  setInterval(() => {
    let sv = "54.36.0.81";
    Gamedig.query({
      type: "mtasa",
      host: sv
    }).then(sunucu => {
      client.user.setActivity(`Sunucuda ${sunucu.raw.numplayers} Kişi`, {
        type: "PLAYING"
      });
    });
  }, 3000);

  //LISTENING = DİNLİYOR
  //WATCHING = İZLİYOR
  //PLAYING = OYNUYOR
  console.log(
    `${client.user.username}: Şu an ` +
      client.channels.size +
      ` adet kanala, ` +
      client.guilds.size +
      ` adet sunucuya ve ` +
      client.guilds.reduce((a, b) => a + b.memberCount, 0).toLocaleString() +
      ` kullanıcıya hizmet veriliyor!`
  );
};
//developed By Lowzy
