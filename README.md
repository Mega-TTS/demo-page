
# Mega-TTS
# Zero-Shot Text-to-Speech at Scale with Intrinsic Inductive Bias

## Abstract
Scaling text-to-speech to a large and wild dataset has been proven to be highly effective in achieving timbre and speech style generalization, particularly in zero-shot TTS. However, previous works usually encode speech into latent using audio codec and use autoregressive language models or diffusion models to generate it, which ignores the intrinsic nature of speech and may lead to inferior or uncontrollable results. We argue that speech can be decomposed into several attributes (e.g., content, timbre, prosody, and phase) and each of them should be modeled using a module with appropriate inductive biases. From this perspective, we carefully design a novel and large zero-shot TTS system called Mega-TTS, which is trained with large-scale wild data and models different attributes in different ways: 1) Instead of using latent encoded by audio codec as the intermediate feature, we still choose spectrogram as it separates the phase and other attributes very well. Phase can be appropriately constructed by the GAN-based vocoder and does not need to be modeled by the language model. 2) We model the timbre using global vectors since timbre is a global attribute that changes slowly over time. 3) We further use a VQGAN-based acoustic model to generate the spectrogram and a latent code language model to fit the distribution of prosody, since prosody changes quickly over time in a sentence, and language models can capture both local and long-range dependencies. We scale Mega-TTS to multi-domain datasets with 20K hours of speech and evaluate its performance on unseen speakers. Experimental results demonstrate that Mega-TTS surpasses state-of-the-art TTS systems on zero-shot TTS, speech editing, and cross-lingual TTS tasks, with superior naturalness, robustness, and speaker similarity due to the proper inductive bias of each module.

[*] This page is for <strong>research demonstration purposes</strong> only.

<div style="width:100%;">
<img align="center" src="figure/MegaTTS.png" style="  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 100%;"  /></div>

<div style="width:100%;height:50px;"></div>

## Zero-Shot TTS Samples
<table border="0" width="100%">
  <thead>
    <tr>
      <th align="center"><strong>Text</strong></th>
      <th align="center"><strong>Speaker Prompt</strong></th>
      <th align="center"><strong>Ground Truth</strong></th>
      <th align="center"><strong>YourTTS</strong></th>
      <th align="center"><strong>VALL-E</strong></th>
      <th align="center"><strong>Mega-TTS</strong></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="40%"><p>Yea, his honourable worship is within, but he hath a godly minister or two with him, and likewise a leech.</p></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/prompt/1.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/gt/1.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/yourtts/1.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/valle/1.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/mega-tts/1.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="40%"><p>Instead of shoes, the old man wore boots with turnover tops, and his blue coat had wide cuffs of gold braid.</p></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/prompt/2.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/gt/2.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/yourtts/2.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/valle/2.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/mega-tts/2.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="40%"><p>The army found the people in poverty and left them in comparative wealth.</p></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/prompt/3.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/gt/3.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/yourtts/3.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/valle/3.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/mega-tts/3.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="40%"><p>He was in deep converse with the clerk and entered the hall holding him by the arm.</p></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/prompt/4.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/gt/4.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/yourtts/4.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/valle/4.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/mega-tts/4.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="40%"><p>So what is the campaign about?</p></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/prompt/5.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/gt/5.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/yourtts/5.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/valle/5.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/mega-tts/5.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="40%"><p>Nothing is yet confirmed.</p></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/prompt/6.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/gt/6.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/yourtts/6.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/valle/6.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/mega-tts/6.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="40%"><p>Her husband was very concerned that it might be fatal.</p></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/prompt/7.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/gt/7.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/yourtts/7.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/valle/7.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/mega-tts/7.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="40%"><p>We've made a couple of albums.</p></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/prompt/8.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/gt/8.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/yourtts/8.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/valle/8.wav" type="audio/wav"></audio></td>
      <td width="12%"><audio controls="" ><source src="audio_sample/zero-shot_TTS/mega-tts/8.wav" type="audio/wav"></audio></td>
    </tr>
  </tbody>
</table>  

