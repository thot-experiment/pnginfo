# auto1111-pnginfo
 an extreremely minimalistic js library to extract PNG info from auto1111 gens

 it works on my machine

## details

 this is an extremely simple library written to extract generation data from pngs generated by [auto1111](https://github.com/AUTOMATIC1111/stable-diffusion-webui/), it works both in the browser and in nodejs (probably deno too?)

 as far as I can tell this works "correctly" with every PNG i've ever generated, and that's good enough for me

## usage

```js
import fs from 'fs/promises'
import PNGINFO from 'pnginfo'

const file = await fs.readFile('generate_waifu.png')
const info = PNGINFO(file)

console.log(info)
```

## notes

PNG Info is actually broken in auto1111, so this aims to be broken the same way. If you have a multi line prompt with the last line starting with `Negative prompt:` that will end up as the negative prompt in the generation, rather than part of the positive prompt. You can also put the Steps/Sampler etc into the negatives and get the same effect. I'm sure there are many other edge cases. Oh yeah also this probably doesn't work on a big endian arch.
