# SüperGLUE Görevleri
Bir görev, eğitilmiş bir model oluşturmak için bir ön eğitim görevi olabilir. Aynı görev, başka bir model için ince ayar yapacak bir aşağı akış görevi olabilir. Ancak, SüperGLUE'nin amacı, belirli bir NLU modelinin ince ayar yaparak birden fazla aşağı akış görevini gerçekleştirebileceğini göstermektir. Çoklu görev modelleri, transformerların düşünme gücünü kanıtlayan modellerdir. Herhangi bir transformerın gücü, önceden eğitilmiş bir model kullanarak birden fazla görevi gerçekleştirebilme ve daha sonra ince ayarlanmış aşağı akış görevlerine uygulayabilme yeteneğinde yatmaktadır.

# BoolQ Görevi
BoolQ, bir Boolean evet veya hayır cevabı görevi olan bir görevdir. SüperGLUE'de tanımlandığı gibi veri seti, 15.942 doğal olarak oluşan örnek içermektedir. `train.jsonl` veri setinin 3. satırının ham örneği, bir pasaj, bir soru ve cevabı (true) içerir:
```json
{
  "question": "is windows movie maker part of windows essentials",
  "passage": "Windows Movie Maker -- Windows Movie Maker (formerly known as Windows Live Movie Maker in Windows 7) is a discontinued video editing software by Microsoft. It is a part of Windows Essentials software suite and offers the ability to create and edit videos as well as to publish them on OneDrive, Facebook, Vimeo, YouTube, and Flickr.",
  "idx": 2,
  "label": true
}
```
Verilen veri setleri zamanla değişebilir, ancak kavramlar aynı kalır.

# Commitment Bank (CB) Görevi
Commitment Bank (CB), zor bir entailment görevidir. Transformer modelinden bir önerme okuması ve daha sonra önermeye dayalı bir hipotez incelemesi istenir. Örneğin, hipotez önermeyi onaylayabilir veya çelişebilir. Daha sonra, transformer modeli hipotezi nötr, bir entailment veya önermenin çelişkisi olarak etiketlemelidir. Veri seti doğal söylemler içerir. `train.jsonl` eğitim veri setinden alınan #77 örneği, CB görevinin ne kadar zor olduğunu gösterir:
```json
{
  "premise": "The Susweca. It means ''dragonfly'' in Sioux, you know. Did I ever tell you that's where Paul and I met?",
  "hypothesis": "Susweca is where she and Paul met",
  "label": "entailment",
  "idx": 77
}
```

# Multi-Sentence Reading Comprehension (MultiRC) Görevi
Multi-Sentence Reading Comprehension (MultiRC), modelden bir metin okumasını ve birkaç olası seçimden seçim yapmasını ister. Görev hem insanlar hem de makineler için zordur. Modele bir metin, birkaç soru ve her soruya olası cevaplar 0 (yanlış) veya 1 (doğru) etiketi ile sunulur. `train.jsonl`'den alınan ikinci örnek:
```json
{
  "text": "The rally took place on October 17, the shooting on February 29. Again, standard filmmaking techniques are interpreted as smooth distortion: \"Moore works by depriving you of context and guiding your mind to fill the vacuum -- with completely false ideas. It is brilliantly, if unethically, done.\" As noted above, the \"from my cold dead hands\" part is simply Moore's way to introduce Heston. Did anyone but Moore's critics view it as anything else? He certainly does not \"attribute it to a speech where it was not uttered\" and, as noted above, doing so twice would make no sense whatsoever if Moore was the mastermind deceiver that his critics claim he is. Concerning the Georgetown Hoya interview where Heston was asked about Rolland, you write: \"There is no indication that [Heston] recognized Kayla Rolland's case.\" This is naive to the extreme -- Heston would not be president of the NRA if he was not kept up to date on the most prominent cases of gun violence. Even if he did not respond to that part of the interview, he certainly knew about the case at that point. Regarding the NRA website excerpt about the case and the highlighting of the phrase \"48 hours after Kayla Rolland is pronounced dead\": This is one valid criticism, but far from the deliberate distortion you make it out to be; rather, it is an example for how the facts can sometimes be easy to miss with Moore's fast pace editing. The reason the sentence is highlighted is not to deceive the viewer into believing that Heston hurried to Flint to immediately hold a rally there (as will become quite obvious), but simply to highlight the first mention of the name \"Kayla Rolland\" in the text, which is in this paragraph.",
  "question": "When was Kayla Rolland shot?",
  "answers": [
    {"text": "February 17", "idx": 168, "label": 0},
    {"text": "February 29", "idx": 169, "label": 1},
    {"text": "October 29", "idx": 170, "label": 0},
    {"text": "October 17", "idx": 171, "label": 0},
    {"text": "February 17", "idx": 172, "label": 0}
  ],
  "idx": 26
}
```

