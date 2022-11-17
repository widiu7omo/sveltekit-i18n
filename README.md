# Sveltekit Auto-Typed i18n

![Status](https://gitlab.com/rokkett/sveltekit-i18n/badges/main/pipeline.svg?ignore_skipped=true&key_text=tests&key_width=40)
![Coverage](https://gitlab.com/rokkett/sveltekit-i18n/badges/main/coverage.svg)
![Beta](https://img.shields.io/badge/status-stable--beta-important)
![npm](https://img.shields.io/npm/v/@rokkett/sveltekit-i18n)

Rollup/Vite Plugin to transpile translations from JSON into TypeScript for Sveltekit.

-   [Documentation](https://gitlab.com/rokkett/sveltekit-i18n/-/blob/main/DOCS.md)
-   [NPM](https://www.npmjs.com/package/@rokkett/sveltekit-i18n)
-   [GitLab](https://gitlab.com/rokkett/sveltekit-i18n)

## Notice

This library is ready for production, but do so with causion.
There are lot of tests that need to be written and possibly some bugs to be fixed.
We do not expect to have breaking bugs or introduce breaking changes.

Found a bug? -> [Contributing](#contributing)

## Installation

```sh
npm install --save-dev @rokkett/sveltekit-i18n
```

## Usage

```ts
// vite.config.ts
import { sveltekit } from '@sveltejs/kit/vite';
import type { UserConfig } from 'vite';
import i18n from '@rokkett/sveltekit-i18n';

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
	import { setLanguage, t } from '$lib/i18n';
	setLanguage('de-CH');
</script>

<main>
	<p>{$t.strongly.typed.translations}</p>
	<p>{$t.even supports('parameters')}</p>
	<!-- Output: <p>what? parameters!</p> -->
</main>
```

## Contributing

If you think you found a bug: [open a issue](https://gitlab.com/rokkett/sveltekit-i18n/-/issues).
Feature request are also welcome.

## License

This library is distributed under the terms of the [ISC License](./LICENSE).  
Find an easy explanation on [choosealicense.com/licenses/isc](https://choosealicense.com/licenses/isc/).
