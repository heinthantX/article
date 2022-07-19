# Event loop

![event loop](./images/javascript-event-loop-step-1.png)

**JavaScript** မှာ event loop ဆိုတဲ့ runtime model တစ်ခုရှိသည်။ JavaScript code တွေဟာ environment တစ်ခုမှာ အခြေပြုပြီး အလုပ်လုပ်ကြတာဖြစ်ပြီး environment ဆိုရာမှာ များသောအားဖြင့် Browser များဖြစ်ပြီး Chrome, Firefox, Microsoft edge, Safari... အစရှိတဲ့ browser တွေဖြစ်ပါတယ်။ **JavaScript** သည် high level, interpreted, single-threaded programing language တစ်ခုဖြစ်သည်။ single-thread ဆိုသည်မှာ တစ်ချိန်တွင် အလုပ် တစ်ခုတည်းကိုသာ လုပ်နိုင်ခြင်းကို ဆိုလိုတာပါ။ ထိုသို့ အလုပ် များကို တစ်ခုပြီး တစ်ခု အစဉ်လိုက်လုပ် ဆောင်စေရန် event loop ကို အသုံး ပြုထားသည်။

## Execution context

Execution context ဆိုတဲ့ စကားလုံးကို ခွဲခြမ်းကြည့်ရလျှင် execution ဆိုတာဟာ code တတွေကို Compile or interpret လုပ်တာဖြစ်ပြီး context ဆိုတာ အခြေအနေတစ်ခုကို ဆိုလိုတာ ဖြစ်သည်။ တစ်နည်းအားဖြင့် JavaScript engine က run ရမည့် task များကို ဆိုလိုခြင်းဖြစ်သည်။ global execution context များကိုတည်ဆောက် သည်။ ထို့နောက် function တစ်ခုကို ခေါ်လိုက်လျှင် JavaScript သည် function execution context တစ်ခုကို တည်‌ဆောက်ပေးသည်။

## Heap

Heap ဆိုသည်မှာ Variable တွေ Function တွေကိုသိမ်ပေးတဲ့ memory နေရာတစ်ခုဖြစ်သည်။

## Call stack

execution context တွေကို အစဉ်လိုက် execute လုပ်ဖို့အတွက် တာဝန်ယူသည်။ Execution context တွေကို last-in-first-out(LIFO) အနေနဲ့စီမံပါတယ်။

```javascript
function first() {
  console.log('first');
}
function second() {
  first();
  console.log('second');
}
function third() {
  second();
  console.log('third');
}
third();
```

**third()** function ကိုခေါသဖြင့် **third()** Function execution context ကိုတည်ဆောက်သည်။ **third()** function ထဲတွင် **second()** ကိုခေါ်သဖြင့် **second()** function execution context ကိုတည်ဆောက်သည်။ ထို့ကဲ့သို့ call stack ထဲတွင် **third()->second()->first()** ကိုအဆင့်ဆင့်တည်ဆောက်သည်။ ထိုနောက် last-in-first-out အနေဖြင့် **first()->second()->third()** အစဉ်လိုက်
execute လုပ်သည်။

```
output:
  first
  second
  third
```

## Stack overflow

Call stack တွင် fixed sized ရှိသည်။ fixed size သည်
web browser or nodeJs စတဲ့ host environment ပေါ်တွင် မူတည်သည်။
function fn() {
fn();
}
fn();

**fn()** သည် အဆုံးမရှိသဖြင့် function execution context များ သည် များလွန်းသော‌ကြောင့် call stack ပေါ်တွင် မသိမ်းနိုင်တော့ပဲ JavaScript engine သည် Maximum call stack size exceeded error ပြမည် ဖြစ်သည်။

## Queque

```javascript
function sayHello() {
  console.log('Hello');
}
setTimeout(sayHello, 1000);
console.log('Me First');
```

setTimeout ကိုခေါ်လိုက်တာနဲ့ တပြိုင်နက် **sayHello()** ဟာ Call Stack ထဲကနေ ထွတ်သွားမှာဖြစ်ပြီးတော့ Web API ဘက်မှာ Timer တစ်ခု စပြီး spin သွားမှာဖြစ်ပါတယ်။ ဒီမှာတော့ တစ်စက္ကန့် ပါ။ ပြီးမှ queue ထဲကို ပို့ပါတယ်။
‘Me First’ ဆိုပြီး log ထွက်လာမယ်။ တစ်စက္ကန့်ကြာပြီးတဲ့အချိန်မှာ Hello ဆိုပြီးထွက်လာပါမယ်။ queue ထဲမှာတော့ function တွေကို first-in-first-out အနေနဲ့ အစဉ်လိုက် execute လုပ်ပါတယ်။

```javascript
console.log('Hi!');
setTimeout(() => {
  console.log('Execute immediately.');
}, 0);
console.log('Bye!');
```

setTimeout function က 0s ဖြစ်နေပေမယ့် 'Execute immediately' က အရင်မထွက်က်ပါဘူး။ ဘာကြောင်လဲဆိုတော့ event loop က call stack ထဲက function တွေကို execute လုပ်မပြီးမချင်း Queue ထဲက ဟာတွေကို execute မလုပ်လို့ပါ။ 'bye!' log ပြီးမှ 'Execute immediately' ကိုlog ထုတ်ပါတယ်။

```
output:
  Hi!
  Bye!
  Execute immediately!
```
