# Context Renormalization
A Bounded-Memory Protocol for Multi-Session LLM Work

Context Renormalization is a simple, model-agnostic protocol for maintaining continuity across multiple LLM sessions. Instead of relying on long, slow conversations or re-explaining project history, the method uses a small text file (context.txt) as a bounded knowledge ledger. Each LLM session adds new durable knowledge and rewrites the ledger back down to a fixed size budget.

This repository contains:
- The research paper in PDF form
- A minimal example context.txt
- Illustrations explaining the workflow
- Optional starter templates for your own projects

---

## Why Context Renormalization?
Working with LLMs over long periods exposes a practical failure mode:
- Browser chat UIs slow down as the DOM tree grows.
- Context windows get filled with redundant history.
- Users restart the chat, losing continuity.
- Knowledge must be manually re-fed into the model.

Context Renormalization solves this by:
1. Storing all durable knowledge in a small file.
2. Using a strict immutable header to define update rules.
3. Rewriting and compressing the knowledge region at every session boundary.
4. Keeping the project state portable across models, vendors, and time.

The ledger acts as a "bounded working memory" shared between you and any future LLM instance.

---

## Repository Structure

- paper/
  - context_renormalization.pdf
- examples/
  - sample_context.txt
- images/
  - workflow_diagram.png
  - profile_icon.png
- templates/
  - empty_context_template.txt

---

## How It Works (Short Version)

1. You maintain a file called context.txt.
2. The top block is the immutable Control Header.
3. Below it is the Knowledge Region, which the LLM is allowed to rewrite.
4. At the end of each LLM session, you say:
   "End of session. Update context according to the control header protocol."
5. The LLM:
   - Increments the session counter.
   - Adds a new session summary.
   - Compresses older sessions to fit a fixed character budget.
   - Computes a Compression Difficulty Score (CDS).
6. The resulting file becomes the starting point for the next session.

This procedure is recursive and deterministic: same input, same output.

---

## Metalanguage (Future Work)

The paper proposes creating a formal metalanguage for:
- Header grammar and invariants
- Safety constraints
- Verification of compression steps
- Cross-vendor interoperability

This would make Context Renormalization a standardized continuity protocol for LLM systems.

---

## Suggested Tags for GitHub

context-renormalization  
bounded-memory  
llm-continuity  
multi-session-llm  
recursive-summarization  
knowledge-ledger  
compression-protocol  
model-agnostic  
ai-research  
human-ai-collaboration  

---

## Citation

If you reference this work, please cite:

Vasili Gavrilov and ChatGPT 5.1  
"Context Renormalization: A Bounded-Memory Protocol for Multi-Session LLM Work."  
2025.

---

## License

You may choose one of the following depending on your preference:
- MIT License (recommended for maximum reuse)
- CC-BY 4.0 (recommended for academic credit)
- Apache 2.0 (recommended when contributions are expected)

Add the license as a LICENSE file at the repository root.

---

## Contact

For discussion, feedback, or contributions:
- GitHub Issues
- https://www.facebook.com/profile.php?id=61585168733135


