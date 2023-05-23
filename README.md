
# Mega-TTS: Zero-Shot Text-to-Speech at Scale with Intrinsic Inductive Bias

## Abstract

Scaling text-to-speech to a large and wild dataset has been proven to be highly effective in achieving timbre and speech style generalization, particularly in zero-shot TTS. However, previous works usually encode speech into latent using audio codec and use autoregressive language models or diffusion models to generate it, which ignores the intrinsic nature of speech and may lead to inferior or uncontrollable results. We argue that speech can be decomposed into several attributes (e.g., content, timbre, prosody, and phase) and each of them should be modeled using a module with appropriate inductive biases. From this perspective, we carefully design a novel and large zero-shot TTS system called Mega-TTS, which is trained with large-scale wild data and models different attributes in different ways: 1) Instead of using latent encoded by audio codec as the intermediate feature, we still choose spectrogram as it separates the phase and other attributes very well. Phase can be appropriately constructed by the GAN-based vocoder and does not need to be modeled by the language model. 2) We model the timbre using global vectors since timbre is a global attribute that changes slowly over time. 3) We further use a VQGAN-based acoustic model to generate the spectrogram and a latent code language model to fit the distribution of prosody, since prosody changes quickly over time in a sentence, and language models can capture both local and long-range dependencies. We scale Mega-TTS to multi-domain datasets with 20K hours of speech and evaluate its performance on unseen speakers. Experimental results demonstrate that Mega-TTS surpasses state-of-the-art TTS systems on zero-shot TTS, speech editing, and cross-lingual TTS tasks, with superior naturalness, robustness, and speaker similarity due to the proper inductive bias of each module. Audio samples are available at https://mega-tts.github.io/demo-page.

<div style="width:100%;">
<img align="center" src="figure/MegaTTS.png" style="  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 100%;"  /></div>


## Zero-Shot TTS Samples
<table border="0" width="100%">
  <thead>
    <tr>
      <th align="center"><h3><b>Text</b></h3></th>
      <th align="center">Speaker Prompt</th>
      <th align="center">Ground Truth</th>
      <th align="center">YourTTS</th>
      <th align="center">VALL-E</th>
      <th align="center">Mega-TTS</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="40%"><p>They moved thereafter cautiously about the hut groping before and about them to find something to show that Warrenton had fulfilled his mission.</p></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/vsvalle_prompt/1.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/vsvalle_gt/1.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/vsvalle_yourtts/1.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/vsvalle_valle/1.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/vsvalle_mega-tts/1.wav" type="audio/wav"></audio></td>
    </tr>
  </tbody>
</table>  