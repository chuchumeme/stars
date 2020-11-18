# Vue强制绑定class和style :lion:

#### class :lion:

- 正常赋值字符串
- 赋值数组 `['xxx','aaa']`
- 赋值对象 `{aClass: true, bClass: true}`
- 使用数组或对象时要在前面加上v-bind或使用语法糖 `:`

#### style :lion:

- 使用对象 `“{color：activeColor，fontSize：fontSize+‘px’}”`activeColor和fontSize为data中的属性