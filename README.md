# TGIC API文档

本文档基于[docsify](https://docsify.js.org/)创建

## 本地预览
1、安装`docsify`

```bash
npm i docsify-cli -g
```

2、本地预览

```bash
docsify serve tgic-api-docs
```

3 、访问 http://localhsot:3000

## 生成PDF

1、安装`docsify-pdf-converter`插件

```bash
npm install --save-dev docsify-pdf-converter
```

2、创建配置文件`.docsifytopdfrc.js`

```js
module.exports = {
  contents: [ "docs/_sidebar.md" ], // array of "table of contents" files path
  pathToPublic: "pdf/tgic-api-docs.pdf", // path where pdf will stored
  pdfOptions: "<options for puppeteer.pdf()>", // reference: https://github.com/GoogleChrome/puppeteer/blob/master/docs/api.md#pagepdfoptions
  removeTemp: true, // remove generated .md and .html or not
  emulateMedia: "screen", // mediaType, emulating by puppeteer for rendering pdf, 'print' by default (reference: https://github.com/GoogleChrome/puppeteer/blob/master/docs/api.md#pageemulatemediamediatype)
}
```

3、添加脚本到`package.json`

```json
{
  "scripts": {
    "convert": "node_modules/.bin/docsify-pdf-converter"
  }
}
```
4、运行命令

```bash
npm run convert
```