# Reverse Engineering

# Reverse Engineering

## Overview / What is it?

> Reverse engineering is the process of analyzing a subject system to identify the system's components and their interrelationships and create representations of the system in another form or at a higher level of abstraction.

Let's break this official definition into questions. Given for example a binary file:

- What does it do if I give it specific *inputs*? What *outputs* does it produce? 
> In other words, we try to analyze its behavior. 

- What is *inside* if I break it down into *smaller* parts? 
> We perform structural analysis through *disassembly*, analyzing *symbols*, or *embedded data*.

- Can I *reconstruct* how it was made or even create a similar program myself?
> This is about recovering / rebuilding the program from the available information.

- Can I *deobfuscate* or *bypass* protections to reveal hidden logic? 
> An example is *software cracking*.

## Real World Applications & Relevance

A large part of cybersecurity involves **analyzing artifacts** that you already have in hand: executables, firmware images, or even memory dumps. Reverse engineering is the discipline that makes this possible.

Some of the main applications include:

- **Malware analysis**: [Malware analysis](https://www.fortinet.com/resources/cyberglossary/malware-analysis) is the study of the unique features, objectives, sources, and potential effects of harmful software and code, such as spyware, viruses, malvertising, and ransomware. It analyzes malware code to understand how it varies from other kinds.

- **Firmware and IoT analysis**: Extracting and analyzing firmware from routers, smart locks, or medical devices to uncover vulnerabilities and undocumented features.

- **Software preservation**: Reverse engineering proprietary or abandoned software, file formats, or protocols so they can still be used or replaced with open alternatives.

- **Studying obfuscation and protections**: Analyzing techniques like *code obfuscation* or [DRM](https://en.wikipedia.org/wiki/Digital_rights_management) to see how programs hide their true logic, and how those protections might be bypassed.

## Recent News & Trends

- **Denuvo and Empress**: [Denuvo](https://en.wikipedia.org/wiki/Denuvo) is one of the most widely used anti-tamper solutions in the gaming industry. The cracker *[Empress](https://www.youtube.com/watch?v=ZUioVa-wdDk)*, known for consistently defeating it, made headlines again in 2025 when announcing a return to Denuvo targets such as [*GTA 6*](https://en.gamegpu.com/game/empress-will-return-to-hack-denuvo-in-2025).

- **AI and Reverse Engineering**: OpenAI and Microsoft [uncovered evidence](https://www.theverge.com/news/601195/openai-evidence-deepseek-distillation-ai-data) suggesting that Chinese AI startup DeepSeek may have used knowledge distillation to train its language model by querying OpenAI’s models and learning from their outputs, effectively reverse engineering their behavior.

## Challenge

If you are interested in trying out a reverse challenge, there is a simple **code-patching exercise** in [../resources/rev_hansapatch](../resources/rev_hansapatch).

There is an ELF executable that can run on Linux systems.

You will need one of the following tools:

* [upx](https://github.com/upx/upx) - a well-known executable packer. It compresses or transforms executables and wraps them in a small loader stub that unpacks the code at runtime.
* [Ghidra](https://ghidra-sre.org/) – for static analysis and decompilation. You can also use [Ida](https://hex-rays.com/ida-free).
* `gdb` – for debugging.

Some complementary tools you may find useful:

* `nm` – list exported symbols.
* `objdump -d` – disassemble functions and inspect call instructions.
* `strings` – quickly check embedded text.


1. Try loading the executable to your static analyzer (Ghidra or Ida). Do you notice anything out of the ordinary? Unpack the executable using `upx`.

>Fun fact: Attackers often use packers to evade detection. By changing the binary’s structure and hiding its real code, a packed file may bypass signature-based detection and make reverse engineering harder.

2. Examine your executable.

2.1. Use `file` to learn more information about your binary. What is a *PIE* executable? 

2.2. The executable is stripped. That means that the static symbol table (.symtab) has been stripped out. But executables often still carry another kind of symbol table that the dynamic linker uses at runtime. Try exploring with `nm -D` to see what remains.

3. The goal is to redirect the program’s control flow so that it calls the hidden function which prints the FLAG. 

>Hint: Do not lose time trying to find a way to solve the challenge by bruteforcing the flag. The aim of the challenge is to redirect your flow 🤓. The value of the FLAG is random.

## Further Reading

- [LiveOverflow](https://www.youtube.com/watch?v=gPsYkV7-yJk)
- [LaurieWired](https://www.youtube.com/watch?v=RnL5HQfq4Ik)
- [Getting started](https://0xinfection.github.io/reversing/)
- [crackmes.one](https://crackmes.one/)
- [flare-on](https://flare-on.com/)
