---
name: content-intelligence
description: Summarize informational content such as conference talks, training sessions, webinars, presentations, lectures, and voice recordings into clear structured insights and takeaways. Use when the goal is knowledge extraction and learning rather than operational decisions and action tracking.
---

# Content Intelligence

## Overview

This skill transforms raw transcripts of informational content (conference talks, training sessions, webinars, presentations, lectures, podcasts, or voice notes) into clear, well-structured summaries focused on insights, frameworks, mental models, and actionable learnings. It prioritizes faithful extraction and active synthesis of ideas while remaining conservative with inference. The output is designed to support deep understanding, reflection, and real-world application.

## Core Principles

- Faithfulness first: Only include information directly supported by the transcript. Never hallucinate concepts, frameworks, mental models, or claims.
- Conservative extraction with strong synthesis: Extract key ideas faithfully, then actively synthesize them into higher-order patterns, mental models, and cross-cutting themes where strongly supported. Avoid both over-extraction and shallow listing.
- Insight-oriented structure: Organize output around themes, mental models, perspective shifts, and learnings rather than decisions and owners.
- Professional neutral tone with technical fidelity: Preserve technical depth, nuance, and the speaker’s original intent. Avoid oversimplification of complex ideas.
- Speaker handling: Map speaker labels when present (especially useful for panels). For single-presenter content, treat the main speaker clearly.
- Adaptive depth: Adjust level of detail and synthesis based on content length and complexity (concise for short talks, deeper synthesis for long-form training or dense material).

## Processing Steps (Perform Internally)

1. Identify the primary speaker(s) and any supporting speakers or panelists. Map labels to real names when context allows.
2. Determine the overall topic, format (keynote, workshop, panel, training module, etc.), and target audience if inferable. Assess whether the content is relatively concise or long-form/dense.
3. Extract core themes, frameworks, models, and key ideas with high fidelity.
4. Actively synthesize related ideas into higher-order mental models, patterns, and cross-cutting themes where the transcript strongly supports such connections.
5. Identify notable insights, mental models, or shifts in perspective presented by the speaker.
6. Surface practical implications and applications when clearly discussed or very strongly implied.
7. Capture memorable quotes, stories, or moments that best illustrate key ideas.
8. Note any open questions, tensions, or areas the speaker flagged for further exploration.
9. Record any resources, tools, books, or references mentioned.
10. For long or dense transcripts, use topic-level chunking and prioritize synthesis of higher-leverage patterns over exhaustive coverage of every point.

## Required Output Format

Output ONLY clean Markdown using these exact headings in this exact order. Begin directly with the first heading. Do not add preamble or meta commentary. Adjust depth of sections based on content length and density (see Advanced Modes).

# Content Summary: [Title or Inferred Topic] — [Date/Speaker]

## Overview

One tight paragraph describing the content, its main purpose, and the core value it delivers.

## Speaker(s)

- List primary speaker(s) and any additional speakers or panelists. Include role or affiliation when available.

## Key Themes

- Major topics or themes covered. Group related ideas together. Aim for 3–7 high-level themes. For longer content, these may be broader and more synthesized.

## Main Ideas & Frameworks

- Core concepts, models, frameworks, or mental models presented. Describe them clearly and explicitly note how ideas connect or build on each other.

## Core Mental Models & Perspective Shifts

- Higher-order mental models, worldviews, or fundamental shifts in thinking that the speaker advocates or demonstrates. Focus on ideas that reframe how one sees a domain, problem, or system. This section emphasizes synthesis over listing.

## Notable Insights & Takeaways

- The most important or thought-provoking points. Focus on ideas that shift understanding or provide new perspective. Prioritize depth and clarity over quantity. Attribute to speaker when relevant.

## Practical Implications & Applications

- How the ideas can be applied in real work, decision-making, or life. Include both explicitly stated applications and strongly implied ones (with a brief "Why implied" note when needed). Keep this insight-oriented rather than turning it into a task list.

## Memorable Quotes & Moments

- Powerful, insightful, or illustrative quotes and stories. Include approximate timestamps when available. Limit to the most impactful ones (typically 3–6).

## Open Questions & Further Exploration

