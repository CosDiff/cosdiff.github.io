


{:.no_toc}
* toc
{:toc}



# Abstract
Although existing text-to-speech (TTS) synthesis models can generate high-quality speech, their performance is typically influenced by the distribution of the training data. When processing tasks that involve complex data distributions, such as code-switching TTS, these models might generate speech that sounds unnatural or has low speaker similarity. In this paper, we propose CosDiff, a novel approach for code-switched TTS enabled by denoising diffusion implicit model (DDIM) and self-supervising soft units. We convert a single-speaker monolingual dataset into a single-speaker bilingual dataset to learn the complex distributional features of the bilingual dataset by simulating the stochastic diffusion process, thus successfully achieving a code-switched TTS effect close to natural speech. In addition, we employ strategies of directly predicting the clean data $x_0$ and progressive diffusion distillation, further accelerating the model's sampling process. Experimental results demonstrate the efficacy of our method in terms of generation quality, sampling speed, and model distillation.
<img src="images/1.png">
# Audio quality
## Cross-lingual conversion comparison
#### Source speaker: Mandarin female; Target speaker: English female
<ruby>Reference/Target Text: 最终，中国男子乒乓球队获得此奖项</ruby>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_cn/009929.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_en/LJ050-0130.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/Vc/EN-CN/soft-vc/softvc_en_009929.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/Vc/EN-CN/cosdiff/cosdiff_en_009929.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


<ruby>Reference/Target Text: 刚认识就要妹子皂片？再聊十块钱的吧</ruby>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_cn/009811.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_en/LJ050-0130.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/Vc/EN-CN/soft-vc/softvc_en_009811.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/Vc/EN-CN/cosdiff/cosdiff_en_009811.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>






#### Source speaker: English female; Target speaker: Mandarin female
<ruby>Reference/Target Text: However, the nineteen sixty-four to sixty-five budget request was submitted in November nineteen sixty-three</ruby>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_en/LJ050-0219.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_cn/009942.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/Vc/CN-EN/soft-vc/softvc_cn_LJ050-0219.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/Vc/CN-EN/cosdiff/cosdiff_cn_LJ050-0219.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


<ruby>Reference/Target Text: between Secretary Dillon and Donald F. Hornig, Special Assistant to the President for Science and Technology, is a useful effort in the right direction</ruby>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_en/LJ050-0267.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_cn/009942.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/Vc/CN-EN/soft-vc/softvc_cn_LJ050-0267.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/Vc/CN-EN/cosdiff/cosdiff_cn_LJ050-0267.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>






## Intra-lingual synthesis comparison
#### Chinese
<ruby>Reference/Target Text: 倒水的学生只听到前半句，遵其命再倾其余水，边倒边叫：去你的</ruby>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_cn/009880.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-tacotron2/CN/Intra_tacotron2_CN_009880.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-fs2/CN/Intra_fs2_CN_009880.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-grandtts/CN/Intra_gradtts_CN_009880.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-cosdiff/CN/Intra_cosdiff_CN_009880.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: 传闻越来越多，后来连老汉儿自己都怕了</ruby>
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
				<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_cn/009942.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-tacotron2/CN/Intra_tacotron2_CN_009942.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-fs2/CN/Intra_fs2_CN_009942.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-grandtts/CN/Intra_gradtts_CN_009942.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-cosdiff/CN/Intra_cosdiff_CN_009942.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


#### English
<ruby>Reference/Target Text: in this crucial area of Presidential protection</ruby>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_en/LJ050-0203.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-tacotron2/EN/Intra_tacotron2_EN_LJ050-0203.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-fs2/EN/Intra_fs2_EN_LJ050-0203.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-grandtts/EN/Intra_gradtts_EN_LJ050-0203.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-cosdiff/EN/Intra_cosdiff_EN_LJ050-0203.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: would take approximately twenty months to implement and require expenditures of approximately three million dollars during that period</ruby>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_en/LJ050-0222.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-tacotron2/EN/Intra_tacotron2_EN_LJ050-0222.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-fs2/EN/Intra_fs2_EN_LJ050-0222.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-grandtts/EN/Intra_gradtts_EN_LJ050-0222.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Intra/Intra-cosdiff/EN/Intra_cosdiff_EN_LJ050-0222.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>



