# schoolcafe-parser
Parser for SchoolCafe PDF calendars to create ICS files

If your kids school uses https://www.schoolcafe.com/ and you want to get their
lunch menus in your Home Assistant dashboard, DAKboard, or any other calendar,
this might help you.

1. Download a PDF of the one-page version of any menu. This currently works off
   of the monthly calendar. If weekly is interesting, submit an issue (and even
   better, a PR) and I'll add it.
2. Pipe the file to `schoolcafe-parse`, which outputs JSON.
3. Pipe that into `schoolcafe-ics`, which outputs ICS format.

`cat ~/Downloads/september.pdf | ./schoolcafe-parse | ./schoolcafe-ics > september.ics`

From there, you can import that into your calendar. For Google Calendar,
open up settings and choose `Import & export` (on the left), which will allow
you to upload an ICS file and add it to a specific calendar.

## Dependencies

1. This requires Python 3, no specific minor version.
2. https://github.com/py-pdf/pypdf is used for the PDF parsing,
   but no other dependencies.
3. Either clone this repo or just save the scripts locally.

Create a virtualenv, e.g., `python3 -m venv ~/.venvs`, and install `pypdf`
in whatever way you please. `pip`, `uv`, etc.

## About

This is little thing I whipped up in a few hours because I felt like scratching
an itch that came from my wife showing me our kid's lunch schedule. If it's
useful to you, awesome.

I felt like hacking it up as two scripts to pipe between because I like
the idea of single responsibility. Currently there's only one output format,
ICS or the [Internet Calendaring and Scheduling](https://datatracker.ietf.org/doc/html/rfc5545) format,
but you could output some other format as well from the JSON the parser
transforms it into.
