---
layout: post
title: Markdown 연습하기
excerpt: "Markdown 연습장"
categories: [hello world]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---

## Markdown 연습하기

자주 쓸 것 같은 애들만 정리할거임.


# Heading 1
` # Heading 1`

## Heading 2
` ## Heading 2`

### Heading 3
` ### Heading 3`

#### Heading 4
` #### Heading 4`

##### Heading 5
` ##### Heading 5`

###### Heading 6
`###### Heading 6`


### 강조하기

Cause if you like the way you look that much
Oh baby you should go and **love yourself**

굵게 `Cause if you like the way you look that much
Oh baby you should go and **love yourself**`

Cause if you like the way you look that much
Oh baby you should go and ~~love yourself~~

선 긋기 `Cause if you like the way you look that much
Oh baby you should go and ~~love yourself~~`

Cause if you like the way you look that much
Oh baby you should go and *love yourself*

기울임 `Cause if you like the way you look that much
Oh baby you should go and *love yourself*`


### Blockquotes
> And if you think that I'm still holdin' on to somethin'
You should go and love yourself

`> And if you think that I'm still holdin' on to somethin'
You should go and love yourself`


### 숫자 목록

1. Item one
   1. sub item one
   2. sub item two
   3. sub item three
2. Item two

```
1. Item one
   1. sub item one
   2. sub item two
   3. sub item three
2. Item two
```


### 기호 목록

* Item one
  * Item two
    * Item three

+ Item one
  + Item two
    + Item three

- Item one
  - Item two
    - Item three

```
* Item one
  * Item two
    * Item three

+ Item one
  + Item two
    + Item three

- Item one
  - Item two
    - Item three
```


### 소스 Code 입력

{% highlight css %}
#container {
  float: left;
  margin: 0 -240px 0 0;
  width: 100%;
}
{% endhighlight %}

```
{% highlight css %}
#container {
  float: left;
  margin: 0 -240px 0 0;
  width: 100%;
}
{% endhighlight %}

```

### Image 삽입
![Smithsonian Image](https://images.unsplash.com/photo-1440635592348-167b1b30296f?crop=entropy&dpr=2&fit=crop&fm=jpg&h=475&ixjsv=2.1.0&ixlib=rb-0.3.5&q=50&w=1250)
{: .pull-right}

` ![Smithsonian Image](https://images.unsplash.com/photo-1440635592348-167b1b30296f?crop=entropy&dpr=2&fit=crop&fm=jpg&h=475&ixjsv=2.1.0&ixlib=rb-0.3.5&q=50&w=1250)
{: .pull-right} `
