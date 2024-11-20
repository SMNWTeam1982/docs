For the 2023 & 2024 seasons we used command based, before that I dont know. The code for those seasons was spagetti, Initially we tried both of those years to write the code in a command based way but as the season progressed and our goal was to just get things working, the command based stuff just got in our way and we ended up just working around the command based stuff.

wpilib explenation of command-based programming: https://docs.wpilib.org/en/stable/docs/software/commandbased/what-is-command-based.html

# Pros and cons of NOT doing command-based
## Pros: 
1. writing code is fast, this is the biggest benefit of not doing command-based
2. the style of coding used when not doing command-based is the same style that many people are already familiar with
3. Can write code in this way without being experienced in the programming language
4. very easy to write TeleOp code
5. We can handle when things are run directly, instead of having to go through the command scheduler
6. Extra verbose

## Cons: 
1. Most teams use command-based
2. pathplanner expects you to use command-based, using pathplanner requires extra effort
3. A little difficult to write Auto code
4. can accidentally create a conflict where 2 pieces of code tell 1 piece of hardware to do something



# Pros and cons of doing command based

## Pros:
1. plenty of examples because most teams use command-based
2. Very easy to write Auto code / sequential code
3. Can avoid conflicts via the command requirments
4. Well written command-based code looks really nice
5. Uses factory functions and lambdas to run code (makes for concise code, concise code can be easier to follow)

## Cons: 
1. Hard to work with when crunched for time
2. Command scheduler is confusing
3. TeleOp code can be convoluted
4. hard to write code that uses multiple subsystems at the same time
5. Uses factory functions and lambdas to run code (these are very confusing, even more for new programmers)
