---
name: minimal-ai-editing
description: Use when English academic or thesis prose is flagged as AI-written, sounds over-polished or formulaic, or needs grammar correction while preserving the author's voice, citations, LaTeX, facts, and sentence structure.
---

# Minimal AI Editing

## Core Rule

Make the smallest useful edit. Preserve the author's reasoning, wording habits, facts, citations, LaTeX commands, comments, and technical terms. Do not promise a detector score or claim that detection can be reliably bypassed.

## Choose the Workflow

Use one of these workflows:

1. **Minimal replacement** when only a few words or transitions sound formulaic.
2. **Author-led reordering** when the paragraph structure sounds generated.
3. **Grammar-only correction** when the author provides a rough draft in their own English.

If repeated rewrites still sound generated, stop rewriting the full paragraph. Extract the claims in Chinese and ask the author to choose the order or write a rough English version. Then correct only clear grammar problems.

## Minimal Replacement

1. Mark only the strongest AI-like expression in each sentence.
2. Replace at most one main issue per sentence.
3. Delete an unnecessary transition instead of replacing every transition with `Also`.
4. Keep technical accuracy even when the result is slightly less polished.
5. Return the edited passage first and a short replacement list second.

Prioritize:

- Template transitions: `Furthermore`, `Moreover`, `Additionally`, `Consequently`, `Therefore`, `Thus`, `In conclusion`, `In summary`, `In order to`
- Inflated wording: `significant`, `significantly`, `notably`, `particularly`, `profound`, `comprehensive`, `crucial`, `imperative`, `robust`
- Over-formal verbs: `delve into`, `underscore`, `highlight`, `exemplify`, `facilitate`, `mitigate`, `ascertain`, `endeavor`, `operationalize`
- Vague nouns: `aspect`, `factor`, `landscape`, `realm`, `nuance`, `manifestation`
- Repeated structures: colon explanations, `not only ... but also`, repeated `This ...` conclusions, and complete definition-example-contrast-summary sequences

Prefer plain alternatives only when they fit the sentence:

| Formulaic wording | Possible replacement |
| --- | --- |
| Furthermore / Moreover / Additionally | Also, or delete |
| Consequently / Therefore / Thus | So, For this reason, or delete |
| In conclusion / In summary | Overall, or delete |
| In order to | To |
| significant | important, large, clear |
| particularly | especially |
| robust | strong |
| mitigate | reduce |
| facilitate | help |
| identify | find |
| manifest as | appear as |
| methodology | method |
| prior to | before |

Do not change domain terms such as `throughput`, `NCCL`, `GPU utilization`, `MTTF`, `MTTR`, or `ETTR` merely because they are formal.

## Author-Led Reordering

Do not rewrite immediately. Extract short movable claims:

```text
关键句：
1. [English claim]
   中文：[简短中文翻译]
2. [English claim]
   中文：[简短中文翻译]

请按你的逻辑回复顺序，例如 2-1。之后再整理英文。
```

Preserve facts, numbers, citations, and technical terms. Separate definitions, evidence, examples, and conclusions. Remove template connectors during extraction.

After the author provides an order:

- Follow it unless it creates a factual error.
- Add only necessary transitions.
- Keep sentence lengths and structures slightly uneven.
- Do not add new claims.

## Grammar-Only Correction

When editing the author's own draft:

- Correct grammar that blocks understanding or is clearly wrong.
- Preserve understandable non-native phrasing and personal word choices.
- Do not make every sentence equally smooth or complete.
- Do not add explanations of why every fact matters.
- Prefer direct author actions such as `we collected`, `we checked`, and `we found` when they reflect the actual research.
- Never insert mistakes deliberately.

## Punctuation

When the author flags punctuation as formulaic, replace colon or semicolon explanations with separate sentences. Avoid em dashes unless the author already uses them.

## Output

For direct editing:

```text
[edited passage]

替换点：
- `old` -> `new`
```

Keep notes short. For author-led reordering, return only the numbered claims and Chinese translations until the author supplies an order.

