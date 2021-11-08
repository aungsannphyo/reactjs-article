## useEffect vs useLayoutEffect

```react
useEffect(() => {
  // do side effects
  return () => /* cleanup */
}, [dependency]);

useLayoutEffect(() => {
  // do side effects
  return () => /* cleanup */
}, [dependency]);
```

useEffect ကဘယ်လိုအလုပ်လုပ်သလဲဆိုရင် ***asynchronously*** ပုံစံအလုပ်လုပ်တယ်, render ပီးမှ useEffect ထဲရေးထားတဲ့ For Example - Api Call အဲ့အရာတွေရဲ့ ရလာတဲ့ result ကို screen ပေါ်ကိုပစ်တင်တယ်။

အဲ့တာကဘယ်လိုလဲဆိုရင်...

၁ ။ ဘယ်လိုနေနေ ပထမဆုံးတစ်ကြိမ်တော့ Render လုပ်မယ် (state change or parent re-renders)

၂ ။  React ကနေ component တွေကို Render လုပ်မယ် (Calls Jsx)

၃ ။ Screen က Updated ဖစ်သွားမယ်

၄ ။ အာ့တွေအကုန်ပီးမှ useEffect ကို Run မယ်



useLayoutEffect ကျမတူတော့ဘူး သူက ကျ ***synchronously*** အလုပ်လုပ်တယ်, သူလဲ render ပီးမှအလုပ်လုပ်တယ်ဆိုပေမဲ့  Screen ပေါ်ပစ်မတင်မှာ Updated လုပ်တာ

အဲ့တာဘယ်လိုလဲဆိုရင်

၁ ။ ဘယ်လိုနေနေ ပထမဆုံးတစ်ကြိမ်တော့ Render လုပ်မယ် (state change or parent re-renders)

၂ ။  React ကနေ component တွေကို Render လုပ်မယ် (Calls Jsx)

၃ ။ useLayoutEffect Run မယ် အဲ့အချိန်မှာ React က Screen ပေါ်ပစ်တင်ဖို့စောင့်ရမယ်

၄ ။ Screen က Updated ဖစ်သွားမယ်



များသောအားဖြင့်ကျွန်တော်တို့ React ရေးတဲ့အခါမှာ State or Props ကိုချက်ချင်းကြီးပြောင်းလဲသွားဖို့မလိုသလို Page ကိုလဲချက်ချင်းကြီး affect ဖစ်သွားစရာမလိုပါဘူး ( 99% များသောအားဖြင့်ပေါ့)

For Example 

၁ ။ Api ကနေ Data လှမ်းယူတဲ့အခါမျိုးတွေ

၂ ။ Event Handler လုပ်တဲ့အခါမျိုးတွေ

၃ ။ State ကို reset လုပ်ပြန်ပီး Modal Dialog တွေကို ပေါ်ချင်ဖျောက်ချင်တဲ့အခါမျိုးတွေ

အဲ့လိုအခြေအနေမျိုးတွေဆိုများသာအားဖြင့် useEffect နဲ့ပဲသုံးကြတယ်။



အဲ့နှစ်ခုရဲ့အဓိကကွာခြားချက်နဲ့ဘယ်လိုနေရာမှာသုံးသင့်သလဲပြောပါဆိုရင်

 DOM ကို interact လုပ်စရာမလိုဘူး ဆိုရင် useEffect ကိုသုံး

DOM ကို mutate လုပ်ရမယ် ချက်ချင်း Screen မှာပြောင်းလဲချင်ရင် useLayoutEffect ကိုသုံး။ တကယ်လို့ကိုယ်က input value အပြောင်းအလဲပေါ်မူတည်ပီး Screen Update လုပ်ချင်လို့ ref နဲ့သုံးချင်တယ်ဆို ပိုသေချာအောင် code တွေ မ run ခင် အကုန် up-to-date ဖစ်နေအောင် useLayoutEffect ကိုသုံးသင့်တယ်

```javascript
const ref = React.useRef()
React.useEffect(() => {
  ref.current = 'some value'
})

// then, later in another hook or something
React.useLayoutEffect(() => {
  console.log(ref.current) // <-- this logs an old value because this runs first!
})
```

