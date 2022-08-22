# Http

Http ဆိုတာ Hypertext Transfer Protocol ဖြစ်ပြီး World Wide Web ရဲ့ အခြေခံအုတ်မြစ်တစ်ခုဖြစ်သည်။ Http သည် application layar protocol တစ်ခုဖြစ်ပြီး client နဲ့ server ကြား information တွေကို transfer လုပ်ရန် client ဘက်မှ Request ပို့ပြီး server က responses ပြန်သည်။ Http request တစ်ခုတွင် request url, http method, Http request headers, body(Optional) တို့ပါဝင်ရသည်။ JavaScript တွင် fetch api ကိုသုံး၍ http request များပြုလုပ်နိုင်သည်။ Http တွင် 1.0, 1.1,2,3 ထိ version များရှိနေပြီဖြစ်သော်လည်း 1997 က ထုတ်ခဲ့သည် Http 1.1 သည် အခုအချိန်ထိ အသုံးများဆဲဖြစ်နေသည်။

## Http methods

Http methods ကတော့ server ကို request လုပ်တဲ့နေရာမှာသုံးတဲ့ request method အမျိုးအစားတွေပဲဖြစ်ပါတယ်။ Get, Post, Put, Patch နဲ့ Delete method ဆိုပြီး အသုံများတဲ့ methods 5 မျိုးရှိပါတယ်။ သူတို့က Database operations တွေဖြစ်တဲ့ Create, Read, Update, Delete (CRUD) တွေလုပ်ဆောင်ကြပါတယ်။ တခြား Head, Options, connect, trace စတဲ့ အသုံမများတဲ့ method တွေလည်း ရှိသေးသည်။

**Get** Method သည် server က data တွေတောင်းခံတဲ့နေရာမှာသုံးပါတယ်။များသောအားဖြင့် http client method အဖြစ် defaultပေးထားလေ့ရှိပါတယ်။

**Post** method သည် Server ကို client ကနေ data ပိုတဲ့အခါသုံးပါတယ်။ အထူသဖြင့် database မှာ data တွေဖန်တီးချင်တဲ့ အခါမှာသုံးပါတယ် ဖန်တီးချင်တဲ့ data ကိုတော့ request body မှာထည့်ရပြီး client ဘက်ကနေ တစ်ခါတည်း သယ်သွားပေးရပါတယ်။

**Put** နဲ့ **Patch** Method ကတော့ database ထဲက data
တွေ update လုပ်ဆောင်ရမှာ သုံးပါတယ်။ ဒီ method
နှစ်ခုက စင်သလိုထင်ရပေမဲ့ အဓိက ကွားခြားချက်တစ်ခုရှိပါတယ်။ **Put** သည် database ထဲက data ရဲ့ resources တွေ အကုန် ပြန်ထည့်ပေးရမှာဖြစ်ပြီး **Patch** ကတော့ တစ်စိတ်တစ်ပိုင်းပဲ့ ပြဆင်တာဖြစ်ပြီး ကိုယ်ပြင်ချင်တဲ့ Resources တစ်စိပ်တစ်ပိုင်းကိုသာ ထည့်ပေးဖို့လိုပါတယ်။
Delete method ကတော့ database ထဲက dataတစ်ခုကို ဖျက်ချင်တဲ့ အခါမှာ သုံးပါတယ်။

## Status code

Http request ပိုပြီးရင် response ပြန်ပါတယ်။ status code
ဆိုတာ request တစ်ခုရဲ့ success ဖြစ်လား စတဲ့ အခြေအနေတွေကို ဖော်ပြတဲ့ နံပါတွေဖြစ်ပါတယ်။ status code မှာ
**1xx**, **2xx**, **3xx**, **4xx**, **5xx** ဆိုပြီးတော့ အစု ငါးခုရှိပါတယ်။ အတွေ့ရများတာတော့ **2xx**, **4xx**, **5xx** တွေပဲဖြစ်ပါတယ်။

**2xx** တွေကတော့ successful ဖြစ်တာကိုပြတဲ့ code တွေဖြစ်သည်။

**200** - ok သည် request လုပ်တဲ့ data တွေ response အောင်မြင်စွာပြန်လာတာကိုဆိုလိုပါတယ်။

**201** - created ကတော့ server မှာ data တွေ အသစ်ဖန်တီးတဲ့ Post
method တွေ success ဖြစ်ခဲ့ရင် ပြတဲ့ code ဖြစ်ပါတယ်။

**4xx** တွေကတော့ client ဘက်က request မှာ error ဖြစ်တာကို ပြတဲ့ code တွေဖြစ်ပါတယ်။

**400** - Bad request သည် client က request မှာ syntax
လွဲနေတာမျိုးဖြစ်ခဲ့လျှင် ပြတဲ့ code ဖြစ်သည်။

**401** - Unauthorized သည် severက user authentication ဖြစ်ဖို့လိုတယ်လို့ သမှတ်ထားတဲ့ route တွေမှာ authenticated မဖြစ်နေရင်
ပြသည်။

**402** - payment required ကတော့ အနာဂတ်မှာ အသုံးပြုဖို့ payment system တွေအတွက် ပြုလုပ်ထားခဲ့တဲ့ code ဖြစ်သည်။ ဒါပေမဲ့ အသုံပြုတာ မရှိသလောက်ကို နည်းနေသေးသည်။

**403** - Fobidden သည် request ကို server က နာလည်‌‌
ပေမဲ့ process လုပ်ဖို့ ငြင်းပယ်တဲ့ အခါမျိုးမှာပြတဲ့ code ဖြစ်ပါတယ်။

