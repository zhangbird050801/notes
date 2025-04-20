---
status: todo
weight: 1
field: 
date: {% if date %} {{date | format("YYYY-MM")}} {% endif %}
DOI: {% if DOI %} {{DOI}} {% endif %}
tags: 
- {{allTags}}
- 文献笔记
authors: {% for t in creators %} {{t.firstName}} {{t.lastName}} {{t.name}} {% if not loop. last %}, {% endif %}{% endfor %}
期刊: {% if journalAbbreviation %} {{journalAbbreviation}} {% endif %}
languages: {{language}}
类别: {{itemType}} {{thesisType}}
期刊: {{publicationTitle}} {{university}}
---

# 论文信息
**title:** {{title}}
**DOI:** {{DOI}}
**tags:** {{allTags}}
**level:** {% if archive %} {{archive}} {% endif %} {% if archiveLocation%} {{archiveLocation}} {% endif %}
**IF:** {% if callNuimber %} {{callNuimber}} {% endif %}
**期刊:** {{publicationTitle}} {{university}}
**类别:** {{itemType}} {{thesisType}}

## abstract: 
{{abstractNote}}

## Files and Links
- **Url**: [Open online]({{url}})
- **zotero entry**: {{pdfZoteroLink}}
- **open pdf**: [zotero]({{select}})

# 概要

# 研究对象

# 背景

# 方法

# 结论

# 标注
## 黄色
{% set i=1%}{% for annotation in annotations %}{% if annotation. color == ' #ffd400 ' %}
### 第 {{i}} 个注释{% set i=i+1 %}
#### 文本:
{{annotation.annotatedText}}
#### 评论:
{{annotation.comment}} {% if annotation. imageBaseName %}
![[{{annotation.imageBaseName}}]]{% endif %}

#### zotero 位置:
{{pdfZoteroLink|replace("//select/", "//open-pdf/")|replace(")", "")}} ? page= {{annotation.page}} &annotation= {{annotation.id}} )
{% endif %}

{% endfor %}

## 红色

{% set i=1%}{% for annotation in annotations %}{% if annotation. color == ' #ff6666 ' %}
### 第 {{i}} 个注释{% set i=i+1 %}
#### 文本:
{{annotation.annotatedText}}
#### 评论: 
{{annotation.comment}} {% if annotation. imageBaseName %}
![[{{annotation.imageBaseName}}]]{% endif %}
#### zotero 位置:
{{pdfZoteroLink|replace("//select/", "//open-pdf/")|replace(")", "")}} ? page= {{annotation.page}} &annotation= {{annotation.id}} )
{% endif %}

{% endfor %}

## 绿色

{% set i=1%}{% for annotation in annotations %}{% if annotation. color == ' #5fb236 ' %}
### 第 {{i}} 个注释{% set i=i+1 %}
#### 文本:
{{annotation.annotatedText}}
#### 评论: 
{{annotation.comment}} {% if annotation. imageBaseName %}
![[{{annotation.imageBaseName}}]]{% endif %}
#### zotero 位置:
{{pdfZoteroLink|replace("//select/", "//open-pdf/")|replace(")", "")}} ? page= {{annotation.page}} &annotation= {{annotation.id}} )
{% endif %}

{% endfor %}

## 蓝色

{% set i=1%}{% for annotation in annotations %}{% if annotation. color == ' #2ea8e5 ' %}
### 第 {{i}} 个注释{% set i=i+1 %}
#### 文本:
{{annotation.annotatedText}}
#### 评论: 
{{annotation.comment}} {% if annotation. imageBaseName %}
![[{{annotation.imageBaseName}}]]{% endif %}
#### zotero 位置:
{{pdfZoteroLink|replace("//select/", "//open-pdf/")|replace(")", "")}} ? page= {{annotation.page}} &annotation= {{annotation.id}} )
{% endif %}

{% endfor %}

## 紫色

{% set i=1%}{% for annotation in annotations %}{% if annotation. color == ' #a28ae5 ' %}
### 第 {{i}} 个注释{% set i=i+1 %}
#### 文本:
{{annotation.annotatedText}}
#### 评论: 
{{annotation.comment}} {% if annotation. imageBaseName %}
![[{{annotation.imageBaseName}}]]{% endif %}
#### zotero 位置:
{{pdfZoteroLink|replace("//select/", "//open-pdf/")|replace(")", "")}} ? page= {{annotation.page}} &annotation= {{annotation.id}} )
{% endif %}

{% endfor %}

## 洋红色

{% set i=1%}{% for annotation in annotations %}{% if annotation. color == ' #e56eee ' %}
### 第 {{i}} 个注释{% set i=i+1 %}
#### 文本:
{{annotation.annotatedText}}
#### 评论: 
{{annotation.comment}} {% if annotation. imageBaseName %}
![[{{annotation.imageBaseName}}]]{% endif %}
#### zotero 位置:
{{pdfZoteroLink|replace("//select/", "//open-pdf/")|replace(")", "")}} ? page= {{annotation.page}} &annotation= {{annotation.id}} )
{% endif %}

{% endfor %}

## 橘色

{% set i=1%}{% for annotation in annotations %}{% if annotation. color == ' #f19837 ' %}
### 第 {{i}} 个注释{% set i=i+1 %}
#### 文本:
{{annotation.annotatedText}}
#### 评论: 
{{annotation.comment}} {% if annotation. imageBaseName %}
![[{{annotation.imageBaseName}}]]{% endif %}
#### zotero 位置:
{{pdfZoteroLink|replace("//select/", "//open-pdf/")|replace(")", "")}} ? page= {{annotation.page}} &annotation= {{annotation.id}} )
{% endif %}

{% endfor %}

## 灰色

{% set i=1%}{% for annotation in annotations %}{% if annotation. color == ' #aaaaaa ' %}
### 第 {{i}} 个注释{% set i=i+1 %}
#### 文本:
{{annotation.annotatedText}}
#### 评论: 
{{annotation.comment}} {% if annotation. imageBaseName %}
![[{{annotation.imageBaseName}}]]{% endif %}
#### zotero 位置:
{{pdfZoteroLink|replace("//select/", "//open-pdf/")|replace(")", "")}} ? page= {{annotation.page}} &annotation= {{annotation.id}} )
{% endif %}

{% endfor %}

# 导入记录
{% persist "annotations" %}
{% set newAnnotations = annotations | filterby ("date", "dateafter", lastImportDate) %}
{% if newAnnotations. length > 0 %}

## Imported: {{importDate | format("YYYY-MM-DD h:mm a")}}

{% for a in newAnnotations %}
> {{a.annotatedText}}
{% endfor %}

{% endif %}
{% endpersist %}
