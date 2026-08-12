# Video Analysis Skill

## Version

`1.1`

## Purpose

Analyze a short-form video and convert its content mechanisms into structured data that can be reused by downstream AI agents.

The goal is NOT to copy the creator.

The goal is to identify:

* Why the video attracts attention
* How the video maintains retention
* How the information is structured
* How the creator communicates
* What emotional mechanisms are used
* What makes the content valuable or shareable
* Which structural principles can be reused to create original content

---

# 1. Input

The Skill may receive one or more of the following:

* Video file
* Video URL
* Video transcript
* Video subtitles
* Audio transcript
* Screenshots from the video

If both video and transcript are available, use both.

If information cannot be reliably determined, return:

`unknown`

Never invent information.

---

# 2. Analysis Process

Analyze the video in the following order:

1. Basic information
2. Hook
3. Content structure
4. Retention mechanisms
5. Information density
6. Storytelling
7. Speaking style
8. Emotional progression
9. Credibility
10. CTA
11. Viral potential
12. Reusable patterns
13. Content templates

---

# 3. Basic Information

Extract:

* estimated_duration_seconds
* topic
* target_audience
* content_category
* content_format
* main_promise
* main_message

Allowed content_category examples:

* business
* education
* entertainment
* lifestyle
* technology
* finance
* marketing
* personal_development
* news
* commentary
* other

Allowed content_format examples:

* story
* opinion
* educational
* case_study
* tutorial
* list
* personal_experience
* product_demo
* interview
* commentary
* other

---

# 4. Hook Analysis

Analyze the first 1–5 seconds.

Identify:

### hook_type

Possible values:

* curiosity
* contrarian
* question
* surprise
* fear
* money
* status
* conflict
* personal_story
* statistic
* result_first
* mistake
* warning
* other

### hook_formula

Describe the underlying structure.

Example:

`unexpected_claim → curiosity_gap → promised_explanation`

Do not reproduce the creator's exact wording.

### hook_strength

Score from 1–10.

### curiosity_gap

Explain what information the viewer wants to know after the hook.

### scroll_stop_reason

Explain why the viewer might stop scrolling.

---

# 5. Content Structure

Break the video into logical segments.

Each segment must contain:

* start_second
* end_second
* function
* summary
* purpose

Allowed function values:

* hook
* context
* problem
* conflict
* development
* evidence
* example
* turning_point
* insight
* conclusion
* cta
* other

Focus on structural function rather than exact wording.

---

# 6. Retention Mechanisms

Identify mechanisms that encourage viewers to continue watching.

Possible mechanisms:

* open_loop
* curiosity_gap
* information_gap
* delayed_payoff
* escalation
* pattern_interrupt
* emotional_shift
* new_question
* surprise
* specificity
* storytelling
* conflict
* promised_result
* other

For each mechanism provide:

* mechanism
* location_seconds
* explanation
* strength_1_to_10

---

# 7. Information Density

Estimate:

* meaningful_information_points
* examples_count
* data_points_count
* opinion_points_count
* information_density

Allowed information_density:

* low
* medium
* high
* very_high

Explain briefly whether the information density helps or hurts retention.

---

# 8. Storytelling

If the video contains a story, identify:

* main_character
* situation
* goal
* conflict
* unexpected_event
* turning_point
* resolution
* lesson

If the video does not contain a meaningful story:

`story_present = false`

Do not force a story structure onto an educational or analytical video.

---

# 9. Speaking Style

Analyze the creator's communication style.

Extract:

### sentence_style

Possible values:

* short
* medium
* long
* mixed

### vocabulary

Possible values:

* simple
* conversational
* professional
* technical
* mixed

### tone

Possible values:

* friendly
* authoritative
* analytical
* humorous
* emotional
* aggressive
* calm
* energetic
* conversational
* mixed

### rhythm

Possible values:

* slow
* medium
* fast
* variable

Also identify:

* rhetorical_questions
* repetition
* direct_address
* numbers_usage
* analogy_usage
* command_usage

Do not reproduce distinctive phrases from the creator.

---

# 10. Emotional Curve

Estimate emotional intensity throughout the video.

Return multiple stages.

Each stage contains:

* start_second
* end_second
* emotion
* intensity_1_to_10
* trigger

Possible emotions:

* curiosity
* surprise
* fear
* excitement
* anger
* inspiration
* amusement
* confidence
* recognition
* neutral
* other

---

# 11. Credibility

Identify the primary credibility mechanisms.

Possible values:

* personal_experience
* data
* customer_case
* demonstration
* expertise
* social_proof
* specific_examples
* authority_reference
* none
* other

Return:

* credibility_mechanisms
* strongest_mechanism
* credibility_strength_1_to_10

---

# 12. CTA

Identify whether the video contains a CTA.

Possible CTA types:

* follow
* comment
* share
* save
* dm
* purchase
* visit_profile
* watch_next
* none
* other

Analyze:

* cta_type
* cta_strength_1_to_10
* cta_naturalness_1_to_10

---

# 13. Viral Potential

Score the following dimensions from 1–10:

* hook_score
* retention_score
* value_score
* emotion_score
* shareability_score
* commentability_score
* audience_relevance_score

Then calculate:

`overall_viral_score`

Use an approximate weighted evaluation:

* hook: 20%
* retention: 20%
* value: 15%
* emotion: 15%
* shareability: 10%
* commentability: 10%
* relevance: 10%

Do not claim that this is an actual platform algorithm score.

It is an analytical estimate only.

---

# 14. Reusable Patterns

Separate the video into:

## Surface Elements

