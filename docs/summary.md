# Project Files & Directories

Assets

|Name|Type|Path|Remark|
|---|---|---|---|
|assets_js|Dir|assets/js|存放额外JS的文件夹|
|assets_media|Dir|assets/media|CMS默认存放媒体文件的文件夹|
|assets_post|Dir|assets/media/post|CMS存放文章图片的文件夹|
|assets_icon|File|assets/media/icon.png|网站的favicon|
|assets_logo|File|assets/media/logo.png|菜单栏的Logo图片|

Configs

|Name|Type|Path|Remark|
|---|---|---|---|
|config|File|config/_default/config.yaml|
|languages|File|config/_default/languages.yaml|
|menus|File|config/_default/menus.yaml|
|params|File|config/_default/params.yaml|参数文件|
|params.xx|File|config/_default/params.xx.yaml|xx取值`en`,`zh`,`zh-Hant`; 覆盖`params`参数文件，用于为特定语言适配合适的参数|

Others

|Name|Type|Path|Remark|
|---|---|---|---|
|theme|Dir|data/themes|存放主题配置文件的文件夹|
|i18n|Dir|i18n|存放国际化文件(`en.yaml`,`zh.yaml`,`zh-Hant.yaml`)的文件夹|
|uploads|Dir|static/uploads|
|cms_tpl|File|data/wowchemy_cms_tpl.yaml|CMS模板文件|

Content

|Name|Type|Path|Remark|
|---|---|---|---|
|content_dir|Dir|content/xx|xx取值`en`,`zh-hans`,`zh-hant`; 存放页面内容的文件夹|
|home|Dir|content/xx/home|网站主页页面|
|admin|File|content/`en`/`admin`.md|CMS后台页面；只能放在默认语言(`en`)的文件夹中，文件名(`admin`)为链接路径|
|terms|File|content/terms.md|服务条款页面|

---

## 1. config.yaml

```yaml
baseurl: 'https://bp.net/' # Website URL

defaultContentLanguage: en

permalinks:
  post: '/blog/:slug'
  authors: '/author/:slug/'
  tags: '/tag/:slug/'
  categories: '/category/:slug/'

module:
  imports:
    - path: github.com/zeeis/hugo-enterprise
```

## 2. languages.yaml

```yaml
en:
  title: BP.NET Website
  contentDir: content/en

zh:
  title: BP.NET 中文官网
  contentDir: content/zh-hans

zh-Hant:
  title: BP.NET 中文官網
  contentDir: content/zh-hant
```

## 3. menus.yaml

```yaml
main:
  - name: menu_item_home
    url: /
    weight: 10

  - name: menu_item_about
    url: about/
    weight: 100
```

## 4. params.yaml

Localization

```yaml
locale:
  date_format: 'Jan 2, 2006'
```

Theme & FontSize
```yaml
appearance:
  theme_day: bp_net
  theme_night: bp_net
font_size: L
```

Website Header

```yaml
header:
  navbar:
    enable: true
    align: r
    highlight_active_link: true
    show_language: true
    show_translations: true
    show_day_night: true
    show_search: true
    show_logo: true
```

Website Footer

```yaml
footer:
  copyright:
    notice: 'Copyright ©{year} BP.NET. All Rights Reserved.'
```

Inject external js

```yaml
plugins_js:
  [myExternalJS1, myExternalJS2]
```

## 5. params.xx.yaml

> eg: params.zh.yaml

```yaml
locale:
  date_format: '2006年1月2日'
footer:
  copyright:
    notice: '版权所有 ©{year} BP.NET.'
```

## 6. theme/`custom-name`.yaml

> eg: theme/bp_net.yaml

```yaml
name: bp_net

font: minimal

light:
  primary: "#3d72b8"
  background: "#efefef"

#  home_section_odd: "transparent"
#  home_section_even: "transparent"

  menu_primary: "#f9f9f9"
  menu_text_active: "#3d72b8"
  menu_text: "#242424"
  menu_title: "#242424"

dark:
  primary: "#2e88ff"
  background: "#141414"

#  home_section_odd: "transparent"
#  home_section_even: "transparent"

  menu_primary: "#242424"
  menu_text_active: "#2e88ff"
  menu_text: "#efefef"
  menu_title: "#efefef"


menu_hover: true
menu_border: true
menu_shadow: false
menu_blur: false
```

## 7. i18n/`xx`.yaml

> eg: i18n/zh.yaml

```yaml
- id: menu_item_home
  translation: 主页
- id: menu_item_about
  translation: 关于
```

## 8. wowchemy_cms_tpl.yaml

```yaml
locale: 'zh_Hans'

backend:
  name: git-gateway
  branch: main
  squash_merges: true
media_folder: '/assets/media'
public_folder: '/media'

i18n:
  structure: multiple_folders
  locales: [en, zh-hans, zh-hant]
  default_locale: en

collections:
  # your collection configuration...
```

## 9. content/`xx`/home/index.md

use "widget_page" then we can add some widget section into home page.

```markdown
---
type: widget_page
headless: true
---
```

## 10. content/`en`/`admin`.md

```markdown
---
# Generate Wowchemy CMS
type: wowchemycms
private: true
outputs:
- wowchemycms_config
- HTML
---

```

## 11. content/`xx`/terms.md

```markdown
---
title: Terms of Use
date: 2018-02-22T06:32:10.708Z
---

some content

```