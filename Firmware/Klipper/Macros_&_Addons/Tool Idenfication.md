** Tool Identification
The idea of identifying tools on a multi-tool machine is not a new idea.  It is beneficial to be able to id a tool prior to the machine proceeding with the manufacturing for multitude of reasons.
Crashing tools into the build plate or into another spot on the printer can be detremental and potentially damage your machine.  
With tool identification i wanted to the following to be accomplished:
Identify the tool that is currently installed on the machine
Inform the user of the current tool installed.
Check if the tool is the correct tool for the job ahead
Give the user an option to proceed with the wrong tool installed
Tell the user which should be installed

To identify the tool i am going to be using simple resistors who's values will be so different that the printer can read the voltages/resistance of each and make a determination of which tool is installed.

I don't want to over-complicate the build process of this which is why using resistors to accomplish distiguishing between the tools is desirable.

Some code snippets hat i have produced so far with the aid of ChatGTP are below.  I'm sure this will get modified at some point.

[heater_fan_pin]
pin: your_pin_number_here

[tool_id]
#Ties the Tool to a certain resistor value
pin: heater_fan_pin
resistor: your_resistor_value_here
tolerance: 5
values:
    100: "Tool 1" #3d printer, 0.4 brass, volcano
    500: "Tool 2" #3d printer, 0.8 brass, volcano
    1000: "Tool 3" #3d printer, 0.4 steel, volcano
    2000: "Tool 4" #3d printer, 0.8 steel, volcano
    3000: "Tool 5" #laser
    5000: "Tool 6" #cnc spindle
    10000: "Tool 7" #drag knife
    20000: "Tool 8" #future
    100000: "Maintenance Tool"

[gcode_macro TOOL_CHECK]
variable_tool_id: {printer.gcode_macro.TOOL_ID()}
variable_tool_name: ""
{% if variable_tool_id is none %}
    ### No tool detected ###
    M117 No tool detected
    M300 S440 P200
    M0
{% else %}
    {% set tool_name = printer.config.gcode_macro.TOOL_ID.values.get(variable_tool_id) %}
    {% if tool_name is none %}
        ### Unknown tool detected ###
        M117 Unknown tool detected
        M300 S440 P200
        M0
    {% else %}
        {% set variable_tool_name = tool_name %}
        {% if printer.gcode_macro.TOOL_ID.expected_id is not none and variable_tool_id != printer.gcode_macro.TOOL_ID.expected_id %}
            ### Wrong tool "{{variable_tool_name}}" detected, expected "{{printer.config.gcode_macro.TOOL_ID.values.get(printer.gcode_macro.TOOL_ID.expected_id)}}"
            M117 Wrong tool "{{variable_tool_name}}" detected, expected "{{printer.config.gcode_macro.TOOL_ID.values.get(printer.gcode_macro.TOOL_ID.expected_id)}}"
            M300 S440 P200
            M0
        {% else %}
            # Tool "{{variable_tool_name}}" detected
            M117 Tool "{{variable_tool_name}}" detected
        {% endif %}
    {% endif %}
{% endif %}


