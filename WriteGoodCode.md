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

### [Bad and unmaintainable code](https://github.com/Droogans/unmaintainable-code)
