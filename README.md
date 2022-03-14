# Evaluating Gender Bias in Machine Translation

This repo contains code and data for reproducing the experiments in [Evaluating Gender Bias in Machine Translation](https://arxiv.org/abs/1906.00591) [Gabriel Stanovsky](https://gabrielstanovsky.github.io/), [Noah A. Smith](https://homes.cs.washington.edu/~nasmith/), and [Luke Zettlemoyer](https://www.cs.washington.edu/people/faculty/lsz), (ACL 2019), and [Gender Coreference and Bias Evaluation at WMT 2020](https://arxiv.org/pdf/2010.06018.pdf), Tom Kocmi, Tomasz Limisiewicz, Gabriel Stanovsky (WMT2020).

## Citing

```
@InProceedings{Stanovsky2019ACL,
  author    = {Gabriel Stanovsky and Noah A. Smith and Luke Zettlemoyer},
  title     = {Evaluating Gender Bias in Machine Translation},
  booktitle = {ACL},
  month     = {June},
  year      = {2019},
  address   = {Florence, Italy},
  publisher = {Association for Computational Linguistics}
}
```

## Requirements
See and install package in requirements.txt

## Install
`./install.sh`

## Set Up
To use this projet, you need to export translator's Api key :

`export AWS_DEFAULT_REGION=eu-west-3`

`export FAST_ALIGN_BASE=/path/to/fast_align`

`export AWS_SECRET_ACCESS_KEY=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

`export AWS_ACCESS_KEY_ID=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

`export GOOGLE_APPLICATION_CREDENTIALS="/path/to/your_json_google_file"`

`export BING_TRANSLATOR_TEXT_KEY=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

`export SYSTRAN_TRANSLATOR_API_KEY=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`


## Running our experiments 
This is the entry point for all our experiments: [scripts/evaluate_all_languages.sh](scripts/evaluate_all_languages.sh).
Run all of the following from the  `src` folder. Output logs will be written to the given
path.
* For the general gender accuracy number, run:

        ../scripts/evaluate_all_languages.sh ../data/aggregates/en.txt  path/to/output/folder/
        
        Our results are in the Resultats folder

* For evaluating *pro*-sterotypical translations, run:

        ../scripts/evaluate_all_languages.sh ../data/aggregates/en_pro.txt  path/to/output/folder/
        
        Our results are in the Pro_stero folder

* For evaluating *anti*-sterotypical translations, run:

        ../scripts/evaluate_all_languages.sh ../data/aggregates/en_anti.txt  path/to/output/folder/
        
        Our results are in the Anti_stero folder
        
* For SYSTRAN translator we created our python file to communicate with the API. This file WAS NOT in the original repo `https://github.com/gabrielStanovsky/mt_gender`.

* In this experiment, we do not have result for SOTA translator.

* If you want to run again the experiment, you can delete Resultats, Pro_stero, Anti_stero folders
## Adding an MT system
1. Translate the file in `data/aggregates/en.txt` to the languages in our evaluation method.
2. Put the transalations in `translations/your-mt-system/en-targetLanguage.txt` where each sentence is in a new line, which has the following format `original-sentence ||| translated sentence`. See [this file](translations/aws/en-fr.txt) for an example.
3. Add your translator in the `mt_systems` enumeration in the [evaluation script](scripts/evaluate_all_languages.sh).