## Cross-lingual synthesis
#### Text: Chinese; Speaker: English female
<ruby>Reference/Target Text: 碰上这样的想合影就会非常困难</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">English speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_en/LJ050-0203.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Cross/EN-CN/Cross_cosdiff_EN_009801.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: 经区政府与多方协调，重新上路</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">English speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_en/LJ050-0203.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Cross/EN-CN/Cross_cosdiff_EN_009803.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


#### Text: English; Speaker: Mandarin female
<ruby>Reference/Target Text: This Commission can recommend no procedures for the future protection of our Presidents which will guarantee security</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">Mandarin speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_cn/009942.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Cross/CN-EN/Cross_cosdiff_CN_LJ050-0270.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: Thus, the local chief of police could be given a master plan, prepared for the occasion, of all protective measures to be taken during the visit</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">Mandarin speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_cn/009942.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/Cross/CN-EN/Cross_cosdiff_CN_LJ050-0187.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


## Code-switching synthesis
#### Text: Chinese+English; Speaker: Mandarin female
<ruby>Reference/Target Text: 我的老板经常说：Work hard, play hard</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">Chinese speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_cn/009942.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/code-swithing/CN/code-swithing_cosdiff_CN_1.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: 我们来读一首诗,千山鸟飞绝,From hill to hill no bird in flight,万径人踪灭,From path to path no man in sight</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">Chinese speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_cn/009942.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/code-swithing/CN/code-swithing_cosdiff_CN_3.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


#### Text: Chinese+English; Speaker: English female
<ruby>Reference/Target Text: 这个源于拳击运动的表达 “to punch above your weight”的本意是“能和高于自己重量级别的对手较量”</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">English speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_en/LJ050-0203.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/code-swithing/EN/code-swithing_cosdiff_EN_4.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: 《阿甘正传》这部电影的英文名字是《Forrest Gump》</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">English speaker</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_en/LJ050-0203.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/code-swithing/EN/code-swithing_cosdiff_EN_5.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>




## Ablation
#### Text: Chinese+English; Speaker: Mandarin female
<ruby>Reference/Target Text: 他的座右铭是：“live and let live“，意思是活在当下，并让别人也这样做</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">Chinese speaker</th>
			<th style="text-align: center">Teahcer(T=4) Synthesized Text</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_cn/009942.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/code-swithing_teacher/CN/code-swithing_cosdifteacher_CN_9.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/code-swithing/CN/code-swithing_cosdiff_CN_9.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: 明天的会议准备好了吗？make sure all documents are ready</ruby>
<table>
	<thead>
		<tr>
                                               <th style="text-align: center">Chinese speaker</th>
			<th style="text-align: center">Teahcer(T=4) Synthesized Text</th>
			<th style="text-align: center">CosDiff Synthesized Text</th>
		</tr>
	</thead>
	<tbody>
		<tr>
             <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_cn/009942.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/code-swithing_teacher/CN/code-swithing_cosdifteacher_CN_8.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/code-swithing/CN/code-swithing_cosdiff_CN_8.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>



#### Text: Chinese+English; Speaker: English female
<ruby>Reference/Target Text: 他的座右铭是：“live and let live“，意思是活在当下，并让别人也这样做</ruby>
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
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_en/LJ050-0267.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/code-swithing_teacher/EN/code-swithing_cosdifteacher_EN_9.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/code-swithing/EN/code-swithing_cosdiff_EN_9.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Reference/Target Text: 明天的会议准备好了吗？make sure all documents are ready</ruby>
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
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/GTWAV/GTWAV_en/LJ050-0267.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/code-swithing_teacher/EN/code-swithing_cosdifteacher_EN_8.wav.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="zh/TTS/code-swithing/EN/code-swithing_cosdiff_EN_8.wav.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


