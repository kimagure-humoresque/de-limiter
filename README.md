# De-limiter

Derived from [the official repository](https://github.com/jeonchangbin49/De-limiter).

## Usage

```sh
$ pip install git+https://github.com/Ishotihadus/de-limiter
```

```python
import de_limiter
import torchaudio
import soundfile as sf

model, sr = de_limiter.load_pretrained_model()
wav, _ = torchaudio.sox_effects.apply_effects_file("input.wav", [["rate", "-vsL", f"{sr}"]])
_, result, *_ = model(wav.unsqueeze(0))
sf.write("output.wav", result.squeeze(0).detach().cpu().numpy().T, sr)
```

## License

This repository is licensed under the MIT License.
