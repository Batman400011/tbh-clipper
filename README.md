# TBH Clipper

Turns a long recording into upload-ready clips.

Point it at a panel show, podcast or stream and it transcribes the audio,
finds where the topics change, cuts the clips, bleeps flagged words in the
audio, writes titles and descriptions, and builds thumbnails — while you do
something else.

Runs entirely on your own machine. Nothing is uploaded anywhere.

---

## Download

**[Download the latest version](../../releases/latest)**

Unzip it somewhere permanent — Documents is fine. Don't leave it inside
your Downloads folder, since that's where it looks for videos to process.

Then double-click **`Start TBH Clipper.bat`**.

That's the only thing you ever double-click. The first run installs
everything; every run after that just opens the app.

---

## Before you start

**Windows will warn you.** Because the download isn't code-signed, you'll
see *"Windows protected your PC"* with only a **Don't run** button. Click
**More info**, then **Run anyway**. This is Windows being cautious about
any unsigned download, not a sign that something is wrong.

**The first run takes 30–60 minutes** and downloads several GB. It's
installing Python, ffmpeg, Ollama and the AI models the tool runs on. That
is genuinely the size of this software.

You may be asked to close the window and double-click again once or twice.
That's expected — Windows needs to refresh its PATH after installing
something, and the script stops rather than continuing in a broken state.

**An Ollama window will probably open** at some point, showing a list of
models and possibly asking you to sign in. **Close it and ignore it.** The
setup downloads the one model it needs by itself — you don't have to pick
anything, and you don't need an Ollama account.

---

## What you need

- Windows 10 or 11
- About 10 GB of free disk space
- Patience on the first run

No graphics card required. It runs on the CPU, which is slower but works on
any normal laptop.

---

## How long a run takes

Roughly **3–4× the length of your video**. A 4-hour recording takes about
13 hours to process.

It checkpoints as it goes, so you can close it and it picks up where it
left off rather than starting over.

---

## Bleeping

Flagged words are replaced with a tone in the finished audio — not just
flagged in text, actually censored in the sound.

The word list lives in `flagged_words.json`, a plain text file you can open
and edit. Matching is whole-word, so `ass` doesn't catch `classic`. It
matches exact forms, so adding `fuck` doesn't cover `fucking` — add both if
you want both.

---

## Speaker labels (optional)

Setup offers to turn this on. You can skip it and add it later in the app
under **Speaker ID**.

It labels who is speaking, which also feeds the debate detection that looks
for rapid back-and-forth. Without it everything else still works — you just
lose speaker names.

The model is free, but its authors require an account:

1. Sign up at [huggingface.co](https://huggingface.co/join)
2. Accept the terms at
   [pyannote/speaker-diarization-3.1](https://huggingface.co/pyannote/speaker-diarization-3.1)
   — this is the step people miss, and it must be the same account
3. Create a token at [settings › tokens](https://huggingface.co/settings/tokens)
4. Paste it into setup, or into **Speaker ID** in the app

---

## Updating

Download the new zip and extract it over your existing folder. Your
settings, presets and installed environment are preserved — none of that
ships in the download.

The app notices the version changed and refreshes its packages on the next
launch.

---

## If something goes wrong

Setup stops and prints the actual error rather than pretending it worked.
Scroll up in the black window, find the line starting with `ERROR`, and
open an issue with it.
