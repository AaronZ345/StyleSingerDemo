{:.no_toc}
* toc
{:toc}

# Abstract

Style transfer for out-of-domain (OOD) singing voice synthesis (SVS) focuses on generating high-quality singing voices with unseen styles (such as timbre, emotion, pronunciation, and articulation skills) derived from reference singing voice samples.
However, the endeavor to model the intricate nuances of singing voice styles is an arduous task, as singing voices possess a remarkable degree of expressiveness. 
Moreover, existing SVS methods encounter a decline in the quality of synthesized singing voices in OOD scenarios, as they rest upon the assumption that the target vocal attributes are discernible during the training phase.
To overcome these challenges, we propose StyleSinger, the first singing voice synthesis model for zero-shot style transfer of out-of-domain reference singing voice samples. 
StyleSinger incorporates two critical approaches for enhanced effectiveness: 
1) the Residual Style Adaptor (RSA) which employs a residual quantization module to capture diverse style characteristics in singing voices, and
2) the Uncertainty Modeling Layer Normalization (UMLN) to perturb the style attributes within the content representation during the training phase and thus improve the model generalization. 
Our extensive evaluations in zero-shot style transfer undeniably establish that StyleSinger outperforms baseline models in both audio quality and similarity to the reference singing voice samples.

# Parallel Style Transfer Samples

In the context of out-of-domain (OOD) scenarios, where the content of the reference voice remains unchanged.

1.Reference/Target: 风花雪月的诗句里我在年年的成长 AP

global style class: tenor happy

<table style='width: 33.3%;'>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/ori/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>
<table style='width: 100%;'>
	<thead>
		<tr>
			<th style="text-align: center">Ref(vocoder)</th>
			<th style="text-align: center">Styler</th>
			<th style="text-align: center">GenerSpeech</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/ref/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/styler/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/speech/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<table style='width: 100%;'>
	<thead>
		<tr>
      			<th style="text-align: center">YourTTS</th>
			<th style="text-align: center">MS RMSSinger</th>
			<th style="text-align: center">StyleSinger</th>
		</tr>
	</thead>
	<tbody>
		<tr>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/yourtts/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/rms/001.wav" type="audio/wav"></audio></td>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/styesinger/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

2.Reference/Target: 为春风吹落 AP SP AP 只是简简单单的爱过我还

global style class: alto sad

<table style='width: 33.3%;'>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/ori/002.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>
<table style='width: 100%;'>
	<thead>
		<tr>
			<th style="text-align: center">Ref(vocoder)</th>
			<th style="text-align: center">Styler</th>
			<th style="text-align: center">GenerSpeech</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/ref/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/styler/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/speech/002.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<table style='width: 100%;'>
	<thead>
		<tr>
      			<th style="text-align: center">YourTTS</th>
			<th style="text-align: center">MS RMSSinger</th>
			<th style="text-align: center">StyleSinger</th>
		</tr>
	</thead>
	<tbody>
		<tr>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/yourtts/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/rms/002.wav" type="audio/wav"></audio></td>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/styesinger/002.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

3.Reference/Target: 我还在逞强 AP 说着谎 AP 也没能力遮挡你去的方向

global style class: alto sad

<table style='width: 33.3%;'>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/ori/003.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>
<table style='width: 100%;'>
	<thead>
		<tr>
			<th style="text-align: center">Ref(vocoder)</th>
			<th style="text-align: center">Styler</th>
			<th style="text-align: center">GenerSpeech</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/ref/003.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/styler/003.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/speech/003.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<table style='width: 100%;'>
	<thead>
		<tr>
      			<th style="text-align: center">YourTTS</th>
			<th style="text-align: center">MS RMSSinger</th>
			<th style="text-align: center">StyleSinger</th>
		</tr>
	</thead>
	<tbody>
		<tr>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/yourtts/003.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/rms/003.wav" type="audio/wav"></audio></td>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/parallel/styesinger/003.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

# Non-Parallel Style Transfer Samples

In out-of-domain (OOD) scenarios, we utilize unseen reference audio with target notes and lyrics to synthesize the target singing voice. 

1.Reference: 风花雪月的诗句里我在年年的成长 AP

global style class: tenor happy

Effectively capturing the timbre, emotion, pitch transitions, vocal techniques, and delicate articulation skills.
<table style='width: 33.3%;'>
	<thead>
		<tr>
			<th style="text-align: center">Ref(vocoder)</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/ref/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