# Reading Comprehension with Commonsense Reasoning Dataset (ReCoRD) Görevi
ReCoRD, bir başka zorlu görevdir. Veri seti, 70.000'den fazla haber makalesinden 120.000'den fazla sorgu içermektedir. Transformer, bu problemi çözmek için ortak akıl yürütme kullanmalıdır. `train.jsonl`'den alınan bir örnek:
```json
{
  "source": "Daily mail",
  "passage": {
    "text": "A Peruvian tribe once revered by the Inca's for their fierce hunting skills and formidable warriors are clinging on to their traditional existence in the coca growing valleys of South America, sharing their land with drug traffickers, rebels and illegal loggers. Ashaninka Indians are the largest group of indigenous people in the mountainous nation's Amazon region, but their settlements are so sparse that they now make up less than one per cent of Peru's 30 million population. Ever since they battled rival tribes for territory and food during native rule in the rainforests of South America, the Ashaninka have rarely known peace.\n@highlight\nThe Ashaninka tribe once shared the Amazon with the like of the Incas hundreds of years ago\n@highlight\nThey have been forced to share their land after years of conflict forced rebels and drug dealers into the forest\n@highlight\n. Despite settling in valleys rich with valuable coca, they live a poor pre-industrial existence",
    "entities": [{"start": 2, "end": 9}, ..., {"start": 711, "end": 715}]
  },
  "query": "Innocence of youth: Many of the @placeholder's younger generations have turned their backs on tribal life and moved to the cities where living conditions are better",
  "answers": [{"start": 263, "end": 271, "text": "Ashaninka"}, {"start": 601, "end": 609, "text": "Ashaninka"}, {"start": 651, "end": 659, "text": "Ashaninka"}],
  "idx": 9
}
```

# Recognizing Textual Entailment (RTE) Görevi
RTE için, transformer modeli önermeyi okumalı, hipotezi incelemeli ve entailment hipotez durumunun etiketini tahmin etmelidir. `train.jsonl` veri setinden alınan #19 örneği:
```json
{
  "premise": "U.S. crude settled $1.32 lower at $42.83 a barrel.",
  "hypothesis": "Crude the light American lowered to the closing 1.32 dollars, to 42.83 dollars the barrel.",
  "label": "not_entailment",
  "idx": 19
}
```

# Words in Context (WiC) Görevi
WiC, bir kelimenin anlamını iki farklı cümlede analiz etmeyi gerektirir. `train.jsonl` veri setinden alınan ilk örnek:
```json
{
  "word": "place",
  "sentence1": "Do you want to come over to my place later?",
  "sentence2": "A political system with no place for the less prominent groups.",
  "idx": 0,
  "label": false,
  "start1": 31,
  "start2": 27,
  "end1": 36,
  "end2": 32
}
```

# The Winograd Schema Challenge (WSC) Görevi
WSC, bir transformer modelinin bir cümlede bir zamirin neye atıfta bulunduğunu belirlemesini gerektirir. `train.jsonl` veri setinden alınan bir örnek:
```json
{
  "text": "I poured water from the bottle into the cup until it was full.",
  "target": {"span2_index": 10, "span1_index": 7, "span1_text": "the cup", "span2_text": "it"},
  "idx": 4,
  "label": true
}
```

---

