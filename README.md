# Sveltekit Auto-Typed i18n

[![npm](https://img.shields.io/npm/v/@abineo/sveltekit-i18n)](https://www.npmjs.com/package/@abineo/sveltekit-i18n)

Vite Plugin to transpile translations from JSON into TypeScript for Sveltekit (TS).

[📖 Documentation](https://github.com/abineo-ag/sveltekit-i18n/blob/main/DOCS.md)
## Notice

Use this library with causion.
There are lot of tests that need to be written and possibly some bugs to be fixed.
But we do not expect to introduce breaking changes.

Found a bug? -> [Contributing](#contributing)

## Installation

```sh
npm install --save-dev @abineo/sveltekit-i18n
```

## Usage

```ts
// vite.config.ts
import { sveltekit } from '@sveltejs/kit/vite';
import type { UserConfig } from 'vite';
import i18n from '@abineo/sveltekit-i18n';

const config: UserConfig = {
	plugins: [i18n({
        {
            src: './src/lib/i18n/src',
            out: './src/lib/i18n',
            folder: 'dist',
            defaultParamType: 'string',
            createGitignore: true,
            createSummary: true,
            defaultLanguage: 'de-CH',
        }
    }), sveltekit()],
};

export default config;
```

```jsonc
// src/lib/i18n/src/de-CH.jsonc
{
	"strongly": {
		"typed": {
			"translations": "Lorem ipsum dolor sit amet."
		}
	},
	"even": {
		"supports": "what? { thing: string }!"
	}
}
```

```html
<script lang="ts">
	import { selectedLanguage, t } from '$lib/i18n';
	selectedLanguage.set('de-CH');
</script>

<main>
	<p>{$t.strongly.typed.translations}</p>
	<p>{$t.even supports('parameters')}</p>
	<!-- Output: <p>what? parameters!</p> -->
</main>
```

## Contributing

If you think you found a bug: [open a issue](https://github.com/abineo-ag/sveltekit-i18n/issues).
Feature request are also welcome.

## License

This library is distributed under the terms of the [ISC License](https://github.com/abineo-ag/sveltekit-i18n/blob/main/LICENSE).  
Find an easy explanation on [choosealicense.com/licenses/isc](https://choosealicense.com/licenses/isc/).
