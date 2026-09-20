A arquitetura do Sage arch sm_75 TURIN


FP16 Q ──quantização──> INT8 Q
                          │
                          │ 128 × D
                          ▼
                     ┌─────────┐
                     │         │
INT8 K ─────────────>│ Q × K   │
 64 × D              │         │
                     └────┬────┘
                          │
                     FP32 qk
                          │
                    online softmax
                          │
                          ▼
FP16 V ───────────────> P × V
     64 × D               │
                          ▼
                       FP32 acc
                          │
                     próximo K/V
