1.去[github](https://github.com)注册账号，进入[vercel](https://vercel.com)用github登录

2.直接访问
<a href="https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fwalinejs%2Fwaline%2Ftree%2Fmain%2Fexample](https://vercel.com/new/clone?s=https%3A%2F%2Fgithub.com%2Fning0818%2Ftypecho-vercel&showOptionalTeamCreation=false)" target="_blank" rel="noopener noreferrer"><img src="https://vercel.com/button" alt="Vercel" tabindex="0"><span><svg class="external-link-icon" xmlns="http://www.w3.org/2000/svg" aria-hidden="true" focusable="false" x="0px" y="0px" viewBox="0 0 100 100" width="15" height="15"><path fill="currentColor" d="M18.8,85.1h56l0,0c2.2,0,4-1.8,4-4v-32h-8v28h-48v-48h28v-8h-32l0,0c-2.2,0-4,1.8-4,4v56C14.8,83.3,16.6,85.1,18.8,85.1z"></path><polygon fill="currentColor" points="45.7,48.7 51.3,54.3 77.2,28.5 77.2,37.2 85.2,37.2 85.2,14.9 62.8,14.9 62.8,22.9 71.5,22.9"></polygon></svg><span class="external-link-icon-sr-only">open in new window</span></span></a>

3.进入github.com/你的用户名/typecho-vercel修改config.inc.php
```
  'host' => '{mysql地址}',
  'port' => 3306,
  'user' => '{mysql用户名}',
  'password' => '{mysql密码}',
  'charset' => 'utf8mb4',
  'database' => '{mysql面板名}',
```
