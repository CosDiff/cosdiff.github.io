


{:.no_toc}
* toc
{:toc}



# Abstract
Although existing text-to-speech (TTS) synthesis models can generate high-quality speech, their performance is typically influenced by the distribution of the training data. When processing tasks that involve complex data distributions, such as code-switching TTS, these models might generate speech that sounds unnatural or has low speaker similarity. In this paper, we propose CosDiff, a novel approach for \textbf{co}de-\textbf{s}witched TTS enabled by denoising \textbf{diff}usion implicit model (DDIM) and self-supervising soft units. We convert a single-speaker monolingual dataset into a single-speaker bilingual dataset to learn the complex distributional features of the bilingual dataset by simulating the stochastic diffusion process, thus successfully achieving a code-switched TTS effect close to natural speech. In addition, we employ strategies of directly predicting the clean data $x_0$ and progressive diffusion distillation, further accelerating the model's sampling process. Experimental results demonstrate the efficacy of our method in terms of generation quality, sampling speed, and model distillation.


## Cross-lingual conversion comparison
#### Source speaker: Mandarin female; Target speaker: English female
<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source speaker</th>
            <th style="text-align: center">Target Speaker</th>
            <th style="text-align: center">Soft-Vc</th>
            <th style="text-align: center">CosDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/FastSpeech 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source speaker</th>
            <th style="text-align: center">Target Speaker</th>
            <th style="text-align: center">Soft-Vc</th>
            <th style="text-align: center">CosDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/FastSpeech 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>






#### Source speaker: English female; Target speaker: Mandarin female
<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source speaker</th>
            <th style="text-align: center">Target Speaker</th>
            <th style="text-align: center">Soft-Vc</th>
            <th style="text-align: center">CosDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/FastSpeech 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source speaker</th>
            <th style="text-align: center">Target Speaker</th>
            <th style="text-align: center">Soft-Vc</th>
            <th style="text-align: center">CosDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/FastSpeech 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>






## Intra-lingual synthesis comparison
#### Chinese
<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">Tacotron 2</th>
            <th style="text-align: center">FastSpeech 2</th>
            <th style="text-align: center">Grad-TTS</th>
            <th style="text-align: center">CosDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/FastSpeech 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">Tacotron 2</th>
            <th style="text-align: center">FastSpeech 2</th>
            <th style="text-align: center">Grad-TTS</th>
            <th style="text-align: center">CosDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/FastSpeech 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


#### English
<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">Tacotron 2</th>
            <th style="text-align: center">FastSpeech 2</th>
            <th style="text-align: center">Grad-TTS</th>
            <th style="text-align: center">CosDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/FastSpeech 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Recording</th>
            <th style="text-align: center">Tacotron 2</th>
            <th style="text-align: center">FastSpeech 2</th>
            <th style="text-align: center">Grad-TTS</th>
            <th style="text-align: center">CosDiff</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/FastSpeech 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GanSpeech/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>



## Cross-lingual synthesis
#### Text: Chinese; Speaker: English female
<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">English speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">English speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


#### Text: English; Speaker: Mandarin female
<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">Mandarin speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">Mandarin speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


## Code-switching synthesis
#### Text: Chinese+English; Speaker: Mandarin female
<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">English speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">English speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


#### Text: Chinese+English; Speaker: English female
<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">English speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">English speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>




## Ablation
#### Text: Chinese+English; Speaker: Mandarin female
<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">English speaker</th>
			<th style="text-align: center">Teahcer Synthesized Text</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">English speaker</th>
			<th style="text-align: center">Teahcer Synthesized Text</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>



#### Text: Chinese+English; Speaker: English female
<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">English speaker</th>
			<th style="text-align: center">Teahcer(T=4) Synthesized Text</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: This type was introduced into England by Wynkyn de Worde, Caxton's successor</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">English speaker</th>
			<th style="text-align: center">Teahcer(T=4) Synthesized Text</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/GT/[000000][LJ001-0069][G].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wav_for_demo/table2/LJSpeech/Tacotron 2/[000000][LJ001-0069][P].wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


