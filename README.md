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

The `vote` command line tool, and underlying library, use `python 3.12` (including [newer language features](https://peps.python.org/pep-0695/)).

To get started:

1. Clone this repository (`git clone git@github.com:front-seat/voter-data-tools.git`)
2. Create a virtualenv (`python -m venv .venv`)
3. Enter the venv (`source .venv/bin/activate`)
4. Install python dependencies (`pip install -r requirements.txt`)
5. Try it! (`./vote.py check your name zipcode dob --details` &mdash; assuming you're in a supported state)

The node stuff (`package.json` and friends) is included only so that we can use [Microsoft's `pyright`](https://github.com/microsoft/pyright) type checker.

You can run tests with `./scripts/test.sh`. They are extremely minimal at the moment; ultimately, we'll want to have a basic suite of unit tests, and a separate set of tests for each state to make sure that the code continues to work correctly.
