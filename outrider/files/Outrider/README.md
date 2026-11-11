# Outrider

Version 1.0. A roleplay preset for models you run yourself, in SillyTavern's Text Completion mode with KoboldCpp.

**Outrider** (about 730 tokens) is a short set of plain rules that small and mid-size models actually follow.

Running Gemma 4 31B? Get Outrider Heavy instead. That model does better with a much larger rule set.

## Pick your model

| Model | Graphics card | Sampler preset | Instruct template | Context template | Context |
|---|---|---|---|---|---|
| Gemma 4 12B | 12 to 16 GB | Outrider - Samplers | Gemma 4 WH (in `templates`) | Gemma 4 | 16K |
| Gemma 4 E4B | 6 to 8 GB | Outrider - Samplers | Gemma 4 | Gemma 4 | 16K |
| Mistral Small 3.2 24B | 16 to 24 GB | Outrider Mistral - Samplers | Mistral V7-Tekken | Mistral V7-Tekken | 16K |
| Mistral Nemo 12B | 8 to 12 GB | Outrider Mistral - Samplers | Mistral V3-Tekken | Mistral V3-Tekken | 16K |
| Llama 3.1 8B | 6 to 8 GB | Outrider - Samplers | Llama 3 Instruct | Llama 3 Instruct | 16K |
| Qwen3.5-9B | 8 to 12 GB | Outrider - Samplers | ChatML WH Qwen (in `templates`) | ChatML | 16K |
| Qwen3.8-27B | 24 GB | Outrider - Samplers | ChatML WH Qwen (in `templates`) | ChatML | 16K |

It was built on the plain models, not finetunes. A finetune should work with its base model's row. The graphics card sizes are estimates from memory use: everything was run on one 24 GB+ card, with KoboldCpp 1.124.2.

## Set it up

1. Start KoboldCpp with your model's file from the `koboldcpp` folder (Load Config, then pick your model file). It sets the context size and cache options. On a smaller card, lower the context there and in SillyTavern to match.
2. In SillyTavern, connect to KoboldCpp under Text Completion.
3. Open Advanced Formatting (the **A** icon). Import `Outrider - System Prompt.json` from the `sysprompt` folder as the System Prompt. Pick the Instruct Template and Context Template from your row of the table, importing the one from `templates` first if your row points there. Turn Instruct Mode on.
4. Open the sampler panel (the sliders icon) and import the file from `TextGen Settings` that your row names. SillyTavern asks whether to allow the preset's regex scripts. Say yes: they run the reply flags and the sex-scene switch.

## What to know

- **Replies are plain roleplay.** No scene header, trackers, or styled text boxes: narration in italics, dialogue in quotes, and nothing else.
- **Point of view and tense follow your story.** The preset keeps whatever the card's greeting and the chat already use. If nothing sets them, it writes in present tense and calls you "you". To fix them, edit the `<turn>` section in Post-History Instructions.
- **Explicit wording switches on when you do.** The explicit-prose rules are only sent once one of your last three messages is sexual. A story scene never sees them, which keeps characters from steering every scene toward sex.
- **Put lorebook entries after the character card,** not before it. Entries that land before the card make the model reread most of the prompt every turn.
- **A 12 GB card and Gemma 12B:** use the Q5_K_M file. Q6_K at 16K context uses about 11.6 GB and leaves no room for the desktop.
- **It needs SillyTavern's current macro engine,** which is on by default.
- **No jailbreaks.** A plain model that refuses something will still refuse it.

Outrider is public domain. Take whatever's useful.
