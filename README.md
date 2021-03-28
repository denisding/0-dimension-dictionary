# 零度字典

## 一、介绍

零度字典是一款便于背诵英语单词的工具，他采用英语自释义（朗文词典第六版）的方式构建单词树，构建方式为：每个单词都有相应的英文释义，每个释义语句都由多个英文单词构成。从而，如果把释义理解为一种关联关系，那么每个单词就会和其他若干单词形成一个一对多的一层结构树，因而，对多个单词进行释义就会构建成一个结构图，每个单词的释义关系都会形成唯一的一个结构树，我们设定释义单词（朗文词典第六版）为树的叶子节点，当系统中具有的单词数量一定时，具有一个固定的释义结构维度，我们称释义维度。

当用户使用系统时，我们在释义结构树的基础上修订叶子节点为用户是否认识单词（无需再释义），即当用户认识某个单词的情况下，该单词为结构树的叶子节点。此时用户使用情况下的释义结构树的维度，我们称用户维度。

随着一个用户使用本系统辅助记忆单词的进程，结构树也会发生相应的变化，通常情况下用户维度随着使用逐渐降低，每个单词最大可能性会成为无需释义。

在释义结构树中，我们把释义单词的维度定义为 0，即释义单词的释义维度为 0。在用户结构树中，我们把用户认识的单词的维度定义为 0，即该单词的用户维度为 0。由于释义单词用户并不一定认识，所以释义维度为 0 的单词用户维度不一定为 0。

## 二、系统设计

系统在有用户使用的前提下才有意义，于是需要把系统中的单词信息、单词释义均存储在公用存储区供多用户使用。系统公用存储区中默认不包含任何单词，可以通过管理员添加、管理员采用用户数据的方式补充公用存储区数据。用户可以新建单词、单词释义，当公用存储区不存在该单词时，用户可以选择推荐给公用存储区。

用户系统默认按照释义维度进行数据展示，当用户标记 `认识` 某个单词，该单词的用户维度标记将被标记为 0，且默认隐藏该释义。用户可以通过 `忘记` 操作来重新恢复该单词的维度。

## Project setup

```base
npm install
```

### Compiles and hot-reloads for development

```base
npm run serve
```

### Compiles and minifies for production

```base
npm run build
```

### Lints and fixes files

```base
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).
