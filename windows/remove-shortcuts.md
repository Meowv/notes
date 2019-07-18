# 移除Windows图标快捷方式小箭头

以管理员身份运行 cmd，键入以下代码即可。

```scheme
reg delete "HKEY_CLASSES_ROOT\lnkfile" /v IsShortcut /f & taskkill /f /im explorer.exe & start explorer.exe 
```



