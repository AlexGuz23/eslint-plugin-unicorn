# Enforce better string content

β This rule is _disabled_ in the `recommended` [config](https://github.com/sindresorhus/eslint-plugin-unicorn#preset-configs).

π§π‘ This rule is automatically fixable by the [`--fix` CLI option](https://eslint.org/docs/latest/user-guide/command-line-interface#--fix) and manually fixable by [editor suggestions](https://eslint.org/docs/developer-guide/working-with-rules#providing-suggestions).

<!-- end auto-generated rule header -->
<!-- Do not manually modify this header. Run: `npm run fix:eslint-docs` -->

Enforce certain things about the contents of strings. For example, you can enforce using `β` instead of `'` to avoid escaping. Or you could block some words. The possibilities are endless.

_It only reports one pattern per AST node at the time._

This rule ignores the following tagged template literals as they're known to contain code:

- ``gql`β¦` ``
- ``html`β¦` ``
- ``svg`β¦` ``
- ``styled.*`β¦` ``

**This rule has no effect by default. You need set [`patterns`](#patterns) to check string content.**

## Fail

```js
/*eslint unicorn/string-content: ["error", { "patterns": { "'": "β" } }]*/
const foo = 'Someone\'s coming!';
```

## Pass

```js
/*eslint unicorn/string-content: ["error", { "patterns": { "'": "β" } }]*/
const foo = 'Someoneβs coming!';
```

## Options

Type: `object`

### patterns

Type: `object`

The example below:

- Adds a custom `unicorn` β `π¦` replacement.
- Adds a custom `awesome` β `π` replacement and a custom message.
- Adds a custom `cool` β `π` replacement, but disables auto fix.

```json
{
	"unicorn/string-content": [
		"error",
		{
			"patterns": {
				"unicorn": "π¦",
				"awesome": {
					"suggest": "π",
					"message": "Please use `π` instead of `awesome`."
				},
				"cool": {
					"suggest": "π",
					"fix": false
				}
			}
		}
	]
}
```

The key of `patterns` is treated as a regex, so you must escape special characters.

For example, if you want to enforce `...` β `β¦`:

```json
{
	"patterns": {
		"\\.\\.\\.": "β¦"
	}
}
```

## Pattern ideas

- Enforce `β` over `'` to avoid escape.
- Enforce `β¦` over `...` for better typography.
- Enforce `β` over `->` for better typography.
- Enforce `^https:\\/\\/` over `^http:\\/\\/` to secure your links.
