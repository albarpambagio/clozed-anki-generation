---
name: clozed-anki-generation
description: Create flashcards for spaced repetition learning, compatible with Anki import. Specializes in cloze deletion cards. Use when creating study flashcards, Anki decks, vocabulary cards, memorization aids, or spaced repetition materials from notes or topics. Triggers - create flashcards, make Anki cards, spaced repetition, memory cards, cloze deletion cards, Anki deck.
---

# Flashcard Creator (Cloze-Focused)

Generate effective cloze deletion flashcards optimized for spaced repetition in Anki.

---

## Core Philosophy

> **One card = one retrievable fact.**
> The goal is not to summarize content — it is to create precise memory triggers.

Cloze cards outperform basic Q&A for most factual and conceptual material because:
- The stem sentence provides context, reducing ambiguity
- The deletion forces active recall of the exact fact
- Multiple deletions on one card create linked sister cards automatically

---

## Step 1: Identify What to Card

Before writing, classify each piece of knowledge:

| Type | Example | Best Card Format |
|---|---|---|
| Definition | What is entropy? | Cloze on the term AND the definition in one note |
| Formula | Standard deviation formula | Cloze on the formula expression |
| Property / Rule | When does X apply? | Cloze on the condition |
| Cause → Effect | Why does Y happen? | Cloze on the cause AND the effect in one note |
| Comparison | How does A differ from B? | One note with c1 for A, c2 for B |
| Sequence / Process | Steps of X | One note with c1, c2, c3 for each step |
| Number / Threshold | Critical value at 95% CI | Cloze on the number |
| Notation / Symbol | What does σ represent? | Cloze on the symbol AND its meaning in one note |

**Never card things you don't understand.** Cloze cards for misunderstood material only reinforce confusion.

---

## Step 2: Cloze Deletion Rules

### Rule 1 — One deletion per concept, but consolidate related facts into one note
Each `{{c1::...}}` should hide exactly one retrievable fact. Do not hide a phrase that contains two distinct ideas. However, **group related facts into a single note** using multiple cloze numbers (c1, c2, c3) rather than creating separate notes.

```
❌ The {{c1::mean is the sum of values divided by n, and is sensitive to outliers}}.
✓  The mean is calculated by dividing the sum of values by {{c1::n}}, and is sensitive to {{c2::outliers}}.

❌ (Separate notes)
   Note A: The {{c1::mean}} is calculated by dividing the sum of values by n.
   Note B: The mean is calculated by dividing the sum of values by {{c1::n}}.
✓  (Consolidated note)
   The {{c1::mean}} is calculated by dividing the sum of values by {{c2::n}}.
```

### Rule 2 — The stem must be self-sufficient
The sentence around the deletion must fully constrain the answer. A reader should never ask "wait, what is this card even about?"

```
❌ It equals {{c1::np}}.                          (What equals np? Unknown without context)
✓  The mean of a binomial distribution equals {{c1::np}}.
```

### Rule 3 — Multi-cloze (c1 + c2 + c3) for related facts in one note
Use c1, c2, c3 on the same note when facts are related, complementary, or form a natural pair/group. Anki creates a separate card for each cN. **Prefer consolidation over fragmentation.**

```
✓  The sample mean is denoted {{c1::x̄}}, and the population mean is denoted {{c2::μ}}.
✓  Type I error probability = {{c1::α}}; Type II error probability = {{c2::β}}.
✓  Refresh time comprises three phases: {{c1::data load time}}, {{c2::transformation time}}, and {{c3::model load time}}.
```

Limit to c1–c4 per note. More than four deletions creates cognitive overload.

### Rule 4 — Delete the answer, not the question
The hidden text should be the hard-to-remember part — not the framing.

```
❌ {{c1::The median}} is the middle value of ordered data.   (The word "median" is the easy part)
✓  The median is the middle value that divides ordered data into {{c1::two equal halves}}.
```

### Rule 5 — Avoid naked deletions
Give enough context that the card is answerable without outside knowledge.

```
❌ The formula is {{c1::Σ(x-x̄)²/(n-1)}}.
✓  The sample variance formula is: s² = {{c1::Σ(x − x̄)² / (n − 1)}}.
```

### Rule 6 — Break lists into enumerated cloze within one note
Do not hide an entire list behind a single cloze. Instead, use numbered clozes in one consolidated note.

```
❌ The sampling methods are {{c1::simple random, stratified, cluster, systematic, convenience}}.

✓  The four main sampling methods are {{c1::simple random}}, {{c2::stratified}}, {{c3::cluster}}, and {{c4::systematic}} sampling.
```

### Rule 7 — Cloze both directions within the same note
For key terms, put both the term and the definition in the same note with different cloze numbers.

```
✓  {{c1::Inferential statistics}} uses {{c2::probability}} to draw conclusions from sample data about a population.
```

---

## Step 3: Sentence Framing Patterns

Use these proven stem patterns to write cloze cards that are clear and unambiguous:

### Definition
```
[Term] is defined as {{c1::[definition]}}.
A {{c1::[term]}} is [definition], characterized by {{c2::[key property]}}.
```

