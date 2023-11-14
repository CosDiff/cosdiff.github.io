


{:.no_toc}
* toc
{:toc}



# Abstract
Although existing text-to-speech (TTS) synthesis models can generate high-quality speech, their performance is typically influenced by the distribution of the training data. When processing tasks that involve complex data distributions, such as code-switching TTS, these models might generate speech that sounds unnatural or has low speaker similarity. In this paper, we propose CosDiff, a novel approach for \textbf{co}de-\textbf{s}witched TTS enabled by denoising \textbf{diff}usion implicit model (DDIM) and self-supervising soft units. We convert a single-speaker monolingual dataset into a single-speaker bilingual dataset to learn the complex distributional features of the bilingual dataset by simulating the stochastic diffusion process, thus successfully achieving a code-switched TTS effect close to natural speech. In addition, we employ strategies of directly predicting the clean data $x_0$ and progressive diffusion distillation, further accelerating the model's sampling process. Experimental results demonstrate the efficacy of our method in terms of generation quality, sampling speed, and model distillation.



## Performance

### LJSpeech
<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">Tacotron 2</th>
            <th style="text-align: center">FastSpeech 2</th>
            <th style="text-align: center">GANSpeech</th>
            <th style="text-align: center">Glow-TTS</th>
            <th style="text-align: center">Grad-TTS</th>
            <th style="text-align: center">DiffSpeech</th>
            <th style="text-align: center">ProDiff Teacher</th>
            <th style="text-align: center">ProDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/FastSpeech 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Glow-TTS/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Grad-TTS/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/DiffSpeech/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/ProDiff Teacher/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/ProDiff/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: the ends of many of the letters such as the t and e are hooked up in a vulgar and meaningless way</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">Tacotron 2</th>
            <th style="text-align: center">FastSpeech 2</th>
            <th style="text-align: center">GANSpeech</th>
            <th style="text-align: center">Glow-TTS</th>
            <th style="text-align: center">Grad-TTS</th>
            <th style="text-align: center">DiffSpeech</th>
            <th style="text-align: center">ProDiff Teacher</th>
            <th style="text-align: center">ProDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000004][LJ001-0111][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000004][LJ001-0111][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/FastSpeech 2/[000004][LJ001-0111][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000004][LJ001-0111][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Glow-TTS/[000004][LJ001-0111][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Grad-TTS/[000004][LJ001-0111][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/DiffSpeech/[000004][LJ001-0111][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/ProDiff Teacher/[000004][LJ001-0111][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/ProDiff/[000004][LJ001-0111][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

Reference/Target Text: The essential point to be remembered is that the ornament, whatever it is, whether picture or pattern-work, should form part of the page
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">Tacotron 2</th>
            <th style="text-align: center">FastSpeech 2</th>
            <th style="text-align: center">GANSpeech</th>
            <th style="text-align: center">Glow-TTS</th>
            <th style="text-align: center">Grad-TTS</th>
            <th style="text-align: center">DiffSpeech</th>
            <th style="text-align: center">ProDiff Teacher</th>
            <th style="text-align: center">ProDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000005][LJ001-0173][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/DiffSpeech/[000005][LJ001-0173][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/FastSpeech 2/[000005][LJ001-0173][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000005][LJ001-0173][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Glow-TTS/[000005][LJ001-0173][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Grad-TTS/[000005][LJ001-0173][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/DiffSpeech/[000005][LJ001-0173][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/ProDiff Teacher/[000005][LJ001-0173][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/ProDiff/[000005][LJ001-0173][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: The prison population fluctuated a great deal</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">Tacotron 2</th>
            <th style="text-align: center">FastSpeech 2</th>
            <th style="text-align: center">GANSpeech</th>
            <th style="text-align: center">Glow-TTS</th>
            <th style="text-align: center">Grad-TTS</th>
            <th style="text-align: center">DiffSpeech</th>
            <th style="text-align: center">ProDiff Teacher</th>
            <th style="text-align: center">ProDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000006][LJ002-0005][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000006][LJ002-0005][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/FastSpeech 2/[000006][LJ002-0005][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000006][LJ002-0005][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Glow-TTS/[000006][LJ002-0005][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Grad-TTS/[000006][LJ002-0005][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/DiffSpeech/[000006][LJ002-0005][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/ProDiff Teacher/[000006][LJ002-0005][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/ProDiff/[000006][LJ002-0005][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

### LibriTTS

Reference/Target Text: villeforts conduct , therefore , upon reflection , appeared to the baroness as if shaped for their mutual advantage .
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">Tacotron 2</th>
            <th style="text-align: center">FastSpeech 2</th>
            <th style="text-align: center">GANSpeech</th>
            <th style="text-align: center">Glow-TTS</th>
            <th style="text-align: center">Grad-TTS</th>
            <th style="text-align: center">DiffSpeech</th>
            <th style="text-align: center">ProDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/GT/000.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/Tacotron 2/000.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/FastSpeech2/000.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/GANSpeech/000.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/Glow-TTS/000.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/Grad-TTS/000.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/DiffSpeech/000.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/ProDiff/000.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

Reference/Target Text: she would invoke the past , recall old recollections ; she would supplicate him by the remembrance of guilty , yet happy days .
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">Tacotron 2</th>
            <th style="text-align: center">FastSpeech 2</th>
            <th style="text-align: center">GANSpeech</th>
            <th style="text-align: center">Glow-TTS</th>
            <th style="text-align: center">Grad-TTS</th>
            <th style="text-align: center">DiffSpeech</th>
            <th style="text-align: center">ProDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/GT/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/Tacotron 2/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/FastSpeech2/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/GANSpeech/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/Glow-TTS/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/Grad-TTS/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/DiffSpeech/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/ProDiff/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: do you intend opening the door ? said the baroness .</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">Tacotron 2</th>
            <th style="text-align: center">FastSpeech 2</th>
            <th style="text-align: center">GANSpeech</th>
            <th style="text-align: center">Glow-TTS</th>
            <th style="text-align: center">Grad-TTS</th>
            <th style="text-align: center">DiffSpeech</th>
            <th style="text-align: center">ProDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/GT/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/Tacotron 2/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/FastSpeech2/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/GANSpeech/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/Glow-TTS/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/Grad-TTS/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/DiffSpeech/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/ProDiff/002.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: come , forget him for a moment , and instead of pursuing him let him go .</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">Tacotron 2</th>
            <th style="text-align: center">FastSpeech 2</th>
            <th style="text-align: center">GANSpeech</th>
            <th style="text-align: center">Glow-TTS</th>
            <th style="text-align: center">Grad-TTS</th>
            <th style="text-align: center">DiffSpeech</th>
            <th style="text-align: center">ProDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/GT/003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/Tacotron 2/003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/FastSpeech2/003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/GANSpeech/003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/Glow-TTS/003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/Grad-TTS/003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/DiffSpeech/003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LibriTTS/ProDiff/003.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

## Ablation 


<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">w/o GP</th>
            <th style="text-align: center">w/o KD</th>
            <th style="text-align: center">Teacher(T=16)</th>
            <th style="text-align: center">Teacher(T=8)</th>
            <th style="text-align: center">ProDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table1/Score-2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table1/Generator-2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/ProDiff-16/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/ProDiff-8/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/ProDiff-2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: the ends of many of the letters such as the t and e are hooked up in a vulgar and meaningless way</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">w/o GP</th>
            <th style="text-align: center">w/o KD</th>
            <th style="text-align: center">Teacher(T=16)</th>
            <th style="text-align: center">Teacher(T=8)</th>
            <th style="text-align: center">ProDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/GT/[000004][LJ001-0111][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table1/Score-2/[000004][LJ001-0111][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table1/Generator-2/[000004][LJ001-0111][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/ProDiff-16/[000004][LJ001-0111][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/ProDiff-8/[000004][LJ001-0111][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/ProDiff-2/[000004][LJ001-0111][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

Reference/Target Text: The essential point to be remembered is that the ornament, whatever it is, whether picture or pattern-work, should form part of the page
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">w/o GP</th>
            <th style="text-align: center">w/o KD</th>
            <th style="text-align: center">Teacher(T=16)</th>
            <th style="text-align: center">Teacher(T=8)</th>
            <th style="text-align: center">ProDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/GT/[000005][LJ001-0173][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table1/Score-2/[000005][LJ001-0173][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table1/Generator-2/[000005][LJ001-0173][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/ProDiff-16/[000005][LJ001-0173][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/ProDiff-8/[000005][LJ001-0173][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/ProDiff-2/[000005][LJ001-0173][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: The prison population fluctuated a great deal</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">w/o GP</th>
            <th style="text-align: center">w/o KD</th>
            <th style="text-align: center">Teacher(T=16)</th>
            <th style="text-align: center">Teacher(T=8)</th>
            <th style="text-align: center">ProDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/GT/[000006][LJ002-0005][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table1/Score-2/[000006][LJ002-0005][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table1/Generator-2/[000006][LJ002-0005][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/ProDiff-16/[000006][LJ002-0005][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/ProDiff-8/[000006][LJ002-0005][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table3/ProDiff-2/[000006][LJ002-0005][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


