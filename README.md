# minimist-json

You pass in args, and it comes out as JSON. That's it.

For example:

	minimist-json --hello=world

Outputs:

	{"_":[],"hello":"world"}

## cli install

Global install:

	npm install -g minimist-json

## install for module

If you add a script in your `package.json` like:

	"scripts": {
		"generate": "minimist-json --hello=world > file.json"
	}

Than you don't need the global install, just the normal one:

	npm install --save minimist-json

## how to use

This uses [minimist](https://www.npmjs.com/package/minimist) to
parse inputs, but with this difference:

	minimist-json [[transform options] --] [input args]

### transform options

For example, you might want to use the input arg `--thing=[1,2]`
and have it be output as `{"thing":[1,2]}` but you'll notice that
what actually comes out is `{"thing":"[1,2]"}`.

This is because the input args are treated as strings. But with
the transform you can do this:

	minimist-json --json=thing -- --thing=[1,2]

And the output will be `{ "thing": [ 1, 2 ] }`

#### `--json`

Use `.` notation for property reference, aka `{ a: { b: [3] } }`
would be `--json=a.b`

### input args

The arg parsing is passed through [minimist](https://www.npmjs.com/package/minimist),
so look there for how to write args correctly.

## license

Published under the [Very Open License](http://veryopenlicense.com/).

<3
