---
title: change tomcat output language
---

## press F9 on intellij 
> then intellij show us the popup  
> so we click "Edit Configurations..."

##  add Tomcat server on list ("Alt + Insert")

## fill option into "VM options : "
> when tomcat prints into log  
> they use language of OS  
> so we have to fill into "VM options:" as follow  
> (this is to change the language to English)

```
-Duser.language=en -Duser.region=us
```




![](http://)
