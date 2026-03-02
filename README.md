# Vezstral: The Bolognese AI

**Vezstral is a fine-tuned Ministral 3B model that talks, thinks, and advises like a true local "vez" (friend) from Bologna, Italy.**

Built for the **Mistral AI Worldwide Hackathon 2026 - Online Edition**, Vezstral demonstrates how powerful Foundation Models can be localized to preserve regional linguistics, cultural nuances, and community identity.

---

## Demo

See Vezstral in action!

[vezstral-screencast-demo](https://github.com/user-attachments/assets/ab921ad4-2f78-42e8-aad8-d1ffb10587cc)






---

## The Vision: AI as a Neighbor

Who said Artificial Intelligence has to be culturally sterile, hyper-polite, and strictly English-first?

As LLMs become ubiquitous, there is a risk of cultural homogenization. We built Vezstral to prove that an AI can have a sharp, highly localized identity. Think of Vezstral not as a corporate assistant, but as your compatriot — a local companion who views the world from a perspective you deeply understand.

Imagine a world where your AI companion speaks Parisian _Verlan_, London _Cockney_, or Liverpool _Scouse_. Expanding this concept to other regions wouldn't just be incredibly cool and genuinely useful for cultural preservation—it would also make interacting with AI feel much more personal, human, and just plain pleasant.

Bologna has a vibrant, sharp cultural identity with a rich linguistic tapestry. Its local language is a mix of traditional _dialetto bolognese_, timeless regional expressions, and modern youth-driven street slang. Vezstral captures this unique spirit.

### Why is this useful?

Beyond being super fun, a hyper-local AI has genuine utility:

- **Cultural Preservation:** Documenting and keeping alive regional dialects and street slang in the age of digital globalization.
- **Authentic Tourism:** Instead of generic "Top 10" lists, you get recommendations for osterias and hidden spots from a model that speaks the local language and understands the city's vibe.
- **Immersive Language Learning:** Instead of boring textbook exercises, learners can interact with a local "penpal" to learn how real people actually speak on the streets of Bologna.

---

## How It Was Built (The Architecture)

This project uses a **Teacher-Student Synthetic Data Distillation** pipeline, powered entirely by the Mistral ecosystem.

1. **The Teacher (Mistral Large 3):** We used Mistral Large 3 to generate a highly specialized synthetic dataset of multi-turn conversations. We prompted the model to act as various Bolognese personas, generating rich JSONL data encompassing casual chats, tourism advice, and slang explanations.
2. **The Student (Ministral 3B):**
   We took the lightweight, edge-ready `mistralai/Ministral-3-3B-Instruct-2512` model and fine-tuned it using the synthetic dataset.

3. **Fine-Tuning (QLoRA):**
   - **Method:** Parameter-Efficient Fine-Tuning (PEFT) using QLoRA.
   - **Quantization:** 4-bit NormalFloat (NF4) for extreme memory efficiency.
   - **Rank (r) & Alpha:** r=16, Alpha=32 targeting Attention projections (`q_proj`, `k_proj`, `v_proj`, `o_proj`).
   - **Hardware:** Trained seamlessly on a single free-tier Google Colab NVIDIA T4 GPU in under an hour.

---

## A Crash Course in Bolognese Slang

Curious about what Vezstral learned? Here is a taste of the linguistic variety injected into the model:

- **"Vez"** - _Friend / Mate / Bro_ (The inspiration for the model's name!).
- **"Soccia!" / "Sorbole!"** - _Wow! / Damn!_ (Universal expressions of surprise or emphasis).
- **"Stare in polleg"** - _To be completely relaxed / chilling._
- **"Pilla"** - _Money._
- **"Fare balotta"** - _Hanging out and having a good time with a group of people._

---

## Repository Structure

- `/notebooks/1_vezstral_teacher.ipynb`: The data generation pipeline using Mistral APIs.
- `/notebooks/2_vezstral_finetuning.ipynb`: The QLoRA training script.
- `/notebooks/3_vezstral_inference.ipynb`: The inference and Web UI script.
- `/data/training_data.jsonl`: The synthetic training dataset.
- `/media/veztral-demo.mp4`: Demonstration video of the model.

_(Note: The fine-tuned LoRA adapter weights are hosted publicly on Hugging Face)._

---

## License

This project is open-source and available under the [MIT License](LICENSE).

---

## Contact

Created by **Nikolai Gorbachev** for the Mistral AI Worldwide Hackathon 2026 - Online Edition.

-
