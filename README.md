# Adversarial Attacks on Deep learning Models

This is a graduation project focused on analyzing vulnerabilities in Arabic transformer models used for hate speech and offensive content detection.

## Summary

The work evaluates how Arabic transformer classifiers respond to adversarial text perturbations. It shows that even high-performing models can be deceived by carefully targeted modifications, exposing key weaknesses in Arabic NLP systems before real-world deployment.

## Motivation

- Arabic NLP is underrepresented compared to English, especially for hate speech detection.
- Transformer models are widely used in Arabic text classification, but their robustness against adversarial attacks is not well studied.
- This project demonstrates real attack techniques and measures their impact on model decisions.

## What Was Done

### Model building

- Fine-tuned an Arabic transformer model based on `aubmindlab/bert-base-arabertv2`.
- Built a custom PyTorch classification head on top of AraBERT.
- Prepared and evaluated dataset splits from Arabic text sources, including hate speech and review datasets.

### Adversarial attack design

- Developed an importance ranking method called **R1S** to identify influential tokens in correctly classified examples.
- Used **CAMeL Tools** for Arabic morphology, token reconstruction, and valid word modification.
- Created adversarial examples with:
  - morphological changes (gender, number, definiteness)
  - token flip attacks on single tokens (`ArFlip1`)
  - token flip attacks on pairs of tokens (`ArFlip2`)

### Evaluation and analysis

- Measured attack success by comparing clean predictions to modified sentence predictions.
- Tracked misclassified examples, skipped sentences, and accuracy drop after attacks.
- Evaluated performance on hate speech data from the OSACT5 corpus.

## Results and Findings

- The attacks significantly degraded model robustness: many original correct answers became incorrect after adversarial modification.
- Single-token and two-token flip attacks were effective at breaking classification for targeted examples.
- Morphological and token-level perturbations were particularly effective in Arabic, due to the language’s rich morphology and tokenization behavior.
- The experiments highlight that model accuracy on clean examples does not guarantee robustness against adversarial input.

## Key Insights

- Arabic transformer models are vulnerable to targeted adversarial attacks even when prediction accuracy is high.
- Importance-based token selection is a strong lever for attack success: changing the most influential token yields larger degradation than random modification.
- Adversarial examples can be constructed using linguistically meaningful transformations, not just random noise.
- Models trained on social-media-like Arabic text show better resilience, but still remain vulnerable.

## Conclusion

This project demonstrates that Arabic hate speech classifiers can be undermined by token-level and morphological adversarial attacks. The work underscores the need for robustness-aware evaluation and stronger defenses in Arabic NLP systems.

## Notebook

The primary implementation is in `Graduation_Project.ipynb`, which contains the full training, attack generation, and analysis workflow.

For full project documentation, see `Final Thesis.pdf`.
