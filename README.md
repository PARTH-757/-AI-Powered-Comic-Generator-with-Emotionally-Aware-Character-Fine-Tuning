# AI-Powered Comic Generator with Emotionally-Aware Character Fine-Tuning

## Introduction  
Comics are a powerful medium to visually narrate stories. This project presents an automated comic generation system designed specifically for Hindi short stories. Leveraging cutting-edge NLP and image generation technologies, it extracts characters, understands scenes, detects emotions, and generates consistent, expressive comic panels using LoRA-fine-tuned Stable Diffusion models. Each character is trained with multiple emotional states to enable expressive storytelling through AI-generated visuals.

---

## Abstract  
This project introduces a complete pipeline for converting narrative Hindi texts into emotionally expressive comic panels. Using advanced NLP techniques, the system identifies characters, scenes, dialogues, and associated emotions. A key innovation lies in the **LoRA (Low-Rank Adaptation) fine-tuning** of a Stable Diffusion model — where each character is trained with five emotional variants (happy, sad, afraid, angry, neutral) to maintain **character and emotion consistency** across generated panels. The system also ensures **location consistency**, preserving each character's spatial position (e.g., ram is in forest) across all related scenes. This approach offers a robust foundation for AI-driven storytelling, with potential applications in education, entertainment, and content localization.

---

## Architecture & Methodology  

### System Components  

1. **Text Processing & Character Extraction**  
   - Parses Hindi short stories to extract named characters.  
   - Segments the story into structured scenes.  
   - Detects dialogues and character positions (e.g., sitting, standing).  

2. **Emotion Detection & Scene Analysis**  
   - Uses keyword-based heuristics to infer emotions and actions.  
   - Supports six emotional states: `happy`, `sad`, `angry`, `fear`, `neutral`, `smile`.  
   - Captures spatial arrangement for location consistency.  

3. **Prompt Construction Module**  
   - Constructs image generation prompts combining character name, emotion, and pose, e.g.,  
     `"a sad Meera standing near a tree in Indian comic style"`.  
   - Reuses spatial context for visual consistency across panels.  

4. **Image Generator with LoRA Fine-Tuning**  
   - Utilizes `Stable Diffusion v2.1`, fine-tuned using LoRA per character.  
   - Each character’s training data is organized into emotion-specific subfolders.  
   - Fine-tuned using tagged prompts for emotional and positional alignment.  
   - LoRA applied to attention modules (`to_q`, `to_k`, `to_v`, `to_out.0`).  

5. **Location Consistency Mechanism**  
   - Stores each character’s position in the scene metadata.  
   - Propagates this information in future prompts to ensure consistent layout.  
   - Enhances readability and maintains narrative clarity.

6. **Comic Panel Assembly**  
   - Auto-generates comic panels with consistent character representation.  
   - Arranges them sequentially by story flow.  
   - Embeds extracted dialogues into the panels using comic-style text formatting.  

---

## Implementation Details  

- **Language:** Python  
- **Model:** Stable Diffusion v2.1 with LoRA  
- **Fine-Tuning Frameworks:** PEFT (LoRA), Diffusers, Transformers  
- **Training Dataset:** Manually curated emotion-specific character images in comic style  
- **LoRA Fine-Tuning Configuration:**  
  - Applied to transformer attention projections  
  - Batch size: 1  
  - Epochs: 10  
  - Emotion-conditioned training prompts  
- **Emotion Detection:** Heuristic-based rule engine over scene text  
- **Location Consistency:** Managed via extracted scene descriptors, reused across prompt generations  
- **Frontend:** Automatically assembled comic pages with scene-wise image generation and dialogue embedding  

---

## Highlights  

- 🎭 Emotion-aware, LoRA-fine-tuned character generation  
- 📚 End-to-end automation from Hindi story to comic  
- 📍 Location consistency across all scenes  
- 🎨 Indian comic art styling for visual familiarity  
- 🚀 Efficient generation using Stable Diffusion on CPU/GPU  

---

