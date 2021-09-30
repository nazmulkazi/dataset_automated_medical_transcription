[![DOI](https://zenodo.org/badge/313781881.svg)](https://zenodo.org/badge/latestdoi/313781881)

# Motivation

We generated this dataset to train a machine learning model for automatically generating psychiatric case notes from doctor-patient conversations. Since, we did have access to real doctor-patient conversations, we used transcripts from two different sources to generate audio recordings of enacted conversations between a doctor and a patient. We employed eight students who worked in pairs to generate these recordings. Six of the transcripts that we used to produce this recordings were hand-written by Cheryl Bristow and rest of the transcripts were adapted from Alexander Street which were generated from real doctor-patient conversations. Our study requires recording the doctor and the patient(s) in seperate channels which is the primary reason behind generating our own audio recordings of the conversations.  

We used Google Cloud Speech-To-Text API to transcribe the enacted recordings. These newly generated transcripts are auto-generated entirely using AI powered automatic speech recognition whereas the source transcripts are either hand-written or fine-tuned by human transcribers (transcripts from Alexander Street).  

We provided the generated transcripts back to the students and asked them to write case notes. The students worked independently using a software that we developed earlier for this purpose. The students had past experience of writing case notes and we let the students write case notes as they practiced without any training or instructions from us.

# Authors

- Kazi, Nazmul
- Kuntz, Matt
- Kanewala, Upulee
- Kahanda, Indika

# Contributors

- Bristow, Cheryl
- Arzubi, Eric

# Description of the dataset

## Case note categories:

| Index | Category                   | Abbr. |
| ----: | -------------------------- | ----- |
|     0 | Client Details             | CD    |
|     1 | Chief Complaint            | CC    |
|     2 | History of Present Illness | HPI   |
|     3 | Past Psychiatric History   | PPH   |
|     4 | History of Substance Use   | HSU   |
|     5 | Social History             | SH    |
|     6 | Family History             | FH    |
|     7 | Review of Systems          | RS    |

## Directories:

| Directory | Description |
| --- | --- |
| <code>transcripts/source</code> | Source transcripts that are used to generate the audio recordings. |
| <code>recordings</code> | Audio recordings of the enacted doctor-patient conversations. |
| <code>transcripts/transcribed</code> | Transcripts generated from the audio recordings using Google Cloud Speech-To-Text API. |
| <code>casenotes</code> | Casenotes written by the students, i.e. annotators. |

## Transcript file structure:

```
[
	{
		"speaker"  : 1,
		"dialogue" : ["sentence 1", "sentence 2", ...]
	},
	...
]
```

### Definitions

| Term | Definition |
| --- | --- |
| <code>speaker</code> | Speaker of the current dialogue turn. |
| <code>dialogue</code> | Sentence(s) spoken by the speaker in current dialogue turn. |

## Case note file structure:

```
[
	{
		"categoryId" : "0",
		"sourceId"   : "0",
		"formalText" : "formal text"
	},
	...
]
```

### Definitions

| Term | Definition |
| --- | --- |
| <code>categoryId</code> | Index of the case note category, e.g. 5 = Social History, to which this sentence is used. This property is zero-indexed. |
| <code>sourceId</code> | Index of the source sentence in the transcript. This property is zero-indexed. |
| <code>formalText</code> | Modified version of the sentence as it is used in the case note. |

**NOTE:** If a sentence is used in multiple casenote categories, a record will appear for each use. `"sourceId":"n"` refers to the sentence whose index is `n` in the whole transcript whereas multiple sentences can belong to the same dialogue turn. In the following transcript, `"sourceId":"3"` refers to `sentence_d`:

```json
[
	{
		"speaker"  : 1,
		"dialogue" : ["sentence_a", "sentence_b"]
	},
	{
		"speaker"  : 2,
		"dialogue" : ["sentence_c", "sentence_d",  "sentence_e"]
	}
]
```

## dataset.pickle

This is a pickle file (protocol version 4) containing all the transcribed transcripts and the casenotes for easy and quick access to the data using python.

# Alternative repository for audio recordings

The audio recordings are also available in [Oxiago Int.](https://oxiago.com/curavoice/dataset/10.5281.4279041/) website.

# Funding

This project is funded by [CATalyst Gap fund, Fall 2019.](https://www.montana.edu/news/19430/msu-office-of-research-economic-development-and-graduate-education-awards-funding-for-msu-inventions)

# Transcripts adapted from Alexander Street

[D0420-S2-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%5C%7Cbibliographic_details%5C%7C2559294#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559294) [D0420-S3-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2098620#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2098620) [D0420-S3-T03](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2559516#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559516) [D0420-S4-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2098612#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2098612) [D0420-S4-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2561394#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2561394) [D0421-S1-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2561887#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2561887) [D0421-S1-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2098556#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2098556) [D0421-S1-T03](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2560970#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2560970) [D0421-S1-T04](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2099870#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2099870) [D0421-S1-T05](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2562474#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2562474) [D0421-S2-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2098922#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2098922) [D0421-S2-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2559292#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559292) [D0421-S3-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2562370#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2562370) [D0421-S3-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2562642#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2562642) [D0421-S3-T03](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2562678#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2562678) [D0421-S3-T04](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2100046#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2100046) [D0421-S3-T05](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2562598#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2562598) [D0422-S1-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2098398#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2098398) [D0422-S1-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2559590#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559590) [D0422-S1-T03](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2559438#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559438) [D0422-S1-T04](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2562032#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2562032) [D0422-S2-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2562278#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2562278) [D0422-S2-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2547687#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2547687) [D0422-S3-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2560312#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2560312) [D0422-S3-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2562258#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2562258) [D0422-S3-T03](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2562028#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2562028) [D0422-S3-T04](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2098626#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2098626) [D0422-S3-T05](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2099848#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2099848) [D0422-S3-T06](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2098838#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2098838) [D0422-S4-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2098418#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2098418) [D0422-S4-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2098430#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2098430) [D0422-S4-T03](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2560586#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2560586) [D0422-S4-T04](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2086469#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2086469) [D0422-S4-T05](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2559642#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559642) [D0423-S1-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2561980#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2561980) [D0423-S1-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2559566#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559566) [D0423-S1-T03](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2560984#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2560984) [D0423-S2-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2098812#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2098812) [D0423-S2-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2100068#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2100068) [D0423-S2-T03](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2562638#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2562638) [D0424-S1-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2559776#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559776) [D0424-S1-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2559817#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559817) [D0424-S1-T03](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2559839#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559839) [D0424-S2-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2559444#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559444) [D0424-S2-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2560564#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2560564) [D0424-S2-T03](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2561578#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2561578) [D0424-S2-T04](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2098504#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2098504) [D0424-S2-T05](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2098464#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2098464) [D0424-S2-T06](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2562030#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2562030) [D0424-S3-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2560316#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2560316) [D0424-S3-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2099936#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2099936) [D0424-S3-T03](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2559843#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559843) [D0424-S3-T04](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2098840#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2098840) [D0425-S1-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2099846#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2099846) [D0425-S1-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2098814#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2098814) [D0425-S1-T03](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2559801#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559801) [D0425-S2-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2560566#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2560566) [D0425-S2-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2098610#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2098610) [D0425-S2-T03](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2559738#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559738) [D0425-S2-T04](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2562240#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2562240) [D0425-S3-T01](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2107339#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2107339) [D0425-S3-T02](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2086473#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2086473) [D0425-S3-T03](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2559807#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559807) [D0425-S3-T04](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2559831#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2559831) [D0425-S3-T05](https://search.alexanderstreet.com/view/work/bibliographic_entity%7Cbibliographic_details%7C2099894#page/1/mode/1/chapter/bibliographic_entity%7Cbibliographic_details%7C2099894)

# Disclaimer

This dataset is provided "As Is" without warranty of any kind. In no event shall the authors or copyright holders be liable for any claim, damages, or other liability. The source transcripts may not be enacted word-to-word as they appear in the transcript. Similarly, we used automatic speech recognition to transcribe the recordings and the transcribed transcripts may not match exactly as the words appear in the audio recordings.

[![DOI](https://zenodo.org/badge/313781881.svg)](https://zenodo.org/badge/latestdoi/313781881)

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
