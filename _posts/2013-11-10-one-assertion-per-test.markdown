---
layout: post
title:  "One assertion per test"
date:   2013-11-10 11:02:29
categories: jekyll update
---
One assertion per test 的意思是：一个 test case 只测试一件事情。

下面有个方法的作用注册用户。

{% highlight ruby %}
def create
  user = User.new(params[:user])
  if user.save
    flash[:success] = "Thanks for registering Myblog, please sign in."
    redirect_to sign_in_path
  else
    flash[:error] = "Please check your input."
    render :new
  end
end
{% endhighlight %}

对于上面这个方法，使用 one assertion per test 的原则你就必须写如下这些测试，下面在两种情况下进行了测试:

{% highlight ruby %}
describe "POST create" do
  context "with valid input" do
    before do
      post :create, user: { email: "eric@gmail.com", password: "123", name: "Eric Wu" }
    end

    it "creates a user" do
      expect(User.count).to eq(1)
    end

    it "redirects to the sign in page" do
      expect(response).to redirect_to sign_in_path
    end

    it "show the sucess message" do
      expect(flash[:success]).to eq("Thanks for registering Myblog, please sign in.")
    end
  end

  context "with invalid input" do
    before do
      post :create, user: { email: "eric@example.com" }
    end

    it "does not create a user" do
      expect(User.count).to eq(0)
    end

    it "redirects to the :new template" do
      expect(response).to render :new
    end

    it "show the error message" do
      expect(flash[:error]).to eq("Please check your input.")
    end
  end
end
{% endhighlight %}

遵循 one assertion per test 的原则能让你更清楚的写出unit test， 如果一个method你做了太多的事情，那么你就知道自己的设计是有问题的，就需要重构代码了。
