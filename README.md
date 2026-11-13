# Phase 2–7 Notebooks: Shared Inputs

Phases 2 through 7 are fine-tuning phases. Each one starts from the same base model, `decoder_baseline_v7_final_model.pt`, and fine-tunes it further. The model and related input files are stored in a public Kaggle dataset so every phase notebook loads the same starting point.

**Dataset:** https://www.kaggle.com/datasets/triggerboe2/phase2-inputs

## Key File

| File | Role |
|------|------|
| `decoder_baseline_v7_final_model.pt` | **Base model.** Foundation for Phases 2–7. Do not modify or overwrite it. |

## Model Versions

Each version uses a different model class and checkpoint. Set `build_model()` and `MODEL_PT` to match the version you are running.

| Version | Model class | Checkpoint file |
|---------|-------------|-----------------|
| v7 | `DecoderOnlyLM_RMSNorm_GQA` | `decoder_baseline_v7_final_model.pt` |
| v2 | `DecoderOnlyLM_RoPE` | `decoder_baseline_rope_final_model.pt` |
| v5 | `DecoderOnlyLM_MoE_Sandwich` | `decoder_v5_final_model.pt` |
| v6 | `DecoderOnlyLM_HybridMask` | `decoder_v6_final_model.pt` |


For example, to run v5, set `MODEL_PT` to the v5 checkpoint path:

```python
MODEL_PT = "/kaggle/input/phase2-inputs/decoder_v5_final_model.pt"
```

## How to Run

### Run on Kaggle

1. Open each notebook (Phase 2 through Phase 7) on Kaggle.
2. Click **+ Add Input** on the right panel, search for `triggerboe2/phase2-inputs`, and add it.
3. The files appear read-only under `/kaggle/input/phase2-inputs/`.
4. Load the base model from that path:

```python
HEAD_PATH   = "lm_head"
LAYERS_PATH = "blocks"
FINAL_NORM  = ("ln_f",)
MODEL_PT    = "/kaggle/input/phase2-inputs/decoder_baseline_v7_final_model.pt"
```

Do this in every phase notebook so all phases start from the same base model.
