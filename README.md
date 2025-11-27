# Test API Challenge — Qahramonov Mirshodbek
---

## Maqsad
Test API bilan quyidagi bosqichlarda ishlay olishingizni namoyish etish:

1. Serverga `POST` yuborish (`msg` va `url` bilan)
2. Javobdan **1-qism kodni** olish
3. Callback URL orqali **2-qism kodni** qabul qilish
4. Ikkala kodni birlashtirish
5. Birlashtirilgan kod bilan `GET` so‘rov yuborish
6. API qaytargan **asl xabarni** msg ni olish

---

## Yechim ( 1 faylda )

**https://starstg.uz/api/interview/callback**

**https://starstg.uz** bu serverga ulangan domen


```js
// callback orqali olish
app.post("/api/interview/callback", (req, res) => {
  console.log("2-qism:", req.body);
  part2 = req.body.part2;
  res.json({ received: true });
});


//post yuborish
  const payload = {
    msg: "Salom, bu vazifadagi test POST sorovi, Qahramonov Mirshodbek tomonidan.",
    url: "https://starstg.uz/api/interview/callback"
  };
  const part1 = (await res.json()).part1;
  console.log("1-qism:", part1);

// kodlarni birlashtirish
const full = part1 + part2;
      console.log("Birlashtirilgan kod:", full);

// full cod bilan **msg** ni olish
const finalRes = await fetch(
        `https://test.icorp.uz/interview.php?code=${full}`
      );

      const msg = await finalRes.text();
      console.log("\nYakuniy xabar:", msg);

```

## ishlatish

## Kutubxonalarni o‘rnating:

npm install express node-fetch


## Faylni ishga tushiring:

node post.js

## Haqiqiy terminal natijasi (serverda olingan)



root@ubuntu-mini-app:~/starstg_back# node post.js



Callback ishga tushdi

2-qism: { part2: '-90b2-5d0c4addf982' }
1-qism: 027f8ef6-ddb9-4833

2-qism

Birlashtirilgan kod: 027f8ef6-ddb9-4833-90b2-5d0c4addf982

Yakuniy xabar: {"msg":"Salom, bu vazifadagi test POST sorovi, Qahramonov Mirshodbek tomonidan."}

