## djs-threads 🚀
**Tüm Discord.js versiyonları için çok hızlı thread integrasyonu 😃**

**📚Örnekler:**

**✨Thread oluşturma**

 ```js
const Discord = require("discord.js")
const client = new Discord.Client()
const threads = require("djs-threads")
const threadEvents = threads.events
threads.login("TOKEN", 98303) //98303 intent sayısıdır ve "98303" tüm intent izinlerinin açık olduğunu ifade eder siz kendi botunuzun intent izinlerinin sayısını hesaplamak isterseniz https://discord-intents-calculator.vercel.app/ sitesini kullanabilirsiniz
client.login("TOKEN")

client.on("ready", () => {
console.log("djs hazır")
})
threadEvents.on("ready", () => {
console.log("djs-threads hazır")
})

client.on("message", (msg) => {
	if(!msg.guild) return
	if(msg.author.id == "user_id") {
	new threads.ThreadManager(msg.channel.id).create({
	name: 'neden-windows-archtan-daha-iyi',
    autoArchiveDuration: 60
	})
	}
})
```

**💻Tüm fonksiyonlar**

```js
//THREAD OLUŞTURMA
new threads.ThreadManager("GUILD_TEXT_CHANNEL_ID").create(OPTIONS_OBJECT)

//THREADLERE KATILMA
new threads.ThreadManager("GUILD_THREAD_CHANNEL_ID").join()

//THREADLERDEN ÇIKMA
new threads.ThreadManager("GUILD_THREAD_CHANNEL_ID").leave()

//THREADLERDEN ÜYE ATMA
new threads.ThreadManager("GUILD_THREAD_CHANNEL_ID").remove("USER_ID")

//THREADLERE ÜYE EKLEME
new threads.ThreadManager("GUILD_THREAD_CHANNEL_ID").add("USER_ID")

//THREAD ÜYESİNİN VERİSİNİ ALMA
const manager = new threads.ThreadManager("GUILD_THREAD_CHANNEL_ID")
const fetchMember = await manager.fetchMember("USER_ID")

//THREADDE BULUNAN ÜYELERİ ÇEKME
const manager = new threads.ThreadManager("GUILD_THREAD_CHANNEL_ID")
const getMembers = await manager.members()

//KANALDAKİ THREADLERİ ALMA
const manager = new threads.ThreadManager("GUILD_TEXT_CHANNEL_ID")
const getMembers = await manager.getThreads({public: true, archived: true}) //bu size kanaldaki tüm herkese açık ve arşivlenmiş olan thread kanallarını verecektir

```

**💻Tüm eventler**

```
ready
threadCreate
threadDelete
threadUpdate
threadMemberUpdate
threadMembersUpdate
```

**NOT: BU PAKET DAHA BİTİRİLMEMİŞTİR**

**❤ ile ! SpongeBed#8181 Tarafından Yapıldı**
