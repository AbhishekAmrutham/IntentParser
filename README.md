# IntentParser สำหรับ Python

Intent parser อย่างง่ายใช้สำหรับทำ chatbot และอื่นๆ

## เริ่มต้น

สิ่งที่ต้องทำก็คือ กำหนดพฤติกรรมของ Intent parser สอนมัน แล้วก็เสร็จ!
```
 intent = ip.intentParser({
        'description' : {
                        "type" : 'ถามเพลงโปรด',
                        "args" : [(ip.REGEX,"ชื่อเพลง"), (ip.OPTIONAL, "แนวเพลง")],
                        "keyword" : [(ip.REQUIRE, "คำบอก"),(ip.OPTIONAL, "แนวเพลง"),(ip.REGEX, "ชื่อเพลง")]},
        'คำบอก' : ['ผม', 'ชอบ', 'เจ๋ง', 'โปรด', 'เพลง', 'แนว'],
        'แนวเพลง' : ["ป๊อป","ร็อค","แจ๊ส","คันทรี","เพลงไทย"],
        'ชื่อเพลง' : ' เพลง (?P<location>.*)'
    })
```
นี่คือขั้นตอนการสร้างทั้งหมด ต่อไปคือการสอน
```
intent.teachWords(["ผมชอบเพลง Yellow", "ฉันรักเพลงแจ๊ส", "เพลงไทยสนุกมาก"])
#ใข้ teachWords() พร้อมกับ list ของประโยคที่จะฝึก
#สอนกี่ครั้งก็ได้แล้วแต่สถานการณ์
```
มันทำอะไรได้บ้าง?
```
print(intent.getResult("ผมชอบเพลงร็อค"))
print(intent.getResult("เพลงคันทรีสนุกมาก"))
```
ผลที่ได้
```
{'type': 'ถามเพลงโปรด', 'args': [('แนวเพลง', ['ร็อค'])], 'confidence': 0.75}
{'type': 'ถามเพลงโปรด', 'args': [('แนวเพลง', ['คันทรี'])], 'confidence': 0.6666666666666666}
```
ใช้ได้ๆ!

### วิธีการติดตั้ง
แค่ดาวน์โหลด .zip ไปแตกไฟล์จากนั้นรันคำสั่งตามนี้

```
$ cd IntentParser
$ python setup.py install
```

## Contributing
โมดูลนี้ผม([nonkung51](https://github.com/nonkung51)) สร้างแค่คนเดียวครับ ถ้าอยากปรับตรงไหนก็ pull request มาได้เลยครับ 

## License

ลิขสิทธิ์เป็น Apache License 2.0 - ดูที่ [LICENSE.md](LICENSE.md) สำหรับรายละเอียด แต่ถ้าอยากใช้นอกเหนือจากขอบเขตนี้ก็คุยกันได้ครับ