### Formula
```
The formula for [concept] is: [name] = {{c1::[formula]}}.
In the formula [formula], [variable] represents {{c1::[meaning]}} and [variable2] represents {{c2::[meaning2]}}.
```

### Condition / When-to-use
```
[Method/test] is used when {{c1::[condition]}}.
The [formula] applies only if {{c1::[assumption]}} and {{c2::[assumption2]}}.
```

### Cause → Effect
```
[Cause] leads to {{c1::[effect]}} and {{c2::[secondary effect]}}.
When [condition], the result is {{c1::[outcome]}}.
```

### Comparison
```
Unlike [A], [B] is {{c1::[distinguishing feature]}}; unlike [B], [A] is {{c2::[distinguishing feature]}}.
[A] measures [X], while [B] measures {{c1::[Y]}} and operates via {{c2::[mechanism]}}.
```

### Numeric threshold / value
```
For a 95% confidence interval, the critical z-value is {{c1::1.96}}.
[Concept] requires at least {{c1::[number]}} [units] to be valid.
```

### Symbol / Notation
```
The symbol {{c1::σ}} represents the population standard deviation.
Population mean is denoted {{c1::μ}} (mu), while sample mean is denoted {{c2::x̄}}.
```

---

## Step 4: The Extra Field

Every card should have an **Extra** field. It does not appear during recall — only after the answer is revealed. Use it for:

- Chapter or topic source (for filtered deck study)
- Hint or disambiguation
- Formula context or worked example
- "See also" related cards

```
Card Text:  The mean of a binomial distribution equals {{c1::np}}.
Extra:      Ch.4 – Binomial Distribution | μ = np; σ = √(np(1−p))
```

---

## Step 5: Anti-Patterns to Avoid

| Anti-Pattern | Why It Fails | Fix |
|---|---|---|
| Clozed the whole answer phrase | Card becomes trivial pattern-matching | Delete only the core fact, keep framing |
| No subject in stem | Card is ambiguous without context | Add the subject explicitly |
| c1 hides two distinct facts | Fails one-fact-per-card rule | Split into c1 and c2 in same note |
| Clozing obvious filler words | Tests reading, not knowledge | Only delete meaningful content |
| Very long deletions | Hard to recall precisely | Shorten or rephrase the sentence |
| Identical twins (c1 and c2 hide same type of thing) | Confusing when both are blank | Differentiate stems or use context clues |
| Cards that only work with the textbook | Not self-contained | Add enough context in the stem |
| Fragmenting related facts into separate notes | Creates redundant cards, harder to maintain | Consolidate into one note with c1, c2 |

---

## Step 6: Anki Export Format

### CSV (Recommended)

Two columns: `Text`, `Extra`. Comma-separated, UTF-8 encoded.

```
"The {{c1::median}} is the middle value that divides ordered data into two equal halves.","Ch.2 – Descriptive Statistics | Center measures"
"Sample variance divides by {{c1::n−1}}; population variance divides by {{c2::N}}.","Ch.2 – Descriptive Statistics | s² = Σ(x−x̄)²/(n−1)"
```

### Import Settings in Anki

1. File → Import → select CSV
2. Note Type: **Cloze**
3. Field mapping: Column 1 → **Text**, Column 2 → **Extra**
4. Enable: **Allow HTML in fields** (for math symbols)
5. Tags: enter deck/topic tags in the import dialog

### Tagging Strategy

Use hierarchical tags for easy filtered deck creation:

```
Subject::Chapter::Topic
stats::ch2::standard-deviation
stats::ch8::confidence-intervals
```

---

## Step 7: Quality Checklist

Before finalizing any batch of cards, verify:

- [ ] Each card tests **exactly one** retrievable fact
- [ ] Related facts are **consolidated into single notes** with c1, c2, c3 rather than fragmented
- [ ] The stem sentence is **self-sufficient** — answerable without outside context
- [ ] The deletion hides the **hard-to-remember** part, not the framing
- [ ] Multi-cloze (c1+c2+c3) used for **related facts in one note**
- [ ] **No naked deletions** — the answer type is always clear from context
- [ ] **No list clozes** — lists use enumerated c1, c2, c3 in one note
- [ ] **Extra field** populated with source chapter and/or context
- [ ] Cards can be answered in **under 10 seconds**
- [ ] **Formulas** have variable meanings in the Extra field
- [ ] Notes with multiple clozes feel like **one cohesive idea**, not random facts stitched together

---

## Quick Reference: Card Count by Content Type

As a rough guide for a typical textbook chapter:

| Content Type | Notes per Unit | Clozes per Note |
|---|---|---|
| Key term / definition | 1 | 2 (term + definition) |
| Formula | 1 | 2–3 (formula + key variables) |
| Rule / condition | 1 | 1–2 |
| Numeric threshold | 1 | 1 |
| Comparison between two concepts | 1 | 2 (one per concept) |
| Process / sequence (n steps) | 1 | n clozes |
| Notation / symbol | 1 | 2 (symbol + meaning) |
