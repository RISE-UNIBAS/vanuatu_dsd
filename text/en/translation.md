### More detailed information about the translation process

We developed a systematic three-phase approach to make this vast German-language collection accessible in English too.

Firstly, in the **preparation phase**, we used Python scripts to analyze the original JSON dataset of 195,000+ records, running character encoding validation to identify and fix common issues with German umlauts (ä, ö, ü, ß) that often get corrupted during data migration. We then extracted 60 representative German-language descriptions for testing.

Secondly, in the **translation phase**, we built automated Python scripts that recursively traverse the JSON structure, identify text fields containing German content, and send them to the DeepL REST API for translation. The DeepL API was configured with specific parameters to maintain paragraph structure and line breaks, the neutral scholarly tone, and to ensure accurate language pair handling. Crucially, our scripts translate description fields, and all other metadata including object IDs, geographic coordinates, collector names, and provenance records remain untouched.

Thirdly, in the **validation phase**, we conducted blind A/B user testing through a custom Streamlit web application with SQLite database backend where 20 human evaluators reviewed side-by-side comparisons of DeepL versus Google Cloud Translation API outputs, with translation sources randomized and hidden to prevent bias. The results were stored in a structured database for statistical analysis, and DeepL demonstrated superior handling of complex ethnographic terminology and historical German phrasing.
