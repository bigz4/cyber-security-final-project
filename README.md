# cyber-security-final-project

**Dataset Download**
* [https://www.kaggle.com/datasets/manmandes/malimg/data](https://www.kaggle.com/datasets/manmandes/malimg/data)
* [https://github.com/elastic/ember?tab=readme-ov-file](https://github.com/elastic/ember?tab=readme-ov-file)


**Fix for ember issues**
A way to fix it is to replace:
`entry_name_hashed = FeatureHasher(50, input_type="string").transform([raw_obj['entry']]).toarray()[0]` 
with:
`entry_name_hashed = FeatureHasher(50, input_type="string").transform([ [raw_obj['entry']] ]).toarray()[0]`

in features.py at line 192. In this way an iterable over iterable over raw features is obtained, as transform() method require.

[referenced github issue](https://github.com/elastic/ember/issues/103#issuecomment-1623975101)