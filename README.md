# TIL
Today I Learned

### Hide Whitespace Changes in GitHub Diffs
Ever have someone push a commit that involves a lot of real changes mixed in with a bunch of less-meaningful whitespace?
Add `?w=1` to the URL to see the diff with whitespace ignored.

### PUT vs. PATCH in RESTful APIs
* `POST` send a payload to create an entry from scratch
* `PUT` send a payload to replace **_ALL_** of a preexisting entry
* `PATCH` send a payload to replace **_PART_** of preexisting entry

### Git Commit Messages
* Messages wrap at the 72nd character mark
* See also: _the “50/72" rule_
