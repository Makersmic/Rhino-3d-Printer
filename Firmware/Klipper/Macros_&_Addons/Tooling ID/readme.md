### Tooling ID Build Log 
# Day2
To be honest this probably day 7 on this idea.  I have begun having another talk with chatgpt about the project, the difference though with this conversation is that i started out basic.
What i mean by that is that i tried to build up to the project letting the ai know aspects of my 3d printer build.  Trying to keep sentences very pointed this technique seems to have opened up a new door of knowledge.  I told the ai some basics about the printer, that i was the designer of a lot of the components, and then focused a few phrases that went into depth about the umbilical.  Whats interesting is that the ai came to the same conclusion as a member of the klipper discord.  The resistor method.  And after talking with another more knowledgable person about the idea, of which to be honest a lot of what he said was over my head at the time but it adds up over time.  At the time of conversation he had mentioned using a voltage divider type circuit for klipper to use to calculate the resistor or rather  ID of the tool.  The ai mentioned this and the way it explained is starting to make sense.  Another great thing is that i am learning the gtr board is proving to be more than capable of keeping up with these 'ideas' i have.
At first it suggested that i use the max318655 amplifier to 'read' the resistors.  Thats when i instantly asked if it was ok to use the built in amplifier of the gtr, yes.  It is.
A good resistor package from amazon that would suit this project and all of the tools that have been referenced:


# Day5
After a long session with chatgpt i have some initial working code.  Chatgpt seems to get some things wrong in the coding process like syntax or indentation every once in a while.  When i get an error i would simply tell chatgpt the error i got and let it handle the troubleshooting.  This ring provide, test, improve went on for a good hour or so until i got code that would not throw an error in the Klipper firmware.  Today i am going to try and train the ai by providing it with a lot of macro examples that are already out there and that are somewhat complex in nature.

So far the working macros are:
-tool_check

-and then a correctly defined section for the temperature sensor