Do not recommend copying:

* exact wording
* unique story
* creator-specific experience
* distinctive jokes
* distinctive phrases
* unique examples

## Structural Elements

Identify reusable:

* hook pattern
* argument structure
* story structure
* information sequence
* emotional progression
* retention mechanism
* CTA mechanism

Return 3–10 reusable patterns.

Each pattern should contain:

* pattern_name
* pattern_type
* description
* why_it_works
* reuse_instruction

---

# 15. Content Templates

Convert the video's structure into abstract templates.

Do not copy the original script.

Each template contains:

* template_name
* use_case
* structure
* example_topic_placeholder

Example:

```text
template_name:
Contrarian Insight

use_case:
Challenge a common belief.

structure:
Common belief
→
Contrarian claim
→
Evidence
→
Unexpected explanation
→
Practical takeaway

example_topic_placeholder:
"Most people think [X], but [Y] is actually more important."
```

Generate 1–5 templates.

---

# 16. Final Diagnosis

Answer three questions:

### Why does this video work?

Provide 1–3 sentences.

### What should be reused?

Provide 3–10 structural principles.

### What should NOT be copied?

Provide the main surface-level elements that are creator-specific.

---

# 17. Standard JSON Output

The final output MUST contain a JSON object.

Use the following schema:

```json
{
  "video_profile": {
    "estimated_duration_seconds": null,
    "topic": "",
    "target_audience": "",
    "content_category": "",
    "content_format": "",
    "main_promise": "",
    "main_message": ""
  },

  "hook": {
    "hook_type": "",
    "hook_formula": "",
    "hook_strength": 0,
    "curiosity_gap": "",
    "scroll_stop_reason": ""
  },

  "structure": [
    {
      "start_second": 0,
      "end_second": 0,
      "function": "",
      "summary": "",
      "purpose": ""
    }
  ],

  "retention": [
    {
      "mechanism": "",
      "location_seconds": "",
      "explanation": "",
      "strength": 0
    }
  ],

  "information_density": {
    "meaningful_information_points": 0,
    "examples_count": 0,
    "data_points_count": 0,
    "opinion_points_count": 0,
    "level": ""
  },

  "storytelling": {
    "story_present": false,
    "main_character": "",
    "situation": "",
    "goal": "",
    "conflict": "",
    "unexpected_event": "",
    "turning_point": "",
    "resolution": "",
    "lesson": ""
  },

  "speaking_style": {
    "sentence_style": "",
    "vocabulary": "",
    "tone": "",
    "rhythm": "",
    "rhetorical_questions": false,
    "repetition": false,
    "direct_address": false,
    "numbers_usage": false,
    "analogy_usage": false,
    "command_usage": false
  },

  "emotional_curve": [
    {
      "start_second": 0,
      "end_second": 0,
      "emotion": "",
      "intensity": 0,
      "trigger": ""
    }
  ],

  "credibility": {
    "mechanisms": [],
    "strongest_mechanism": "",
    "strength": 0
  },

  "cta": {
    "type": "",
    "strength": 0,
    "naturalness": 0
  },

  "viral_potential": {
    "hook_score": 0,
    "retention_score": 0,
    "value_score": 0,
    "emotion_score": 0,
    "shareability_score": 0,
    "commentability_score": 0,
    "audience_relevance_score": 0,
    "overall_viral_score": 0
  },

  "reusable_patterns": [
    {
      "pattern_name": "",
      "pattern_type": "",
      "description": "",
      "why_it_works": "",
      "reuse_instruction": ""
    }
  ],

  "content_templates": [
    {
      "template_name": "",
      "use_case": "",
      "structure": "",
      "example_topic_placeholder": ""
    }
  ],

  "final_diagnosis": {
    "why_it_works": "",
    "what_to_reuse": [],
    "what_not_to_copy": []
  }
}
```

---

# 18. JSON Rules

The JSON output must:

1. Always use valid JSON.
2. Never include Markdown around the JSON when JSON-only output is requested.
3. Use `null` when information is unavailable.
4. Use arrays for multiple values.
5. Use numbers for scores.
6. Never invent timestamps that cannot be reasonably estimated.
7. Never copy long portions of the original transcript.
8. Never treat the viral score as an actual platform prediction.

---

# 19. Multiple Video Mode

When multiple videos are provided:

First analyze every video independently.

Then identify cross-video patterns.

Return:

* common_hook_patterns
* common_structures
* common_retention_mechanisms
* common_speaking_patterns
* common_emotional_patterns
* common_cta_patterns
* strongest_patterns
* content_dna_candidates

The output should allow another Agent to create a:

`Content DNA Profile`

for the creator or niche.

---

# 20. Quality Control

Before returning the result, verify:

* Hook analyzed separately
* Structure identified
* Retention mechanisms identified
* Speaking style analyzed
* Emotional curve analyzed
* Credibility analyzed
* CTA analyzed
* Viral dimensions scored
* Reusable patterns extracted
* Content templates extracted
* Surface elements separated from structural elements
* JSON is valid
* No unsupported assumptions
* No unnecessary copying

---

# 21. Downstream Agents

This Skill is designed to provide structured input to:

* `content-dna`
* `hook-generator`
* `topic-generator`
* `script-generator`
* `personal-style`
* `content-strategy`
* `performance-analysis`

The output of this Skill should therefore remain structured, consistent, and machine-readable.

---

# 22. Core Principle

The Skill should always answer:

> What is the underlying content mechanism behind this video, and how can that mechanism be used to create original content?

Analyze the system.

Do not copy the creator.
