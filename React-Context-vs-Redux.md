# React Context vs Redux

React မှာ State Management အတွက် Redux ကိုများသောအားဖြင့်သုံးကြတယ်။ အဲ့နေရာမှာ မေးခွန်းရှိလာပီ React Version 16.3.0 မှာစတင်မိတ်ဆက်ခဲ့တဲ့ Context Api ကိုသုံးမရဘူးလားပေါ့။ Context ကလဲ State  ကို Provider မှာ ထားပီး  Component Tree တစ်ခုလုံးကို အပေါ်ကနေစပီးအောက်ဆုံးထိ Context Api နဲ့သယ်သွားလို့ရတဲ့အတွက် Props Chains or Props Drilling  မဖစ်တဲ့အားသာရှိတယ် ပြောရရင် State Management အနေနဲ့သုံးလို့ရတယ်။ 

Props Drilling ဆိုလို့ပြောရရင် Context ကိုမသုံးပဲ  Component Composition သုံးပိးရေးလို့ရတယ်ဆိုပေမဲ့ ကိုယ့်ရဲ့Nested Child Component တွေအရမ်းများရင်ကျလဲအဆင်မပြေပြန်ဘူး။

Component တစ်ခုကို Provider တစ်ခုနဲ့ wrap ပီးသူ့ Component နဲ့သုံးသွားလို့ရတယ်။အဲ့လို အားသာချက်ရှိနေတာကိုဘာလို့ State Management အတွက် Redux ကိုသုံးနေသေးလဲဆိုပီးမေးစရာရှိလာတယ်။ အောက်က example ကိုကြည့်လိုက်ရအောင်

```react
return (
	<AuthContextProvider>
    	<ThemeContextProvider>
        	<LanguageContextProvider>
                <GetAllUserProvider>
                	<UpdateUserProvider>
                    	<Users />
                    </UpdateUserProvider>
                </GetAllUserProvider>
            </LanguageContextProvider>
        </ThemeContextProvider>
    </AuthContextProvider>
)
```

အပေါ်က example မှာဆို တစ်ခုနဲ့တစ်ခု Nested ဖစ်လွန်းတယ် ကိုယ်ရဲ့ Project မှာက အဲ့ထက်မကလဲရှိရင်ရှိနိုင်တယ် Component တစ်ခုနဲ့တစ်ခု Date Share သုံးရတာတွေလဲရှိနိုင်တယ်။ အဲ့တော့ဘာဖစ်လာလဲဆိုရင် JSX Tree က အရမ်းကို ရှုပ်ထွေးလာတယ် State ကို  Management လုပ်ဖို့ခက်ခဲလာနိုင်တယ်။ နောက်ပိုင်း Maintain ဖို့မလွယ်ဘူး။ နောက်တစ်ချက်က အဓိကအချက် Performance ကိုထိခိုက်တယ် ဘာလို့လဲဆို Context Api က State changes အများဆုံးလုပ်ရမဲ့လုပ်ငန်းတာ၀န်အတွက် အဓိကလုပ်ထားတာမဟုတ်တဲ့အတွက်ဖစ်တယ်။

 Project တစ်ခုမှာ Context Api  ရော Redux ရောတွဲသုံးမယ်ဆိုတွဲသုံးလို့ရပါတယ် ။  တွဲသုံးမယ်ဆိုရင်လဲ ဥပမာ (locale,Theme) တို့လိုနေရာတွေမှာပဲသုံးသင့်တယ်။ Context ကိုဘယ်လိုအခြေအနေမှာပဲသုံးသင့်သလဲဆို Small or Medium လောက်ရှိတဲ့ Project လောက်ဆို Redux သုံးစရာမလိုပဲ Context နဲ့တင်အဆင်ပြေနိုင်တယ်။ အဲ့လိုမှမဟုတ်ဘူး ကိုယ့်ရဲ့ Project က Enterprise Level or ကြီးတယ်လို့ထင်ရင် Redux ကိုပဲသုံးဖို့အကြံပေးလိုပါတယ်ဗျာ။

