---
layout: post
title: Clean Code - Notes 01
category : notes
tagline: ""
tags : [coding, best practices, csharp]
---
{% include JB/setup %}

### Clean Code: Writing Code for Humans
#### Pluralsight Video Course Notes

##### Assign booleans implicitly.

bad:
{% highlight csharp %}
bool isGoingToLunch
if(cashInWallet > 6.00)
{
    isGoingToLunch = true;
} else {
    isGoingToLunch = false;
}
{% endhighlight %}
good:
{% highlight csharp %}
bool isGoingToLunch = cashInWallet > 6.00;
{% endhighlight %}

Always use positive bool statements (our brains have a harder time understanding double negatives) example of a bad bool:  !isNotLoggedIn


##### Ternary is elegant.

bad:
{% highlight csharp %}
int registrationFee;
if (isSpeaker) registrationFee = 0;
else registrationFee = 50;
good:
int registrationFee = isSpeaker ? 0 : 50;
{% endhighlight %}


##### DRY - DON’T REPEAT YOURSELF

##### YAGNI - YOU AIN’T GONNA NEED IT 
(don’t add unnecessary complexity you think you’ll need late)


##### Avoid being “Stringly” Typed.

bad:
{% highlight csharp %}
if (employeeType == “manager”)
good (enum):
if (employee.Type == EmployeeType.Manager)
{% endhighlight %}
Reasons: 1) Strongly typed => No typos  2) Intellisense support  3) Documents states 
4) Searchable

Complex Conditionals:
Bad:
{% highlight csharp %}
if (employe.Age > 55
    && employee.YearsEmployed > 10
    && employee.IsRetired == true)
{ logic }
{% endhighlight %}
What question is this trying to answer?
Good (Use Intermediate Variable):
{% highlight csharp %}
if (bool eligibleForPension = 
    employee.Age > MinRetirementAge
    && employee.YearsEmployed > 10
    && employee.IsRetired;)
{  logic   }
{% endhighlight %}
Much clearer intent



Complex Conditionals (again)        
Bad:
// check for valid file extensions. confirm admin or active
{% highlight csharp %}
if (fileExtension == “mp4” ||
    fileExtension == “mpg” ||
    fileExtension == “avi”)  
    && (isAdmin || isActiveFile);
{% endhighlight %}

Favor expressive code over comments
Good:
{% highlight csharp %}
if (ValidFileRequest(fileExtension, active))

private bool ValidFileRequest (string fileExtension, bool isActiveFile, bool isAdmin)
{
    var validFileExtensions = new List<string>() 
    { “mp4”, “mpg”, “avi” };
    bool validFileType =     validFileExtensions.Contains(fileExtension);
    bool userIsAllowedToViewFile 
= isActiveFile || isAdmin;

    return validFileType && userIsAllowedToViewFile;
}
{% endhighlight %}




Favor Polymorphism over Enums for Behavior
Dirty:
{% highlight csharp %}
private void LoginUser(User user)
{
    switch (user.Status)
           {
                 case Status.Active:
                        //logic for active users
                        break;
                 case Status.Inactive:
                        //logic for active users
                        break;
                  case Status.Locked:
                        //logic for active users
                        break;
          }
}
{% endhighlight %}

Clean:
{% highlight csharp %}
private void LoginUser(User user)
{
           user.Login();
}
private abstract class User
{
         public string FirstName;
         public string LastName;
         public Status Status;
         public int AccountBalance;
        
         public abstract void Login();
}
private class ActiveUser : User
{
        public void Login()
        {
                // Active user logic here
        }
}
private class InactiveUser : User
{
        public void Login()
        {
                // Inactive user logic here
        }
}
private class LockedUser : User
{
        public void Login()
        {
                // Locked user logic here
        }
}
{% endhighlight %}

Be Declarative if possible (Take advantage of LINQ in C# and other languages)
