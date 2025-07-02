The task is to develop an automated framework using LLMs to generate, evaluate, and analyze domain names tailored for diverse business descriptions. This helps simulate a real-world LLM product pipeline, covering generation, evaluation, error handling, and visualization.

Phase 1: Domain Generation
LLM Used: gpt-4 via LangChain + OpenAI integration.

Prompt: A PromptTemplate was designed to generate 3 creative domain names for each business.

Input: 122 synthetic business descriptions (generated via another LLM prompt).

Safety Filtering: Businesses containing unsafe or inappropriate content (e.g., adult, gambling, drugs) were skipped.

✅ Output: domain_name_dataset.json — containing generated domains with metadata and statuses (success, blocked, error).

Phase 2: Domain Evaluation
LLM Role: Acted as a domain judge using a structured prompt with scoring criteria:

Relevance

Readability

Brandability

Appropriateness

Output Format: Structured JSON with score (float between 0–1) and a brief reason.

Edge Handling:

Invalid JSON responses were parsed and cleaned using regex and key quotation fixes.

Entries with score: null were automatically retried using the same prompt.

✅ Output:

evaluated_results.json — initial raw scores and errors.

final_evaluation_results.json — fixed and cleaned version after retries.

Phase 3: Analysis & Visualization
✅ Summary Metrics
Total Domains Evaluated: All successfully generated domain names.

Failures (Post-Retry): 0 — All domains were successfully evaluated after error correction.

📊 Visualizations
Histogram showing distribution of domain scores — indicating most fall in the 0.8–0.95 range.

Top 10 Domains:

gentlemenscouture.com (1.0) – high-quality men’s suits

prepforsuccess.com (1.0) – tutoring agency

TechEaseSolutions.com (0.95) – tech company

RecycleRevolution.com (0.95) – recycling company

...and others showcasing diverse industries.

Observations
Domains with clear semantic relevance and simplicity consistently scored higher.

Common failure patterns:

LLM outputs missing JSON format.

Descriptive over-explanation beyond prompt instruction.

Fix strategy:

Applied regex to isolate JSON.

Normalized keys and quote types.

Retried failures with consistent formatting.

🔹 Optional Phases (Skipped / Not Implemented)
Fine-tuning or Custom Model Training: Not executed due to time constraints and absence of structured prompt-completion pairs (prompt column missing).

API Deployment or UI Interface: Out of scope for this task.

Custom Model Evaluation: LLM was used as both generator and judge — classical benchmark or human comparison not done.

✅ Final Output Files
File Name	Description
domain_name_dataset.json	Raw generated domains per business description
evaluated_results.json	Initial evaluation scores
final_evaluation_results.json	Cleaned scores with all errors handled
Assignment.ipynb	Full source code for generation and evaluation
Score Histogram & Top 10 Table	Used in visual and tabular summary

Conclusion
The system successfully implements an automated pipeline for domain name generation and evaluation using GPT-4. It includes robust error handling and insightful visualization to aid business decision-making. While fine-tuning was out of scope, the experiment validates how LLMs can assist in creative ideation tasks at scale.

