# Gemini Chat Experiments 🤖

Look, we've all been there. You want to play around with Google's shiny new Gemini API but you don't want to deal with all the boilerplate. This notebook is basically my scratchpad for messing around with Gemini 2.0 Flash.

## What's This About?

Just a straightforward Colab notebook where I'm testing out the Google Gemini API. Nothing fancy, nothing production-ready, just pure experimentation. Started with simple prompts, moved on to chat sessions, and threw in some code generation for good measure.

## The Setup

You'll need:
- Google Colab (or Jupyter if you're running locally)
- A Google API key (store it in Colab secrets as `GOOGLE_API_KEY`)
- That's literally it

## What's Inside

The notebook walks through:
1. **Basic setup** - importing the genai library and handling those annoying rate limit errors
2. **Simple prompts** - asking Gemini to explain stuff like it's talking to a 5-year-old (classic)
3. **Chat sessions** - maintaining conversation history, because context matters
4. **Creative writing** - getting it to write poems and essays about random stuff
5. **Code generation** - making it write Java factorial functions (because why not?)

## The Good Bits

### Retry Logic
Added some retry logic for when the API gets cranky:
```python
is_retriable = lambda e: (isinstance(e, genai.errors.APIError) and e.code in {429, 503})
```
Honestly saved me from so many "quota exceeded" headaches.

### Pretty Output
Used IPython's Markdown display to make the responses actually readable. Raw text output is fine, but formatted markdown just hits different.

### Chat Memory
The chat object keeps track of conversation history, which is neat. You can have actual back-and-forth conversations instead of isolated queries.

## Config Tweaks

There's a `short_config` object floating around that controls:
- `temperature` - how creative/random the responses are
- `top_p` - nucleus sampling stuff
- `max_output_tokens` - so it doesn't ramble forever

## Things I Learned

- The API is pretty straightforward once you get past the initial setup
- Gemini 2.0 Flash is surprisingly fast (hence the name, I guess)
- Chat sessions are way more useful than one-off prompts
- The retry decorator is your friend when dealing with rate limits

## Want to Use This?

1. Copy the notebook to your Google Drive
2. Add your API key to Colab secrets
3. Run the cells in order (or don't, I'm not your supervisor)
4. Experiment and break things

## Future Ideas

- Stream responses for that ChatGPT-like experience
- Add image generation/analysis
- Build something actually useful instead of just playing around
- Maybe add some error handling that isn't just "retry and hope"

## Disclaimer

This is literally just me learning and experimenting. If you're looking for production-ready code, this ain't it. But if you want to see how someone else stumbled through the Gemini API docs and made something work, welcome aboard.

## License

Do whatever you want with this. Seriously. It's a notebook with API calls, not rocket science.

---

*Built while procrastinating on actual work, powered by coffee and curiosity*
