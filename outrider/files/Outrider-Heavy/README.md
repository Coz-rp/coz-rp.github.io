# Outrider Heavy

Version 1.0. A roleplay preset for models you run yourself, in SillyTavern's Text Completion mode with KoboldCpp.

**Outrider Heavy** (about 4,070 tokens) is a large rule set, compressed, for Gemma 4 31B, which can carry it.

Running a smaller model? Get Outrider instead: about 730 tokens of plain rules, for Gemma 4 12B and E4B, Mistral, Llama 3.1, and Qwen.

## Your model

| Model | Graphics card | Sampler preset | Instruct template | Context template | Context |
|---|---|---|---|---|---|
| Gemma 4 31B and 26B | 24 GB and up | Outrider Heavy - Samplers | Gemma 4 WH (in `templates`) | Gemma 4 | 32K |

It was built on the plain model, not a finetune. A finetune should work with its base model's row. Gemma 4 26B shares the 31B row but was not tested. The graphics card sizes are estimates from memory use: everything was run on one 24 GB+ card, with KoboldCpp 1.124.2.

## Set it up

1. Start KoboldCpp with your model's file from the `koboldcpp` folder (Load Config, then pick your model file). It sets the context size and cache options. On a smaller card, lower the context there and in SillyTavern to match.
2. In SillyTavern, connect to KoboldCpp under Text Completion.
3. Open Advanced Formatting (the **A** icon). Import `Outrider Heavy - System Prompt.json` from the `sysprompt` folder as the System Prompt. Pick the Instruct Template and Context Template from your row of the table, importing the one from `templates` first if your row points there. Turn Instruct Mode on.
4. Open the sampler panel (the sliders icon) and import the file from `TextGen Settings` that your row names. SillyTavern asks whether to allow the preset's regex scripts. Say yes: they run the reply flags and the sex-scene switch.

## Outrider Heavy in Chat Completion

Outrider Heavy also comes as a Chat Completion preset, `Outrider Heavy CC`, in the `Chat Completion` folder. It sends the same text, with every block as a switch: point of view, tense, length, and each module. Use it if you'd rather toggle than edit.

1. Start KoboldCpp the same way.
2. In SillyTavern, pick Chat Completion and the source Custom (OpenAI-compatible). For the URL, enter the address KoboldCpp shows when it starts, with `/v1` on the end.
3. Import `Outrider Heavy CC.json` in the Chat Completion presets panel, and say yes to its regex scripts.
4. Open Additional Parameters, below the URL, and paste this into Include Body Parameters. It carries the banned phrases, Min P, and DRY settings, which KoboldCpp reads:

```
min_p: 0.05
dry_multiplier: 0.8
dry_base: 1.75
dry_allowed_length: 2
dry_sequence_breakers: ["\n", ":", "\"", "*", "·", "[", "]", "📍", "🕰", "🗓", "👥", "#"]
banned_tokens: ["lets out a", "let out a", "a sharp,", "her heat", "center of her", "jagged", "heavy thud", "reach his eyes", "reach her eyes", "reach their eyes", "ghost of a smile", "unhurried", "for a long moment", "breath catches", "breath catching", "breath hitches", "breath hitching", "weight of it", "something shifts", "something shifted", "shiver down", "shivers down", "a low hum", "knuckles", "mask of", "flicker of", "predatory", "ragged", "dull thud", "wet heat"]
```

The preset holds no connection settings, so importing it leaves your own endpoint, model, and parameters as they are. No chat template is needed in SillyTavern: KoboldCpp applies the model's own.

## What to know

- **Replies are plain roleplay.** No scene header, trackers, or styled text boxes: narration in italics, dialogue in quotes, and nothing else.
- **Point of view and tense follow your story.** The preset keeps whatever the card's greeting and the chat already use. If nothing sets them, it writes in present tense and calls you "you". To fix them, edit the `<turn>` section in Post-History Instructions.
- **Explicit wording switches on when you do.** The explicit-prose rules and the intimacy draws are only sent once one of your last three messages is sexual. A story scene never sees them, which keeps characters from steering every scene toward sex.
- **Put lorebook entries after the character card,** not before it. Entries that land before the card make the model reread most of the prompt every turn.
- **It needs SillyTavern's current macro engine,** which is on by default.
- **No jailbreaks.** A plain model that refuses something will still refuse it.

Outrider Heavy is public domain. Take whatever's useful.