Target: 吹向我脸庞 AP 想起你轻柔的话语 AP 曾打湿我眼眶 AP
<table style='width: 100%;'>
	<thead>
		<tr>
			<th style="text-align: center">Styler</th>
			<th style="text-align: center">GenerSpeech</th>
      			<th style="text-align: center">YourTTS</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/styler/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/generspeech/001.wav" type="audio/wav"></audio></td>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/yourtts/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<table style='width: 66.7%;'>
	<thead>
		<tr>
			<th style="text-align: center">MS RMSSinger</th>
			<th style="text-align: center">StyleSinger</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/rmssinger/001.wav" type="audio/wav"></audio></td>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/stylesinger/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

2.Reference: 为春风吹落 AP SP AP 只是简简单单的爱过我还

global style class: alto sad

Successfully transferring the timbre, emotion, vocal techniques, and subtle elongation in articulation skills.
<table style='width: 33.3%;'>
	<thead>
		<tr>
			<th style="text-align: center">Ref(vocoder)</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/ref/002.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

Target: 幸福没有那么容易 AP 才会特别让人着迷 AP 什么都不懂的年纪 AP
<table style='width: 100%;'>
	<thead>
		<tr>
			<th style="text-align: center">Styler</th>
			<th style="text-align: center">GenerSpeech</th>
      			<th style="text-align: center">YourTTS</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/styler/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/generspeech/002.wav" type="audio/wav"></audio></td>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/yourtts/002.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<table style='width: 66.7%;'>
	<thead>
		<tr>
			<th style="text-align: center">MS RMSSinger</th>
			<th style="text-align: center">StyleSinger</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/rmssinger/002.wav" type="audio/wav"></audio></td>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/stylesinger/002.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

3.Reference: 圈圈圆圆圈圈天天年年天天的我深深看你的脸 AP 生气的温柔埋怨的温柔 SP

global style class: alto sad

Successfully transferring the timbre, emotion, vocal techniques, vibrato skill, and subtle elongation in articulation skill.
<table style='width: 33.3%;'>
	<thead>
		<tr>
			<th style="text-align: center">Ref(vocoder)</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/ref/003.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

Target: 修炼爱情的心酸 AP 学会放好以前的渴望 AP 我们那些信仰要忘记多难
<table style='width: 100%;'>
	<thead>
		<tr>
			<th style="text-align: center">Styler</th>
			<th style="text-align: center">GenerSpeech</th>
      			<th style="text-align: center">YourTTS</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/styler/003.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/generspeech/003.wav" type="audio/wav"></audio></td>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/yourtts/003.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<table style='width: 66.7%;'>
	<thead>
		<tr>
			<th style="text-align: center">MS RMSSinger</th>
			<th style="text-align: center">StyleSinger</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/rmssinger/003.wav" type="audio/wav"></audio></td>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/nonparallel/stylesinger/003.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


# Ablation Studies

We undertake ablation studies to showcase the efficacy of various designs incorporated within StyleSinger.
UMLN and RSA are the Uncertainty Modeling Layer Normalization and the Residual Style Adaptor, while Pitch and Decoder mean the pitch diffusion predictor and the diffusion decoder.
VQ means using VQ instead of RQ, and MSLN means using Mix-Style LN instead of UMLN.

1.Reference/Target: 而鲜血如红唇 AP 前朝记忆渡红尘 AP 伤人的不是刀刃 AP

global style class: alto sad

<table style='width: 33.3%;'>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation/ori/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<table style='width: 100%;'>
	<thead>
		<tr>
			<th style="text-align: center">Ref(vocoder)</th>
			<th style="text-align: center">StyleSinger</th>
			<th style="text-align: center">wo UMLN</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation/ref/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation/stylesinger/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation/wo umln/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<table style='width: 100%;'>
	<thead>
		<tr>
      			<th style="text-align: center">wo RSA</th>
			<th style="text-align: center">wo Pitch</th>
			<th style="text-align: center">wo Decoder</th>
		</tr>
	</thead>
	<tbody>
		<tr>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation/wo dsa/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation/wo ppdp/001.wav" type="audio/wav"></audio></td>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation/wo decoder/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<table style='width: 100%;'>
	<thead>
		<tr>
      			<th style="text-align: center">VQ</th>
			<th style="text-align: center">MSLN</th>
			<th style="text-align: center">MS RMSSinger</th>
		</tr>
	</thead>
	<tbody>
		<tr>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation/wo rq/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation/mix-layer/001.wav" type="audio/wav"></audio></td>
      			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation/rmssinger/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

