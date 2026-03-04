---
title: 'The Double-edged Sword of LLM-based Data Reconstruction: Understanding and Mitigating Contextual Vulnerability in Word-level Differential Privacy Text Sanitization'

authors:
  - Stephen Meisenbacher
  - Alexandra Klymenko
  - me
  - Florian Matthes

date: '2025-11-18T00:00:00Z'
publishDate: '2025-11-18T00:00:00Z'

publication_types: ['paper-conference']

publication: 'Proceedings of the 24th Workshop on Privacy in the Electronic Society (WPES 2025)'
publication_short: 'WPES 2025'

abstract: 'Differentially private text sanitization refers to the process of privatizing texts under the framework of Differential Privacy (DP), providing provable privacy guarantees while also empirically defending against adversaries seeking to harm privacy. Despite their simplicity, DP text sanitization methods operating at the word level exhibit a number of shortcomings, among them the tendency to leave contextual clues from the original texts due to randomization during sanitization – this we refer to as contextual vulnerability. Given the powerful contextual understanding and inference capabilities of Large Language Models (LLMs), we explore to what extent LLMs can be leveraged to exploit the contextual vulnerability of DP-sanitized texts. We expand on previous work not only in the use of advanced LLMs, but also in testing a broader range of sanitization mechanisms at various privacy levels. Our experiments uncover a double-edged sword effect of LLM-based data reconstruction attacks on privacy and utility: while LLMs can indeed infer original semantics and sometimes degrade empirical privacy protections, they can also be used for good, to improve the quality and privacy of DP-sanitized texts. Based on our findings, we propose recommendations for using LLM data reconstruction as a post-processing step, serving to increase privacy protection by thinking adversarially.'

summary: 'Exploring how LLMs can both exploit and enhance differential privacy in text sanitization, revealing a double-edged sword effect and proposing adversarial post-processing for improved privacy.'

tags:
  - Large Language Models
  - Privacy-Preserving AI
  - Natural Language Processing

featured: true

hugoblox:
  ids:
    doi: '10.1145/3733802.3764058'

links:
  - type: pdf
    url: '/uploads/Paper_The_Double-edged_Sword_of_LLM-based_Data_Reconstruction.pdf'
  - type: source
    url: 'https://dl.acm.org/doi/full/10.1145/3733802.3764058'

---

Published at **ACM WPES 2025**, this work explores the dual nature of LLM-based data reconstruction in differential privacy, demonstrating how adversarial thinking can strengthen privacy protections.

**Key Findings:**
- LLMs can exploit contextual vulnerability in DP-sanitized texts
- Same LLM capabilities can improve privacy protection
- Recommendations for adversarial post-processing
