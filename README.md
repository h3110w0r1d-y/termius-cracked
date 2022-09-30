# Termius-cracked

## 破解方法

安装npm 安装asar
```shell
npm install -g asar
```
### for Windows

...


### for MAC

1. 解包app.asar
```shell
cd /Applications/Termius.app/Contents/Resources/
asar extract app.asar ./app
mv app.asar app.asar.bak
```
2. 修改app/js/background-process.js

搜索await this.api.bulkAccount

`const x=e=await this.api.bulkAccount();` -> `var x=e=await this.api.bulkAccount();`

```js
var e=await this.api.bulkAccount();
e.account.pro_mode=true;
e.account.current_period={
    "from": "2022-01-01T00:00:00",
    "until": "2099-01-01T00:00:00"
};
e.account.plan_type="Premium";
e.account.user_type="Premium";
e.account.authorized_features.show_trial_section=false;
e.account.authorized_features.show_subscription_section=true;
delete e.trial;
delete e.team;
delete e.student;
return .......
```

搜索await this.api.login

`const o=await this.api.login` -> `var o=await this.api.login
![image](https://user-images.githubusercontent.com/52311174/192995873-3b40a579-70dc-41b5-b4eb-25f993fc48f7.png)
