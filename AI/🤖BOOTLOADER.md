# BOOTLOADER - ROBO-KAREL Výlety
## Project summary
**Výlety současnosti** is a magazine in czech language, we are going to semiautomate production of some articles using various LLMs.
The articles should be written in quality czech language. Most of communication in chat threads will be in czech too. 

## Jazyk výstupů — povinné
Každá odpověď ve vláknu i každý zápis do repositáře musí před odesláním projít kontrolou češtiny.

- spisovná čeština, bez překlepů a bez rozbité shody
- žádné anglické slovo v české koncovce (*fourech souborech*)
- žádný poloviční překlad (*Článek jsem nesahe*)
- termíny nástrojů (skill, commit, draft) neskláněj anglicky; buď je nech v základním tvaru, nebo řekni česky

Podrobnosti: `AI\🤖project-instructions.md`, oddíl o jazyku výstupů.

## Instructions
### Peristance and GIT
**Project data and instructions location:** GitHub repo `https://github.com/Jouffan/ai-robo-karel-vylety.git` (branch `main`)

Git intructions live in `AI\🤖Grok-Git-Workflow-generic.md`


### File naming convention
- file types
    - 🤖: Instructions for AI, skills, etc.
    - 📄: Article (product)
    - 📜: Article - example (these are older articles intended to serve as inspiration for writing new ones)
    - 📝: Note, notes,  draft text for future use.
- file status (e.g., 🔴, 🟡, 🟢, ⚠️, ✅, 👍, 🚧, ...)
    Add this to the filename so that the file’s status is clear at a glance when viewing the directory contents.

#### Emoji in filenames (Basic instructions)
Emojis are part of the real name. A close-looking mark is a **different file**.

**What goes wrong if you guess the mark**
- You read or write the wrong file and think you updated the real one.
- A second “ghost” file appears next to the original.
- An empty folder whose name is only an emoji gets created.
- The name comes back garbled (`�`, `%F0%9F…`, Greek lookalikes). Further writes make it worse.

**Do this instead**
- List the folder first. Copy the name exactly as listed.
- Identify files by the plain-text tail (`BOOTLOADER.md`, `example.md`), then keep the emoji that is already on that tail.
- If a name looks broken, stop and list the folder again. Do not invent a “fixed” emoji.
- Do not strip the emoji off a name to make it “safer.”

Full Git rules live in `AI\🤖Grok-Git-Workflow-generic.md`. This note is only so you do not damage files before that file is loaded.


### Additional instructions
`AI\🤖project-instructions.md` - main instruction file always active.

