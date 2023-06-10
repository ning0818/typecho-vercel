1.去[github](https://github.com)注册账号，进入[vercel](https://vercel.com)用github登录

2.访问[Deply](https://vercel.com/new/clone?s=https%3A%2F%2Fgithub.com%2Fning0818%2Ftypecho-vercel&showOptionalTeamCreation=false)

3.进入github.com/你的用户名/typecho-vercel修改config.inc.php
```
  'host' => '{mysql地址}',
  'port' => 3306,
  'user' => '{mysql用户名}',
  'password' => '{mysql密码}',
  'charset' => 'utf8mb4',
  'database' => '{mysql面板名}',
```
