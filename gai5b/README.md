# G/AI 5B Dataset Builder

Mục tiêu mặc định: 5,000,000,000 token THẬT. Không oversampling để bơm số token.

Pipeline streaming + quality filtering + document SHA-256 dedup + consecutive 2-sentence dedup. Shard chuẩn 500K token, trong giới hạn 100K–1M.

Run trên máy có GPU/storage lớn:

```bash
pip install -U datasets transformers tqdm
python build_5b.py --tokenizer gpt2 --out gai_5b_shards --resume
python validate_5b.py gai_5b_shards
```

Thay `gpt2` bằng tokenizer cuối cùng của G/AI trước khi chốt thống kê, vì cùng văn bản có thể cho số token khác nhau với tokenizer khác.

Raw datasets bên ngoài không được nhúng vào repository này nếu license không cho phép redistribution. Builder tải chúng lúc training và ghi provenance vào manifest.
