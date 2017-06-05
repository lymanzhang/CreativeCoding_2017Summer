## conditions: Relational Operators

For a machine to make decisions about things it needs to be able to compare and test variables in order to decide which action to perform.

For example, even something as simple as a thermostat makes a decision about whether to turn a heater on or off based on the temperature in the room. We could write the method the thermostat uses using what’s called ‘pseudo code’:

```java
if (room temperature is less than the thermostat dial setting) then
    turn the heater on.
else
    turn the heater off.
```

This simple kind of testing is the basis of how computers make decisions. Being able to make decisions based on conditions in your environment is one of the first steps to autonomy. Autonomy means ‘self-determination’ and making machines and computer programs ‘autonomous’ is a big deal in artificial intelligence (AI) research. Of course there’s a substantial gap between the autonomy of a thermostat and a person, so we might infer that there are degrees of autonomy and autonomous behaviour.

Anyway, enough of the philosophy, back to making decisions.

The pseudo code for the thermostat outlines the basic idea of decision making in code. We can generalise this specific case to the more general form:

```java
if (condition is true) then
    do something
else
    do something else
end if
```

The condition part is evaluated as a boolean expression, which means it can only evaluate to be true or false (sorry, no half-truths or shades of grey). Sometimes the condition can be composed of several comparisons. If statements can also be ‘nested’:
```java
if (it's Friday night and money in my wallet is greater than £10) then
    if (there's a good movie on at the local Cinema) then
        Go see the movie.
    else
        Go dancing in a club.
    end if
else
    Stay at home.
end if.
```

This example is slightly more complex because it involves two levels of if...then testing and the condition for the first test requires two different things to be true. If it’s not Friday night or I don’t have more than £10 in my wallet, then I stay at home.

Here’s the thermostat example in Processing. In this example, we’re assuming the functions getTemperature() and getThermostatTempSetting() are able to access external information from the thermostat (there are no built-in functions to do this, but it would be possible via a library).

```java
float currentTemperature = getTemperature();
float thermostatSetting = getThermostatTempSetting();

if (currentTemperature < thermostatSetting) {
    turnHeaterOn();
} else {
    turnHeaterOff();
}
```

Notice that there’s no ‘then’ (it’s inferred) and that the curly brackets ({ and }) are used to mark the beginning and end of the code blocks for the if and else sections.

Here’s the second example in Processing form. I’ve taken a little license with the functions:

```java
if (day == FRIDAY && hour() >= 19 && availableCash > 10) {
    if (match(currentMovieList, movieIwantToSee) != null) {
        seeMovie(movieIwantToSee);
    } else {
        goClubbing();
    }
} else {
    stayAtHome();
}
```

This example seems more complicated, so let’s look at a few important aspects of the code. Firstly, the condition inside the first if statement is: day == FRIDAY && hour() >= 19 && availableCash > 10. The && characters are called a ‘logical and’, they’re another type of operator that looks at the boolean (true/false) value of the expression on either side and returns true if both are true, false otherwise. The other logical operator you’ll want to know is or: ||. It returns true if either expression is true, false if both are false.

The first part of the condition is day == FRIDAY. We assume day is a variable that contains the current day of the week. The == tests for equality (are the left and right side equal?). It uses two = characters to distinguish it from the assignment operator, =. Assigning a value to a variable (=) is different from testing if two things are equal (==).

match() is a built-in Processing function that tests for a matching string from a list. For now, the only important thing to know is that this function is testing if the name of the movie you want to see is contained within a list of movies currently showing. I’ve conveniently left out how you would actually get this information!

match() returns a list of matched strings, but if none match it returns a special value, null. For this to happen it means no movies currently showing matched the movie you wanted to see. So the condition uses the not equal operator, != to make sure there was a match before executing the movie-seeing function.

Here’s a summary of the relational operators.

|Operator|Meaning
|------|------|
|>|大于|
|>=|大于或等于|
|<|小于|
|<=|小于或等于|
|==|等于|
|!=|不等于|
