---
name: interview-prep-documentation
description: Create interview preparation documents for data analytics projects. Use when preparing talking points, anticipated questions, and structured Q&A guides for job interviews, portfolio reviews, or case study presentations.
---

# Interview Prep Documentation

Create structured interview preparation documents for data project walkthroughs.

## Document Structure

```
docs/INTERVIEW_TALKING_POINTS.md
├── Project Walkthrough
├── Technical Decisions
├── Data Challenges
├── Key Insights
├── Business Recommendations
├── What I'd Do Differently
├── Business Impact
├── Technical Deep-Dives
├── Behavioral Questions
└── Quick Reference Card
```

## Section Templates

### Project Walkthrough

Answer structure: **Business Question → Data Model → KPIs → Insights → Recommendations**

```markdown
**Script:**
> "This project analyzes [X] from [source], across [time period]. I started with a **business question**: '[question]'. I built a **star schema** in PostgreSQL with `fact_orders` at the center... I defined **KPIs** like [metric 1], [metric 2]... **Key findings**: [finding 1], [finding 2]. My **recommendations** focus on [recommendation]."
```

### Technical Decisions

For each major tool/library choice, prepare:
- Reason for choice (3-5 bullet points)
- Trade-offs and alternatives considered
- Production considerations

### Data Challenges

For each challenge, structure as: **Problem → Impact → Resolution**

```markdown
**Challenge: [Name]**
> "[Describe the problem]. I resolved it by [solution]. This [impact]."
```

### Business Recommendations

For each recommendation, include:

```markdown
**[Title]** ([Priority])
- **Target:** [Who it addresses]
- **Action:** [What to do]
- **Expected Impact:** [Quantified outcome]
```

### What I'd Do Differently

List 3-5 improvements showing growth mindset:
- What you'd add given more time/data
- Tools/methods you'd use now
- Process improvements

### Quick Reference Card

```markdown
**Memorize These 5 Things:**
1. **[Metric]**: [Value] (context)
2. **Problem**: [Core problem statement]
3. **Solution**: [Core solution]
4. **Tech Stack**: [tools used]
5. **Differentiator**: [what makes it stand out]

**One-Sentence Project Summary:**
> "[One sentence: what + stack + key finding + impact]"
```

## Workflow

```
Task Progress:
- [ ] 1. Write Project Walkthrough script
- [ ] 2. Document Technical Decisions for each tool
- [ ] 3. List Data Challenges with resolution
- [ ] 4. Compile Key Insights with numbers to memorize
- [ ] 5. Draft Business Recommendations with impact
- [ ] 6. Add What I'd Do Differently
- [ ] 7. Write Behavioral Questions
- [ ] 8. Fill Quick Reference Card
```

## Quality Checklist

- [ ] Every section has specific numbers and facts
- [ ] Technical decisions explain "why" not just "what"
- [ ] Data challenges show problem-solving process
- [ ] Business impact is quantified
- [ ] Quick reference card is memorable (5 bullet points)
- [ ] Can explain the project in 1 sentence
