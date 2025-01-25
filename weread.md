---
isbn: { { metaData.isbn } }
category: { { metaData.category } }
---

# 元数据

> [!abstract]+ {{metaData.title}}
>
> -   ![ {{metaData.title}}|200]({{metaData.cover}})
> -   书名： {{metaData.title}}
> -   作者： {{metaData.author}}
> -   简介： {{metaData.intro}}
> -   出版时间： {{metaData.publishTime}}
> -   ISBN： {{metaData.isbn}}
> -   分类： {{metaData.category}}
> -   出版社： {{metaData.publisher}}

# 高亮划线

{% for chapter in chapterHighlights %}

## {{chapter.chapterTitle}}{% for highlight in chapter.highlights %}{% if highlight.reviewContent %}{% else %}

> [!tip] {{ highlight.markText |trim }}
>
> -   {{highlight.createTime}}{% endif %} > {% endfor %}{% endfor %}

# 读书笔记

{% for chapter in bookReview.chapterReviews %}{% if chapter.reviews or chapter.chapterReview %}

## {{chapter.chapterTitle}}

### 章节评论

{% if  chapter.chapterReviews %}{% for chapterReview in chapter.chapterReviews %}> [!note] {{chapterReview.createTime}}

> {{chapterReview.content}}

{% endfor%}{%endif %}

### 划线评论

{% if chapter.reviews %}{%for review in chapter.reviews %}> [!note] {{review.createTime}}

> -   **原文** > {{review.abstract |trim }}
> -   **评论** > {{review.content}}

{% endfor %}{%endif %}{% endif %}{% endfor %}

# 本书评论

{% if bookReview.bookReviews %}{% for bookReview in bookReview.bookReviews %}## 书评 No.{{loop.index}}
{{bookReview.mdContent}}
{{bookReview.createTime}}
{% endfor%}{% endif %}
