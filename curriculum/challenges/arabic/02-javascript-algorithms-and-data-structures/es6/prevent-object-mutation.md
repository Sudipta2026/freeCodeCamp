---
id: 598f48a36c8c40764b4e52b3
title: منع تغيير الكائن (Prevent Object Mutation)
challengeType: 1
forumTopicId: 301207
dashedName: prevent-object-mutation
---

# --description--

كما رأينا في التحدي السابق، استخدام `const` وحده لا يحمي بياناتك من امكانية تغييرها. لضمان عدم تغيير بياناتك، توفر جافا سكريبت دالة `Object.freeze` لمنع تغيير البيانات.

سيتم رفض أي محاولة لتغيير الـ object، مع اظهار خطأ إذا كان السكريبت يعمل في strict mode.

```js
let obj = {
  name:"FreeCodeCamp",
  review:"Awesome"
};
Object.freeze(obj);
obj.review = "bad";
obj.newProp = "Test";
console.log(obj); 
```

الكود `obj.review` و `obj.newProp` سيسفر عن أخطاء، لأن محررنا يعمل في وضع الـ strict mode افتراضيا، وسوف تعرض وحدة التحكم القيمة `{ name: "FreeCodeCamp", review: "Awesome" }`.

# --instructions--

في هذا التحدي سوف تستخدم `Object.freeze` لمنع تغيير الثوابت الرياضية. تحتاج إلى تجميد الـ object الآتي `MATH_CONSTANTS` بحيث لا يستطيع أحد تغيير قيمة `PI`،او إضافة أو حذف properties (خصائص).

# --hints--

لا ينبغي أن تستبدل كلمة `const`.

```js
(getUserInput) => assert(getUserInput('index').match(/const/g));
```

`MATH_CONSTANTS` يجب أن يكون متغير ثابت (باستخدام `const`).

```js
(getUserInput) =>
  assert(getUserInput('index').match(/const\s+MATH_CONSTANTS/g));
```

لا يجب عليك تغيير التعريف الأصلي لـ `MATH_CONSTANTS`.

```js
(getUserInput) =>
  assert(
    getUserInput('index').match(
      /const\s+MATH_CONSTANTS\s+=\s+{\s+PI:\s+3.14\s+};/g
    )
  );
```

`PI` يجب أن يساوي `3.14`.

```js
assert(PI === 3.14);
```

# --seed--

## --seed-contents--

```js
function freezeObj() {
  const MATH_CONSTANTS = {
    PI: 3.14
  };
  // Only change code below this line


  // Only change code above this line
  try {
    MATH_CONSTANTS.PI = 99;
  } catch(ex) {
    console.log(ex);
  }
  return MATH_CONSTANTS.PI;
}
const PI = freezeObj();
```

# --solutions--

```js
function freezeObj() {
  const MATH_CONSTANTS = {
    PI: 3.14
  };
  Object.freeze(MATH_CONSTANTS);

  try {
    MATH_CONSTANTS.PI = 99;
  } catch(ex) {
    console.log(ex);
  }
  return MATH_CONSTANTS.PI;
}
const PI = freezeObj();
```
