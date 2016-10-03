# TIL
Today I Learned

### Hide Whitespace Changes in GitHub Diffs
Ever have someone push a commit that involves a lot of real changes mixed in with a bunch of less-meaningful whitespace?
Add `?w=1` to the URL to see the diff with whitespace ignored.

---

### PUT vs. PATCH in RESTful APIs
* `POST` send a payload to create an entry from scratch
* `PUT` send a payload to replace **_ALL_** of a preexisting entry
* `PATCH` send a payload to replace **_PART_** of preexisting entry

---

## Git

### Git Commit Messages
* Messages wrap at the 72nd character mark
* See also: _the “50/72" rule_

### `git commit -n`
* `-n` option bypasses the pre-commit and commit-msg hooks
* Occasionally needed when committing a work-in-progress, if
the `'karma:threshold'` pre-commit hook fails
```
ERROR [Threshold]: Failed minimum coverage threshold expectations
```
https://git-scm.com/docs/git-commit

---

## `module.exports` and `require`

### module.exports a Value
```
// file: myModule.js
module.exports = 'some example value';

// file: myModule.spec.js
var myModule = require('./myModule.js');
var assert = require('chai').assert;

describe('myModule', function () {
    it('should load', function () {
        assert.equal('some example value', myModule);
    });
});
```

### module.exports a Function
```
// file: add.js
module.exports = function (a, b) {
    return a + b;
};

// file: add.spec.js
var add = require('./add.js');
var assert = require('chai').assert;

describe('add', function () {
    it('should add two numbers', function () {
        assert.equal(23, add(20, 3));
    });
});
```

---

### stubby4node - Sequence of Responses
* `response` property can be a _sequence_
* Note the dashes (`YAML` array syntax)
indicating two children under the `response` parent

```
-   request:
        url: ^/api/example/1234/[\w_-]+/asdf$
        method: PUT
    response:
    -   latency: 1500 # latency simulates API delay
        status: 200
        headers:
            content-type: application/json
        file: test/api-mocks/responses/example/asdf.json
    -   status: 404 404 # second (even-numbered) request returns 404
```
https://github.com/mrak/stubby4node

---

## CSS

### Margin Property
```
margin: 10px                 // applies to all sides
margin: 10px 20px            // 10 applies to top & bottom, 20 for left and right
margin: 10px 20px 30px       // 10 for top only, 20 for left and right, 30 for bottom only
margin: 10px 20px 30px 40px  // each side has a unique value
```

* Mnemonic for remembering the order:
  * start at North (top) and then travel clockwise
  * Top, Right, Bottom, Left
* One opinion (code style) is to _always_ use the longhand version
  * Listing all four values (even if some are the same) may be more maintainable (think `git diff`)
  * While the one-value and four-value versions of this syntax are easily remembered,
the two-value and three-value versions of this syntax are often forgotten
