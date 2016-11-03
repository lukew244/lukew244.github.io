---
layout: post
title:  "Private methods in Ruby really aren't that private"
date:   2016-09-10 13:12:38 +0100
categories: Ruby
---

Most beginner Ruby tutorials draw a simple distinction between public methods (accessible inside and outside the object) and private methods (accessible only inside the object). Consider the following example:

{% highlight ruby %}
class Employee
  attr_reader :full_name

  def initialize(full_name, salary)
    @full_name = full_name
    @salary = salary
  end

  private

  attr_reader :salary
end
{% endhighlight %}

As you would expect, in the terminal we can create a new instance of this class and access our employee's full name, but not their salary:

{% highlight ruby %}
2.3.0 :002 > Jim = Employee.new('Jim Smith', '£45,000')
 => #<Employee:0x007fa3fb0456e0 @full_name="Jim Smith", @salary="£45,000">
2.3.0 :003 > Jim.full_name
 => "Jim Smith"
2.3.0 :004 > Jim.salary
NoMethodError: private method `salary' called for #<Employee:0x007fa3fb0456e0>
{% endhighlight %}

Left at that, it would suggest that Ruby is similar to C or Java, where genuinely private methods exist. In reality, Ruby is more like Javascript: making a method private signals an intent about how your program should be used, but does not actually prohibit access. Notice what happens when we try a different approach to get our employee's salary:

{% highlight ruby %}
2.3.0 :005 > Jim.send :salary
 => "£45,000"
{% endhighlight %}

This works because Ruby only refuses private method calls when our object is the explicit receiver (i.e. we call `object.method`, like in the first example above). In the second example, we were able to get around this by calling the send method[^1] explicitly on our object, and passing in the salary method as an argument to send.

Of course, it goes without saying that truly sensitive information should be stored securely in a database or as an environment variable, not being passed around in private methods. But it's worth being aware that private isn't as private as you might have thought.  

[^1]: A good explanation of the send method can be found [here](http://stackoverflow.com/questions/3337285/what-does-send-do-in-ruby). It is a method belonging to the Object class, which is the default parent of all other classes in Ruby. Since objects inherit methods from their ancestors, it can be called on our Employee class without being defined within Employee itself.