**404** - Not found သည် server က request လုပ်တဲ့
Resources တွေကို ရှာမတွေ့တဲ့ အခါမှာ ပြတဲ့code ဖြစ်ပါတယ်။ 404. သည် web မှာ ခနခနဖြစ်တတ်သောကြောင့်
အသိများဆုံး code များထဲတွင်လည်း ပါသည်။

**405** - Method Not Allowed သည် server က Http request method ကိုသိပေမဲ့ api ကခွင့်မပြုထားခြင်းမျိုးဖြစ်သည်။ ဥမမာဆိုလျှင် api က data resource တစ်ခုခုကို
ဖျက်ဖို့ Delete method ကို ခွင့်မပြုထားချင်းမျိုးဖြစ်သည်။

**5xx** code များသည် server ဘက်မှာ error ဖြစ်လျှင်ပြတဲ့ code များဖြစ်သည်။

**500** - Internal Server Error သည် server က ဘယ်လို‌‌ကိုင်တွယ်ရမယ်မှန်း မသိတဲ့ အခြေအနေတွေကို ရင်ဆိုင်ရတဲ့ အခါမှာပြသည်။

**501** - Not Implemented ကတော့ server က support မလုပ်တဲ့ method တွေကို request လုပ်တဲ့အခါမှာ ပြတဲ့ code
တွေဖြစ်ပါတယ်။ server တစ်ခုက မဖြစ်မနေ support လုပ်ဖို့
လိုအပ်တဲ့ method တွေကတော့ Get နဲ့ Head method တိုဖြစ်ပါတယ်။

**503** - Service Unavailable သည် server က request တွေကို handle လုပ်ဖို့ အဆင်သင့်မဖြစ်သေးတဲ့ အချိန်မျိုးမှာ ပြပါတယ်။ ဘာကြောင့်လဲဆိုတော့ maintenance ကြောင့်
Server down နေတာမျိုး overloadd ဖြစ်နေတာမျိုးတွေကြောင့်ဖြစ်ပါတယ်။
ဒီထဲမပါသေးတဲ့ တခြား status code တွေလည်း များစွာ ရှိပါသေးတယ်။
တခြား status code အစုတွေဖြစ်တဲ့ 1xx ဟာဆိုရင် Information responses တွေမှာ ပြတာဖြစ်ပြီး
3xx ကတော့ redirect ဖြစ်သွားတဲ့ အခါမျိုးမှာ ပြတာဖြစ်ပါတယ်

## What is a **url**

![urlSample](<images/image%20(1).png>)

**Url** ဆိုတာ Uniform Recourse Locater ဖြစ်ပြီး web address တွေဖြစ်ကြပါတယ်။ ပုမှန်အားဖြင့် broswer ရဲ့
Address bar မှာ မြင်ရပါတယ်။ url တွေက unique ဖြစ်ကြသည်။ Url ဆိုတာ တကယ်တော့ uniform resource identifier (Uri) တွေရဲ့ အစိတ်အပိုင်းတစ်ခုဖြစ်ပါတယ်။
Example ပုံအတိုင်းပြောပြရရင် Uri တစ်ခုမှာ "http://" လိုတွေ့ရတဲ့ scheme၊ en.wikipdedia.org ဆိုတဲ့ domain name ရယ် /နောက်က file လမ်းကြောင်းတွေရယ် , ? နောက်က query param တွေရယ် နောက်ဆုံး # နောက်က anchor fragment တွေပါဝင်ပါတယ်။ query param တစ်ခုမှာ
= ရှေ့ကဟာက key ဖြစ်ပြီး နောက်က value ဖြစ်ပါတယ်။
ပုံမှာဆိုရင် "title" ဆိုတဲ့ key ကိုခေါ်ရင် "Burrito" ဆိုတဲ့ value ကိုရမှာဖြစ်ပါတယ်။ uri တစ်ခုမှာ query param တစ်ခုမကရှိနိုင်ပြီး တစ်ခုနဲ့ တစ်ခုကြား & နဲ့ဆက်ကြပါတယ်။
Http request ဆိုတာ ထို url/uri တွေကို request လုပ်ကြရတာဖြစ်ပါတယ်။

## Content-Type

**Content-Type** ဆိုတာက request တစ်ခုလုပ်ရင် headers
မှာထည့်ပေးရတဲ့ request ထဲက body ရဲ့ အမျိုးအစားဖြစ်ပါတယ်။ Post, Put, Patch စတဲ့ body ပါတဲ့ request တွေမှာထည့်ပေးရပါတယ်။ Content-Type မှာ application/json
သည် အသုံးအများဆုံးဖြစ်ပြီး
application/x-www-form-urlencoded , multipart/form-data, နဲ့ တခြားခြားသော Content-Type များစွာလည်း ရှိပါသေးသည်။ application/json data ပိုရာတွင်သုံးတာဖြစ်ပြီး json ဆိုတာ JavaScript Object Notation ဖြစ်ပြီး
JavaScript object ပုံစံဖြစ်၍ သိပ်မစိမ်းပေ။ applicationx-www-form-urlencoded နဲ့ multipart/form-data နှစ်ခုလုံးကတော့ form data တွေကို Post
request လုပ်တဲ့နေရာမှာသုံးကြတာဖြစ်သည်။ မတူတာကတော့ application/x-www-form-urlencoded သည် text form data တွေပို့ရာမှာ သုံးတာဖြစ်ပြီး
multipart/form-data ကတော့ binary data တွေ file တွေ
Upload လုပ်တဲ့နေရာတွင်သုံးကြသည်။
