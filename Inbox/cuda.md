

24-05-2026 16:09

Status: #in_progress

Tags:

# cuda

## installation
``` bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128
```
### verify
``` python
python - <<'PY'
import torch

print("torch:", torch.__version__)
print("torch file:", torch.__file__)
print("cuda available:", torch.cuda.is_available())
print("torch cuda version:", torch.version.cuda)

if torch.cuda.is_available():
    print("gpu:", torch.cuda.get_device_name(0))
    x = torch.randn(3, 3, device="cuda")
    print(x)
PY
```

## My Questions


## References

