# Green Brother 👀

In this online education world it's really hard for teachers to know whether the
students are working on the expected exercises or doing completely
different activities(gaming, social media, etc...)

The goal is to create a web application where the teachers can monitor whether
the students are runnning irrelevant applications and they can do some manual
actions(like check on them on a chat platform)

## Architecture

- There should be a backend application which receives incoming data
from the devices of the students.
- A frontend is necessary where the teacher can conveniently see the incoming data
- Obviously it's not possible to see running processes on a computer through
internet, there should be an application that runs on the computers of the students.
This could be a python script, a background demon process, etc... which
makes HTTP requests to the backend application in every 30 seconds or so
and sends the neccessary information to the backend.
You can assume that the student device is running windows for now.

## Functional expectations

- The suspicious applications or behaviour should be displayed as a
warning next to the students.
- Teachers should be able to tell the application if an application
is not suspicios. For example if the main communication platform that
the class uses is Discord, it should not be reported as suspicious.
- It is not an explicit requirement, that there are more teachers and
the students belong to a specific teacher, you can do it in a way that
we have one teacher and all the students report to that one. Obviously if
you solve that multiple teacher can sign in and every student belongs to a single
teacher that is awesome :)

## Edge cases

You have to prepare that today's children are very smart and they can outplay
an application if it's not robust enough. For example they might close their local
application which reports to the backend so the backend should check whether these
reports are received in the expected intervals and if not, that should also
reported as suspicious event.

Also someone might have 2 computers and on one of them where they are running the
local application, nothing special is happening while they are hunting zombies
on the other machine. Besides the running applications you might track
other activities like mouse distance, changing active windows, etc...
Be careful to don't receive any sensitive data. It's not nice to track
the exact keys they are pressing.

These were just examples, try to make your application as robust as possible
so they can not outsmart your application.

## Extra points

- It would be very nice if the teacher doesn't have to refresh the application
to see the new suspicious activities. The frontend should automatically display
new stuff. This could be achieved with polling, or even better, with WebSocket
connection between the frontend and backend.

- Another important aspect is that it's not incovinient for the students.
For example: asking them to install python and run a python script in a terminal
window is not the best experience as a user.

- It's not easy to tell if someone is using a specific web application like
Facebook, because obviously it would be a pretty serious security issue if that
would be possible.
Still it's a really important use case in an application like this so a creative
solution is necessary here. For example if we can detect a web browser process
that eats up 500 MB RAM we can be pretty sure that it's not StackOverflow.

- If we are dealing with IT students, they might reverse engineer our application
and write their own script which sends fake data. Find out a clever authentication
process which they can't replicate without a secret or private key.

## Tips and tricks

- If something is not working properly, find a way to mock it. For example
if the student side application is not behaving well, you could just make
a script that feed random or pre-filled data to the backend

## Scoring

The following aspects will be scored on a scale from 1-10:

- Usability(from both teacher and student side point of view)
- Robustness(how effective is the suspicious activity detection)
- Presentation
