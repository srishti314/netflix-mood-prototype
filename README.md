Product Strategy Brief
Mood-Aware Promotional Asset Intelligence for Netflix Content Operations
Prepared by Srishti Gupta prompt engineered with Claude | February 2026 | Work Sample for CPOP AI Product Manager Role
Executive Summary
Netflix already personalizes which titles members see. The next frontier is personalizing how those titles are
presented based on a member's emotional context. Today, Netflix serves different artwork per user, but the creative
asset selection is driven primarily by historical preference patterns. It does not adapt to a member's current mood or
situational context (late-night wind-down vs. Saturday morning energy vs. post-breakup comfort seeking).
This brief proposes a Mood-Aware Promotional Asset Intelligence system: an AI-powered internal platform tool
that (1) automatically tags the emotional tone of every promotional asset in the catalog, (2) infers member emotional
context from behavioral signals, and (3) matches asset presentation to mood in real time. The product sits within the
CPOP publishing pipeline, empowering creative teams with emotional analytics and giving the personalization engine
a richer asset vocabulary to draw from.
Problem
Netflix's promotional assets (thumbnails, trailers, synopses, banners) are the bridge between a title and a member's
decision to watch. The current personalization system selects assets based on who a member is. It does not adapt to
how a member feels right now. This creates several missed opportunities:
•
Same emotional register regardless of context: A member browsing at 9pm after a stressful day sees the
same asset framing as when they browse on a relaxed Sunday afternoon. The title might be right, but the
emotional pitch of the promotional creative may not match the moment.
•
Creative teams lack emotional performance data: Content creators, editors, and artwork teams produce asset
suites for each title but have limited visibility into which emotional angles resonate with which audience segments
in which contexts. Asset creation is guided by intuition and broad A/B results, not granular emotional intelligence.
•
Promotional asset tagging is manual and inconsistent: Emotional tone metadata for artwork, trailers, and
synopses is either missing or applied manually by individual editors with varying taxonomies. This limits the
personalization engine's ability to select assets along emotional dimensions.
•
Localized assets amplify the gap: When promotional assets are localized across 30+ languages, emotional
tone can shift in translation. Without systematic emotional tagging, there is no scalable way to verify that localized
assets preserve the intended emotional register.
Proposed Solution
Build a three-layer AI system that sits within the CPOP content platform, creating a new capability for how promotional
assets are tagged, selected, and optimized:
Layer 1: Emotional Tone Tagging Engine (Content Side)
Use multimodal ML models to automatically classify the emotional tone of every promotional asset in the catalog. For
artwork: analyze color palette, facial expressions, composition, and scene content to assign emotional vectors (e.g.,
tension, warmth, nostalgia, excitement, melancholy). For trailers and previews: combine video understanding models
with audio sentiment analysis to classify emotional arc and dominant mood. For synopses and promotional copy: use
fine-tuned LLMs to classify emotional register and framing angle (character-driven warmth vs. plot-driven suspense
vs. thematic gravitas). This runs at ingest time within the publishing pipeline, creating a structured emotional metadata
layer across the entire asset catalog.
Layer 2: Member Mood Inference (Demand Side)
Infer a member's current emotional context from behavioral signals that Netflix already collects, without requiring any
explicit input from the member. Signals include: time of day and day of week, device type (TV lean-back vs. mobile
commute), recent viewing history within the session (just finished a heavy drama vs. light comedy), browse velocity
(rapid scrolling signals different intent than slow deliberate browsing), and rewatch behavior (comfort-seeking signal).
The model outputs a probabilistic mood vector, not a single label, allowing for nuanced matching.
Layer 3: Mood-Asset Matching and Creative Intelligence Dashboard
Match the member's inferred mood vector to the emotional tone vectors of available promotional assets for each title
in their feed, selecting the asset framing most likely to resonate in the moment. Simultaneously, surface aggregated
insights to creative teams via an internal dashboard: which emotional angles are driving engagement for which
audience segments, how localized versions of an asset compare on emotional alignment, and which titles have asset
suites with emotional gaps (e.g., no warm/nostalgic variant for a title that performs well in late-night sessions).
Why This Belongs in CPOP
This is a content operations and publishing product, not a consumer recommendation product. The primary
deliverables are:
•
An automated tagging capability that enriches the promotional asset pipeline with emotional metadata at scale
(content operations infrastructure)
•
An internal creative intelligence tool that empowers artists, editors, and content executives with data on
emotional performance (internal tool for creative teams)
•
A richer asset vocabulary that the existing personalization engine can consume to improve asset selection
(platform capability that integrates with downstream systems)
•
Localization quality signal that flags when translated/dubbed assets drift from the source asset's emotional
tone (content QA for globalization)
The CPOP team's mission is to develop innovative approaches to how Netflix promotes, localizes, and distributes
content. Mood-aware asset intelligence directly extends each of these three pillars.
System Design
Component Input ML Approach Output
Image Emotion
Tagger
Artwork files
(thumbnails, banners)
Vision model (fine-tuned on Netflix
asset corpus) classifying emotional
dimensions
Emotional vector per image asset
Video Emotion
Tagger
Trailers, previews,
sizzles
Multimodal model: video
understanding + audio sentiment +
scene classification
Emotional arc + dominant mood per video
asset
Text Emotion
Tagger
Synopses, promo
copy (all languages)
Fine-tuned multilingual LLM for
emotional register classification
Emotional vector per text asset +
cross-language drift score
Mood Inference
Model
Session-level
behavioral signals
Contextual bandit / lightweight
sequence model on implicit signals
Probabilistic mood vector per active session
Asset Matcher Mood vector + asset
emotional vectors
Nearest-neighbor matching with
exploration/exploitation balancing
Ranked asset selection per title per session
Creative
Dashboard
Aggregated matching
+ engagement data
Analytics + clustering for
segment-level emotional patterns
Insights: emotional gaps, segment preferences,
localization drift
Validation Plan
Phased, hypothesis-driven approach with clear go/no-go criteria at each stage:
Phase 1: Emotional Tagging Accuracy (6 weeks)
•
Build emotional tagging models for artwork and synopses using Netflix's existing asset corpus
•
Validate against human expert labels from a panel of creative team members
•
Hypothesis: Automated tags achieve 80%+ agreement with human expert labels on a held-out set
•
Go/no-go: If agreement < 70%, refine taxonomy and retrain before proceeding
Phase 2: Mood-Asset Matching Lift (10 weeks)
•
A/B test mood-aware asset selection against current personalization for a subset of titles and markets
•
Hypothesis: Mood-matched assets increase click-through rate by 5%+ and title-start rate by 3%+
•
Secondary metric: Session depth (do members browse less and watch more when assets match mood?)
•
Go/no-go: Statistically significant lift on primary metric within 6 weeks of test launch
Phase 3: Creative Intelligence Dashboard (8 weeks, parallel with Phase 2)
•
•
•
Ship dashboard MVP to a pilot group of creative leads and content executives
Hypothesis: Creative teams use emotional gap data to inform at least 30% of new asset briefs
Measure: Dashboard adoption, asset suite diversity scores, qualitative feedback from creative leads
Metric Target Why It Matters
Emotional tag accuracy 80%+ human agreement Foundation for all downstream value
Click-through rate lift +5% in A/B test Direct member engagement impact
Title-start rate lift +3% in A/B test Conversion from browse to watch
Creative dashboard adoption 70%+ weekly active use in
pilot
Tool value for internal creative teams
Localization emotional drift
detection
Flag 90%+ of tone-shifted
assets
Cross-market experience consistency
Key Risks and Mitigations
•
•
•
•
Mood inference feels invasive: The system uses only behavioral signals Netflix already collects (time, device,
viewing patterns). No biometric, facial, or external data. Mood is inferred probabilistically, not labeled. Members
never see a "mood" label. The experience simply feels more attuned.
Emotional taxonomy is subjective: Start with a small, validated taxonomy (6-8 dimensions) developed with
creative team input. Use continuous vectors rather than hard categories to allow nuance. Iterate taxonomy based
on what actually predicts engagement.
Attribution is complex: Isolating the impact of mood-matched assets from other personalization factors requires
careful A/B test design. Use title-level randomization within the same recommendation slate to control for title
selection effects.
Creative team adoption: If the dashboard is not intuitive or the insights feel abstract, adoption will stall.
Co-design with creative leads from day one. Ship a minimal version early and iterate based on how they actually
use it.
Why This Problem Resonates With Me
This product requires three capabilities that map directly to my background. First, incubating ML-powered products
from research to production: at Medidata, I shipped a fine-tuned LLM that reduced clinical study setup time by 80%
and drove 0-to-1 development of an LLM-powered analytics system using RAG and prompt engineering. I have
hands-on experience with the ML lifecycle from data collection through model evaluation to production deployment.
Second, building intelligent internal tools for domain expert users: the creative intelligence dashboard for content
teams is structurally the same challenge as the analytics tools I built for clinical researchers and data managers. I
know how to translate complex model outputs into actionable interfaces that experts trust. Third, partnering with
applied researchers and data scientists to translate AI capabilities into scalable products: at Medidata I
coordinated across data science, engineering, and UX to ship products that balanced technical sophistication with
user-centric design, and at BlackRock I built production ML models with interpretability frameworks that
decision-makers relied on.
Netflix's mission to entertain the world depends on making every member feel like the platform was built just for them.
Mood-aware promotional asset intelligence is a step toward that: not just showing the right title, but presenting it in the
right emotional light at the right moment. I would be excited to bring this from concept to production within the CPOP
team.
