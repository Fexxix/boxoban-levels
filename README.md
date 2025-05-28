# Boxoban Levels (Structured Fork for Sokoverse)

This is a fork of the [DeepMind Boxoban dataset](https://github.com/deepmind/boxoban-levels) — a collection of Sokoban-style puzzles used in research on model-free planning and reinforcement learning.

This fork re-organizes the original dataset to make it easier to index, access, and use for large-scale puzzle distribution — especially within the [Sokoverse project](https://github.com/Fexxix/sokoverse).

---

## 📦 Why This Fork Exists

In the original dataset, levels are grouped by difficulty (`unfiltered`, `medium`, `hard`), and further split into subfolders (`train`, `valid`, `test`) with 1,000 levels per `.txt` file, each containing puzzles separated by semicolons.

That structure is great for ML research but makes runtime lookup and distribution tricky.

This fork restructures it to support **efficient, category-aware access** for large-scale puzzle serving in live applications like Sokoverse.

---

## 🧩 How It's Used in Sokoverse

[Sokoverse](https://github.com/Fexxix/sokoverse) is a modern Sokoban-inspired game platform featuring:

- 🌍 **Boxoban Challenge Mode** — over 1.5M curated levels distributed uniquely to players.
- 💡 Levels are never repeated across players once solved (unless discarded).
- ⚡ Levels are streamed directly from this repository via GitHub CDN.
- 🧠 Backend logic assigns levels using deterministic IDs:  
  `category-fileNumber-levelNumber` → e.g. `medium-69-420`.

This structured format allows the Sokoverse backend to serve levels quickly without ever storing them in full — only the ID is required.

---

## 📂 Folder Structure

Each category (`medium`, `hard`, `unfiltered`) is now a flat folder of `.txt` files:

```

boxoban/
├── medium/
│   ├── 0.txt
│   ├── 1.txt
│   └── ...
├── hard/
│   ├── 0.txt
│   └── ...
└── unfiltered/
├── 0.txt
├── 1.txt
└── ...

```

Each `.txt` file contains puzzles in this format:

```
; 0
##########
#   ##  ##
#@ ##  ###
# ###.$###
#  ##   ##
#  ## $###
# ### ..##
# ### $ ##
# $    .##
##########

; 1
##########
# . ######
#.   #####
#   ## ###
#      ###
#  #$$$.##
#  #.  @##
#  ###$###
#       ##
##########

; 2
##########
#####    #
```

---

## 📊 Dataset Summary

| Category    | Puzzles                             |
|-------------|-------------------------------------|
| Medium      | 450,000 train + 50,000 validation   |
| Hard        | 3,332                               |
| Unfiltered  | 900,000 train + 100,000 validation + 1,000 test |

---

## 📚 Citation

If you use this dataset in academic work, please cite the original authors:

```

@misc{boxobanlevels,
author = {Arthur Guez and Mehdi Mirza and Karol Gregor and Rishabh Kabra and Sebastien Racaniere and Theophane Weber and David Raposo and Adam Santoro and Laurent Orseau and Tom Eccles and Greg Wayne and David Silver and Timothy Lillicrap and Victor Valdes},
title = {An investigation of Model-free planning: boxoban levels},
howpublished= {[https://github.com/deepmind/boxoban-levels/}](https://github.com/deepmind/boxoban-levels/}),
year = "2018"
}

```

---

## 🙋 Questions?

- 📬 Dataset questions: [theophane@google.com](mailto:theophane@google.com)
- ❓ Fork-specific questions or suggestions?
Please open an issue in this repository. I welcome bug reports, improvement ideas, and integration questions.

---

## 📝 Disclaimer

This is not an official Google product. This fork is maintained independently for use in Sokoverse and other related projects.
