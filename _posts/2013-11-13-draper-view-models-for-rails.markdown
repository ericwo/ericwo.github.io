---
layout: post
title:  "Draper: Rails decorators"
date:   2013-11-13 18:05:10
categories: jekyll update
---

Draper adds an object-oriented layer of presentation logic to your Rails application.

Without Draper, this functionality might have been tangled up in procedural helpers or adding bulk to your models. With Draper decorators, you can wrap your models with presentation-related logic to organise - and test - this layer of your app much more effectively.

假设你的应用有一个Article对象，使用Draper你可以创建一个相应的ArticleDecorator。
{% highlight ruby %}
# app/controllers/articles_controller.rb
def show
  @article = Article.find(params[:id]).decorate
end
{% endhighlight %}

在view中，你就可以像使用model一样使用这个相应的decorator。当你需要一个在view中的逻辑或者开始想要有一个helper方法，你就可以在这个decorator实现。现在我们来看看怎么把存在的Rails helper放到decorator中去实现。假设你有这个存在的helper:
{% highlight ruby %}
# app/helpers/articles_helper.rb
def publication_status(article)
  if article.published?
    "Published at #{article.published_at.strftime('%A, %B %e')}"
  else
    "Unpublished"
  end
end
{% endhighlight %}

不使用decorator的话，你就必须要在Article中实现`publication_status`这个方法。但是这个方法的作用是描述一个物体的属性，不应该放在model中。

看看用decorator怎么实现：
{% highlight ruby %}
# app/decorators/article_decorator.rb
class ArticleDecorator < Draper::Decorator
  delegate_all

  def publication_status
    if published?
      "Published at #{published_at}"
    else
      "Unpublished"
    end
  end

  def published_at
    object.published_at.strftime(%A, %B %e)
  end
end
{% endhighlight %}

Decorators 是一个非常好的地方去实现下面这些需求的地方：

+  格式化复杂的日期显示
+  定义常用对象的表述，比如有一个`name`方法，使用`first_name`和`last_name`这两个属性。

当你发现自己的view中有太多逻辑你可以首先考虑使用Decorator这个gem来重构。
