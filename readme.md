## 1.去[github](https://github.com)注册账号，进入[vercel](https://vercel.com)用github登录

## 2.直接访问<a href="https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fwalinejs%2Fwaline%2Ftree%2Fmain%2Fexample](https://vercel.com/new/clone?s=https%3A%2F%2Fgithub.com%2Fning0818%2Ftypecho-vercel&showOptionalTeamCreation=false)" target="_blank" rel="noopener noreferrer"><img src="https://vercel.com/button" alt="Vercel" tabindex="0"><span><svg class="external-link-icon" xmlns="http://www.w3.org/2000/svg" aria-hidden="true" focusable="false" x="0px" y="0px" viewBox="0 0 100 100" width="15" height="15"><path fill="currentColor" d="M18.8,85.1h56l0,0c2.2,0,4-1.8,4-4v-32h-8v28h-48v-48h28v-8h-32l0,0c-2.2,0-4,1.8-4,4v56C14.8,83.3,16.6,85.1,18.8,85.1z"></path><polygon fill="currentColor" points="45.7,48.7 51.3,54.3 77.2,28.5 77.2,37.2 85.2,37.2 85.2,14.9 62.8,14.9 62.8,22.9 71.5,22.9"></polygon></svg><span class="external-link-icon-sr-only"></span></span></a>

![image](https://github.com/ning0818/typecho-vercel/assets/117955401/622002f2-c9aa-4494-ad1a-ee051a37ceb3)


## 3.进入github.com/你的用户名/typecho-vercel    ,修改config.inc.php
```
  'host' => '{mysql地址}',
  'port' => 3306,
  'user' => '{mysql用户名}',
  'password' => '{mysql密码}',
  'charset' => 'utf8mb4',
  'database' => '{mysql面板名}',
```
### 备注：免费mysql数据库申请请参考https://dusays.com/590/
## 4.去vercel项目中的settings/domains绑定域名，然后去https://your_domain.com/install.php 根据提示安装typecho

## Typecho源码更改：
1.添加config.inc.php
```
<?php
define('__TYPECHO_SECURE__',true);
define('__TYPECHO_ROOT_DIR__', dirname(__FILE__));
define('__TYPECHO_PLUGIN_DIR__', '/usr/plugins');
define('__TYPECHO_THEME_DIR__', '/usr/themes');
define('__TYPECHO_ADMIN_DIR__', '/admin/');
@set_include_path(get_include_path() . PATH_SEPARATOR .
__TYPECHO_ROOT_DIR__ . '/var' . PATH_SEPARATOR .
__TYPECHO_ROOT_DIR__ . __TYPECHO_PLUGIN_DIR__);
require_once 'Typecho/Common.php';
Typecho_Common::init();
$db = new Typecho_Db('Pdo_Mysql', 'typecho_');
$db->addServer(array (
  'host' => '{mysql地址}',
  'port' => 3306,
  'user' => '{mysql用户名}',
  'password' => '{mysql密码}',
  'charset' => 'utf8mb4',
  'database' => '{mysql面板名}',
  'engine' => 'MyISAM',
), Typecho_Db::READ | Typecho_Db::WRITE);
Typecho_Db::set($db);
```
2.添加vercel.json
```
{
  "functions": {
    "api/index.php": {
      "runtime": "vercel-php@0.6.0"
    }
  },
  "routes": [{ "src": "/(.*)", "dest": "/api/index.php" }]
}
```
3.添加api/index.php
```
<?php
$file= __DIR__ . '/..'.$_SERVER["PHP_SELF"];
if(file_exists($file))
{
  return false;
}
else
{
  require_once __DIR__ . '/../index.php';
}
```
4.更新install.php
Delete:
```
    if (!$writeable) {
        $errors[] = _t('上传目录无法写入, 请手动将安装目录下的 %s 目录的权限设置为可写然后继续升级', $uploadDir);
    }

```
Add:
```
#    if (!$writeable) {
#        $errors[] = _t('上传目录无法写入, 请手动将安装目录下的 %s 目录的权限设置为可写然后继续升级', $uploadDir);
#    }
```



