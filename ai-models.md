# How the AI works — Mathsboard

[Versión en español](es/modelos-ia.md)

Mathsboard uses two different engines.

1. **Its own maths engine**, built into the App. It computes the worked steps of every lesson, the graphs and the interactive explorers. It needs no AI and no internet, and it is always available.
2. **An AI model**, which does what needs language:
   - reading your handwriting;
   - explaining steps in words;
   - answering your questions;
   - giving hints;
   - creating new exercises.

You can choose one of three AI options in **Settings**. Only the one you choose is used.

## 1. Apple Intelligence (default)

- The App uses Apple's on-device language model (Foundation Models).
- Everything runs **on your iPad**. Nothing is sent anywhere.
- It answers immediately and needs no download.
- It requires an iPad that supports Apple Intelligence, with Apple Intelligence turned on in Settings.

## 2. On-device model (optional)

- An open model, **Gemma 4 E2B** (4-bit, MLX format), runs directly on the iPad's chip through Apple's MLX framework.
- It works offline and handles images (your handwriting) itself.
- **Download:** about 3.5 GB, only once, the first time you select it.
  - The model comes from Hugging Face (`mlx-community/gemma-4-e2b-it-4bit`).
  - The download runs in the background. You can keep using the App or cancel it.
- **Privacy:** after the download, nothing leaves the iPad. The only network request is the download itself.
- It needs an iPad with 8 GB of memory or more.

## 3. DAFO Swarm

DAFO Swarm is a separate app that you install **on your own Mac** (Apple Silicon). It turns the Mac into an AI server for your iPad.

- **Why use it:** a Mac can run larger and more capable models than an iPad, and the iPad keeps its memory and battery free.
- **How it works:**
  1. Install DAFO Swarm on the Mac. It downloads and runs the model on the Mac, using MLX.
  2. The Mac publishes a standard, OpenAI-compatible API on your local network.
  3. In Mathsboard, open *Settings → AI* and enter the Mac's address, for example `http://192.168.1.20:43100/v1`.
  4. When you ask something, the iPad sends the exercise (text and the image of your handwriting) to **your** Mac. The Mac answers, and the iPad shows the result.
- **Privacy:** your exercises only travel between your iPad and your Mac, on your own network. We never receive them.
- **Download:** installers for DAFO Swarm are published at [github.com/gabgiani/dafo-swarm-downloads](https://github.com/gabgiani/dafo-swarm-downloads/releases).
- **Model mirrors:** that same page hosts mirrors of the models, split into parts. DAFO Swarm uses them when Hugging Face is slow or unavailable, and joins the parts back together automatically.

## Summary

| | Apple Intelligence | On-device model | DAFO Swarm |
|---|---|---|---|
| Runs on | iPad | iPad | Your Mac |
| Download | None | ~3.5 GB, once | The model is downloaded on the Mac |
| Works offline | Yes | Yes | Local network needed |
| Your data leaves the iPad | No | No | Only to your own Mac |
