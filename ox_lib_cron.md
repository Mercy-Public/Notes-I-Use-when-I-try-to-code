Server
A Lua implementation of cron, allowing tasks to be scheduled to run periodically at fixed times, dates, and intervals.

Cron expression
A string containing five values separated by white spaces, representing a set of times to execute a task.

Field	Valid values
Minutes	0-59
Hours	0-23
Day of month	1-31
Month	1-12 or jan-dec
Day of week	1-7 or sun-sat
Note: Day of the week is set to match os.date and starts at 1, unlike the cron-standard which starts at 0.

* Wildcards
Represents all values, e.g. * * * * * will run every minute, or * * * * 1 will run every minute on Sunday.

, Lists
Commas can be used to create a list of values, e.g. * * * * sun,mon,tue will run every minute on Sunday, Monday, and Tuesday.

- Ranges
Dashes define a range of values, e.g. 10-30 * * * * will start running the task at the 10th minute, and every minute until the 30th minute.

/ Steps
Slashes can be used for step values, e.g. * */4 * * * will run every 4 hours and is shorthand for * 0,4,8,12,16,20 * * *.

Functions
lib.cron.new
Creates a new cronjob, scheduling a task to run at fixed times or intervals.

lib.cron.new(expression, job, options)
expression: string
A cron expression such as * * * * * representing minute, hour, day, month, and day of the week
job: fun(task: OxTask, date: osdate)
options?: table
debug?: boolean
Return:

task: OxTask