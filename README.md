# Termius-cracked

## 破解方法

安装npm 安装asar
```shell
npm install -g asar
```
### for Windows

大同小异，看下面Mac的破解方法


### for MAC

1. 解包app.asar
```shell
cd /Applications/Termius.app/Contents/Resources/
asar extract app.asar ./app  # 修改完不需要重新打包
mv app.asar app.asar.bak  # 留个备份，或者直接rm
rm app-update.yml  # 防止自动更新

```
2. 修改app/js/background-process.js

搜索`await this.api.bulkAccount`

`const e=await this.api.bulkAccount();` -> `var e=await this.api.bulkAccount();`

```js
var e=await this.api.bulkAccount();
e.account.pro_mode=true;
e.account.current_period={
    "from": "2022-01-01T00:00:00",
    "until": "2099-01-01T00:00:00"
};
e.account.plan_type="Premium";
e.account.user_type="Premium";
e.account.expired_screen_type=null;

e.account.authorized_features.show_create_team_promotions=false;
e.account.authorized_features.show_trial_section=false;
e.account.authorized_features.show_subscription_section=true;
e.account.authorized_features.show_github_account_section=false;
e.account.authorized_features.show_team_member_activation_into_identities_tour=false;
e.trial=null;
e.team=null;
e.student=null;
e.personal_subscription={
    "now": new Date().toISOString().slice(0, -5),
    "status": "SUCCESS",
    "platform": "stripe",
    "current_period": {
        "from": "2022-01-01T00:00:00",
        "until": "2099-01-01T00:00:00"
    },
    "revokable": true,
    "refunded": false,
    "cancelable": true,
    "reactivatable": false,
    "currency": "usd",
    "created_at": "2022-01-01T00:00:00",
    "updated_at": new Date().toISOString().slice(0, -5),
    "valid_until": "2099-01-01T00:00:00",
    "auto_renew": true,
    "price": 12.0,
    "verbose_plan_name": "Termius Pro Monthly",
    "plan_type": "SINGLE",
    "is_expired": false
};
return .......
```

搜索await this.api.login

`const s=await this.api.login` -> `var s=await this.api.login`
```js
var s=await this.api.login({email:a,firebase_token:n,authy_token:r,password:$I.generateHash(t),device:HA.toJSON()});
s.bulk_account.account.pro_mode=true;
s.bulk_account.account.current_period={
    "from": "2022-01-01T00:00:00",
    "until": "2099-01-01T00:00:00"
};
s.bulk_account.account.plan_type="Premium";
s.bulk_account.account.user_type="Premium";
s.bulk_account.account.expired_screen_type=null;

s.bulk_account.account.authorized_features.show_create_team_promotions=false;
s.bulk_account.account.authorized_features.show_trial_section=false;
s.bulk_account.account.authorized_features.show_subscription_section=true;
s.bulk_account.account.authorized_features.show_github_account_section=false;
s.bulk_account.account.authorized_features.show_team_member_activation_into_identities_tour=false;
s.bulk_account.trial=null;
s.bulk_account.team=null;
s.bulk_account.student=null;
s.bulk_account.personal_subscription={
    "now": new Date().toISOString().slice(0, -5),
    "status": "SUCCESS",
    "platform": "stripe",
    "current_period": {
        "from": "2022-01-01T00:00:00",
        "until": "2099-01-01T00:00:00"
    },
    "revokable": true,
    "refunded": false,
    "cancelable": true,
    "reactivatable": false,
    "currency": "usd",
    "created_at": "2022-01-01T00:00:00",
    "updated_at": new Date().toISOString().slice(0, -5),
    "valid_until": "2099-01-01T00:00:00",
    "auto_renew": true,
    "price": 12.0,
    "verbose_plan_name": "Termius Pro Monthly",
    "plan_type": "SINGLE",
    "is_expired": false
};
return .......
```
