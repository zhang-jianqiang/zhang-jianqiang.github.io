---
title: MySQL保存表情符号
date: 2023-11-08 00:04:19
tags:
---

# MySQL保存表情符号

# 一、什么utf8mb4

utf8mb4 是 MySQL 中的字符集，用于编码宽字符集（如表情符号）。utf8mb4 的编码方式，允许编码 Unicode 中的所有字符，因此是处理国际化、多语言数据的首选编码。通常，新版的 MySQL 数据库已经使用了utf8mb4。

# 二、保存表情报错
## 1、错误1： 表情符号变成了问号
如果不使用utf8mb4作为字符集，保存表情符号时，表情符号会被MySQL解释成无法识别的字符，变成问号（ “？”）。这是因为 MySQL 的默认字符集是 utf8 ，该字符集最多只能表示三个字节，保存表情符号时会产生截断。如果出现这种情况，解决方法是把字符集改为utf8mb4。

## 2、错误2：utf8mb4保存表情符号提示：`Incorrect string value`
当使用utf8mb4保存表情符号时，MySQL会默认使用 utf8mb4\_general\_ci 排序规则，其只支持常见的字符范围。但是，在某些情况下，表情符号可能无法在该排序规则下存储或查找，这就会出现“Incorrect string value”错误。为解决这种错误，需要更改字符集排序规则。通常，utf8mb4\_unicode\_ci用于保存表情符号，因为它允许把更把多个语言支持保存到数据中。

## 3、字符集设置正确，仍然提示 ：`Incorrect string value`

如果我们使用程序连接数据库的`dsn`配置中的`charset`设置为`utf8`时，即使我们数据表及字段字符集设置为`utf8mb4`，在插入表情符号时依然会提示：`Incorrect string value`，因此需要将`dsn`中的数据库连接配置中的字符集设置为`utf8mb4`

# 三、结论

字符集：utf8mb4 

排序规则： utf8mb4_unicode_ci

dsn中的charset：utf8mb4