## Speech Editing Samples
<table border="0" width="100%">
  <thead>
    <tr>
      <th align="center"><strong>Text</strong></th>
      <th align="center"><strong>Original Speech</strong></th>
      <th align="center"><strong>Editspeech</strong></th>
      <th align="center"><strong>A3T</strong></th>
      <th align="center"><strong>Mega-TTS</strong></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="60%"><p>However, there is <strong>an issue</strong>, isn't there? --> However, there is <strong>an obvious issue</strong>, isnt there?</p></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/gt/1.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/editspeech/1.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/a3t/1.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/mega-tts/1.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="60%"><p>Others have tried to explain <strong>the phenomenon</strong> physically. --> Others have tried to explain <strong>the rare phenomenon for them</strong> physically.</p></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/gt/2.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/editspeech/2.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/a3t/2.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/mega-tts/2.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="60%"><p>Well, he <strong>can</strong> do it. --> Well, he <strong>is able to</strong> do it.</p></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/gt/3.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/editspeech/3.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/a3t/3.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/mega-tts/3.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="60%"><p>Throughout the centuries people have <strong>explained the rainbow</strong> in various ways. --> Throughout the centuries people have <strong>constantly explained the rainbow phenomenon</strong> in various ways.</p></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/gt/4.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/editspeech/4.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/a3t/4.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/mega-tts/4.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="60%"><p>She has nothing to <strong>say to</strong> journalists. --> She has nothing to <strong>communicate with</strong> journalists.</p></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/gt/5.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/editspeech/5.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/a3t/5.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/mega-tts/5.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="60%"><p>I am confident of <strong>the outcome</strong> this week. --> I am confident of <strong>the midsemester outcome at</strong> this week.</p></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/gt/6.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/editspeech/6.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/a3t/6.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/mega-tts/6.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="60%"><p>Something <strong>happened</strong> on that island. --> Something <strong>wrong suddenly happened</strong> on that island.</p></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/gt/7.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/editspeech/7.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/a3t/7.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/mega-tts/7.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="60%"><p>You probably <strong>have never seen</strong> them before. --> You probably <strong>have worked with</strong> them before.</p></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/gt/8.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/editspeech/8.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/a3t/8.wav" type="audio/wav"></audio></td>
      <td width="10%"><audio controls="" ><source src="audio_sample/speech_editing/mega-tts/8.wav" type="audio/wav"></audio></td>
    </tr>
  </tbody>
</table>


## Cross-Lingual TTS Samples
<table border="0" width="100%">
  <thead>
    <tr>
      <th align="center"><strong>English Text</strong></th>
      <th align="center"><strong>Chinese Speaker Prompt</strong></th>
      <th align="center"><strong>YourTTS</strong></th>
      <th align="center"><strong>VALL-E</strong></th>
      <th align="center"><strong>Mega-TTS</strong></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="40%"><p>He honours whatever he recognizes in himself, such morality equals self-glorification.</p></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/prompt_chinese/1.wav" type="audio/wav"></audio></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/yourtts_engligh/1.wav" type="audio/wav"></audio></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/vallex_englisht/1.wav" type="audio/wav"></audio></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/mega-tts_english/1.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="40%"><p>There could be little art in this last and final round of fencing.</p></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/prompt_chinese/2.wav" type="audio/wav"></audio></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/yourtts_engligh/2.wav" type="audio/wav"></audio></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/vallex_englisht/2.wav" type="audio/wav"></audio></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/mega-tts_english/2.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="40%"><p>It's the first time Hilda has been to our house and Tom introduces her around.</p></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/prompt_chinese/3.wav" type="audio/wav"></audio></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/yourtts_engligh/3.wav" type="audio/wav"></audio></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/vallex_englisht/3.wav" type="audio/wav"></audio></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/mega-tts_english/3.wav" type="audio/wav"></audio></td>
    </tr>
    <tr>
      <td width="40%"><p>It was youth and poverty and proximity and everything was young and kindly.</p></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/prompt_chinese/4.wav" type="audio/wav"></audio></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/yourtts_engligh/4.wav" type="audio/wav"></audio></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/vallex_englisht/4.wav" type="audio/wav"></audio></td>
      <td width="15%"><audio controls="" ><source src="audio_sample/cross-lingual_TTS/mega-tts_english/4.wav" type="audio/wav"></audio></td>
    </tr>
  </tbody>
</table> 

