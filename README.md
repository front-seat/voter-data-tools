# FrontSeat Voter Data Tools

_Warning: this is very new code._

Contains a command line tool (`./vote.py`), and python library (`vlib`), to check voter registration status.

Currently we support checking in:

- Georgia
- Michigan
- Wisconsin

Checking registration is accomplished by interacting directly with Secretary of State websites. Eventually, we'll support any state that has a website for checking registration status.

### Check registration of a single voter

To check whether a voter is registered:

```
./vote.py check <first-name> <last-name> <zip> <dob YYYY-MM-DD> [--details]
```

This will tell you whether the user is registered to vote. You can request extra details (registration date, current status, etc.) with the `--details` flag.

### Check registration of multiple voters in bulk

There is also a tool to check every record in a CSV file:

```
./vote.py check-csv <input-file.csv> [--details]
```

A new CSV is written to `stdout` with the same fields as the input CSV plus extras related to the registration check.

### Getting started

This uses `python 3.12`. Clone this repository, create a venv (`python3 -m venv .venv`), enter it (`source .venv/bin/activate`), and the install the requirements (`pip install -r requirements.txt`). After that, `./vote.py` should work as expected.
