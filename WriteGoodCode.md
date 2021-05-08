# Write Good Code

- In faculty and at my first jobs I never knew about clean code or well-written code. I was just inspired by what the older and experienced programmers written and commented inside those enormous files. So here I'll add articles and lessons about what good code is and should be.
- Remember that: A code can ALWAYS be improved. Good practices will get better, apps will be updated, improved and you'll have to keep up with improving your code.

## [Naming](https://deviq.com/practices/naming-things)

 - The most important thing is to be consistent within the project.
 - Choose meaningful names and logical ones. If the names of variables/methods/classes make sense, you'll help other programmers to understand your code.
 - Pair with other developers from your team and find a common solution for better naming inside the app.
 - Names should describe why an element exists and what's its purpose. Don't name something short and comment near what it is or what it does, better think of a name that describes it.
 - EX:
 ```
 int d; // elapsed time in days
 ```
    VS
 ```
 int elapsedTimeInDays;
 ```
 - As you can see, if a good name is picked, you won't need the comment anymore.

### Good qualities to include in your naming

 - Pronounceable
 - Searchable
 - Name methods only for their scope, don't include side-effects
 - Use longer names if that's needed, don't be afraid
 - Don't use numbers in names
 - Be consistent (don't use begin/end in one place, start/finish in another, etc.)

### [Naming is everything](https://jasonroelofs.com/articles/2012/10/01/naming-is-everything/)
- Software development is split into two processes: Informing other programmers what the computer is doing and telling the computer what to do.
- It may be easy to tell a computer what to do with x.y = z but think about the future developer, or your colleagues.
- People will look a lot over code without modifying it. Keep that in your mind.
- Even simple methods are more understandable with good naming.

Example:
```
def copy(x, y)
  x.member1 = y.member1
  x.member2 = y.member2
end
```
After good naming:
```
def copy(from, to)
  to.member1 = from.member1
  to.member2 = from.member2
end
```

With good naming, the method looks a lot easier and understandable. Every variable is clear and the actions inside are descriptive

#### Parameters and Variables
- we don't want to use to general names and we want to be specific with what data we use around the functions.
- don't be afraid to be explicit with your names. They don't have to be small, they can be composed by 2-3-4 or how many words you need to make its scope clear.

#### Methods and functions
- methods names should show clearly what they do or return.

#### Constructors

- They help you and other developers to create code that will make its intentions and usability more visible and intuitive.

Example:
```
class ListMessages

  def self.received_by(user)
    new(:received, user)
  end

  def self.sent_to(user)
    new(:sent, user)
  end

  def initialize(sent_or_received, user)
    @messages = Message.send("#{sent_or_received}_by", user)
  end
end
````
Now look how messages are created:
```
messages = ListMessages.sent_to(user)
```
VS
```
messages = ListMessages.new(:sent, user)
```

#### Behavioral naming and consistency
- When adding new variables, make sure they do what they pretend to do.
- Make sure every time that your code is consistent and the naming pattern is respected.


## [Multiple returns statements are a bad ideea](https://www.yegor256.com/2015/08/18/multiple-return-statements-in-oop.html)

- a return method should only have a single return statement and nothing else.
- any other operators and statements are against object-oriented programming.
Below you'll observe 3 cases.

1 - a classic example of a return method.
```
public int max(int a, int b) {
  if (a > b) {
    return a;
  }
  return b;
}
```
2 - a more readable, easy-to-understand, and well-written code of the same function.
```
public int max(int a, int b) {
  int m;
  if (a > b) {
    m = a;
  } else {
    m = b;
  }
  return m;
}
```
3 - Even a better code with a single return statement.
```
public int max(int a, int b) {
  return new If(
    new GreaterThan(a, b),
    a, b
  );
}
```
- As a conclusion of all of the above, in the future, try to use only one return statement with no other complications and do it in one-line code if it's possible. It will be easy to read, easy to maintain, and easy to understand.

###### Here is a long and detailed lesson about [Bad and unmaintainable code](https://github.com/Droogans/unmaintainable-code)
