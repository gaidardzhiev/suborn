# SUBORN

*Subvert. Observe. Research. Never deploy.*

This repository contains the paper [**Suborn: A Threat Model for LLM-Orchestrated Firmware Agents**](./suborn.pdf) by [Ivan Gaydardzhiev](https://github.com/gaidardzhiev) (2026).

## On the Nature of the Threat

The paper defines and analyzes a threat class that does not yet appear in the public literature: the LLM orchestrated firmware agent. An implant embedded in the pre OS execution environment whose command selection, operational strategy, and self modification behavior are delegated to a remote large language model rather than encoded in the firmware binary.

The central observation is that this architecture separates capability from intent in a way that breaks the assumption underlying firmware image analysis as a detection mechanism. A firmware binary can be fully analyzed and found to contain no attack logic in the conventional sense, and yet be a complete attack platform, because the intent is held externally by a model the defender cannot observe or interrogate.

## The Structure of the Argument

- The threat model and a formal definition of the attack class
- Two insertion substrates: the Coreboot ramstage and the Intel Management Engine, analyzed for their respective capability profiles, persistence properties, and insertion difficulty
- The full range of insertion vectors: build pipeline compromise, physical SPI flash access, OS level exploitation of firmware interfaces, and firmware update mechanism abuse
- The LLM controller architecture: communication model, conversation memory across boot cycles, trigger model, killswitch design, and command primitive table
- LLM directed self modification: the agent's capacity to rewrite its own firmware binary, extend its primitive table, and modify legitimate firmware components in response to detection signals or controller direction
- Detection gaps created by this architecture across static analysis, behavioral analysis, forensic reconstruction, and signature detection
- The open question of local inference inside ME class hardware, and the memory constraints that currently make it infeasible
- A structured enumeration of open problems for defenders, none of which have adequate solutions in the current firmware security literature

## Contents

- [suborn.pdf](./suborn.pdf) the paper

- [suborn.tex](./suborn.tex) the LaTeX source

- [tex2pdf.sh](./tex2pdf.sh) an interactive POSIX shell utility that builds the LaTeX source

## License

The paper is released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) by Ivan Gaydardzhiev, 2026.

The code in this repository is released under [GPL-3.0-only](./COPYING).