- Questions raised (explicitly or implicitly) that were left open. Areas the speaker suggested need more thought, research, or experimentation.

## Resources & References

- Books, tools, papers, websites, frameworks, or other resources mentioned by the speaker.

## Key Moments (Timestamps)

2–4 notable exchanges, powerful moments, turning points, or illustrative stories with approximate timestamps.

## Strict Rules

- Never hallucinate frameworks, models, mental models, or insights not present in the transcript.
- Actively synthesize where strongly supported, but do not force connections. When in doubt about synthesis, stay closer to explicit content.
- Prefer under-extraction on implied applications or insights. When in doubt, leave it out or clearly mark it.
- For any implied applications included, add a short "Why implied" explanation.
- Preserve technical accuracy, nuance, and complexity. Do not oversimplify ideas for the sake of accessibility — especially in technical or engineering contexts.
- When speaker attribution is uncertain, note it rather than guessing.
- For long-form or dense content, prioritize synthesis of higher-level patterns, mental models, and cross-cutting themes over exhaustive detail in every section.
- Do not add reasoning, meta commentary, or apologies. Begin directly with the "# Content Summary" heading.

## Additional Guidance

- If metadata (title, speaker name, date, event name, or format) is provided, incorporate it into the summary and use it to improve context and speaker mapping.
- When timestamps are available, reference them in Key Moments, Quotes, and where they add value.
- Maintain clean, scannable Markdown with proper heading hierarchy and bullet formatting.
- For very long transcripts (full-day training, multi-hour conferences, or dense technical material), focus on distilling the highest-leverage ideas, mental models, and cross-cutting themes rather than attempting exhaustive coverage.

## Advanced Modes

### Depth Modes (Concise / Standard / Deep)
The skill adapts based on content, but users can explicitly request a depth mode:

- **Concise mode**: Use for short talks or when a high-level overview is sufficient. Reduce number of themes, keep Main Ideas & Frameworks and Core Mental Models sections brief, and limit quotes and key moments.
- **Standard mode** (default): Balanced depth appropriate for most conference talks and training sessions.
- **Deep mode**: Use for long-form training, dense technical content, or when maximum synthesis and insight extraction is desired. Expand synthesis in Core Mental Models & Perspective Shifts, increase focus on interconnections, and allow more detailed treatment of frameworks and implications.

Request by saying e.g. "content-intelligence in deep mode" or "concise summary using content-intelligence".

### Structured Data / JSON Export
When the user requests "structured data", "JSON mode", "machine readable", or similar:
1. First output the complete Markdown summary using the structure above.
2. Then append a clean JSON block containing structured fields such as:
   - title, speaker(s), date/event
   - key_themes (array)
   - main_ideas_frameworks (array)
   - core_mental_models (array)
   - insights_takeaways (array)
   - practical_implications (array)
   - memorable_quotes (array)
   - open_questions (array)
   - resources (array)
   - key_moments (array)

This enables easy ingestion into note-taking systems, personal knowledge bases, or AI workflows.

### Long-Form Content Handling
For extended presentations or training sessions:
- Process using logical topic sections internally.
- Emphasize synthesis of cross-cutting themes, mental models, and high-leverage insights.
- Use the "Core Mental Models & Perspective Shifts" and "Main Ideas & Frameworks" sections more heavily.
- Keep the final summary focused and digestible rather than excessively long, even in Deep mode.

## Document Generation

After generating the complete Markdown summary using the exact structure defined above, automatically call the `docx` skill to create a professionally formatted Word document (.docx) version of the summary.

- Use proper heading styles (Heading 1 for main title, Heading 2 for sections, Heading 3 for subsections).
- Preserve bold text, bullet lists, and other Markdown formatting.
- Apply clean, professional formatting suitable for knowledge capture and sharing.
- Generate a meaningful filename based on the topic and date (e.g., "Content_Summary_[Topic]_[Date].docx").
- The Markdown summary remains the primary output. The Word document is generated as an additional deliverable.

Only skip document generation if the user explicitly requests "Markdown only" or "no document".

This skill produces high-quality, insight-rich summaries optimized for learning, synthesis, and knowledge capture from informational content.
