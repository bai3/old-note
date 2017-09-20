## jquery中attr设置checkbox的checked属性解决方法

## 问题分析:

当使用jquery中的attr方法改变checkbox的checked属性时，即使设checked为true，也会直接将checked更改为checked，导致后面取消点击时，在想通过attr更改时吗，就会变得没有效果。

## 解决方案:

使用jquery中的prop方法就可以完美解决，当使用prop时，会将checked设为true和false，而不是checked。

轻松解决。。