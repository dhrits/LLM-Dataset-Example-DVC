This repository is meant to be a simple demonstration of how to use DVC to track versions of LLM datasets. In the case of this repository, we track the [SQuAD-It](https://github.com/crux82/squad-it/) dataset. We download the dataset via `download_data.ipynb` and save an HF dataset version to disk. Thereafter we use `dvc add` to add the dataset to the DVC cache.

The flow was as follows:
```
git init .
git add .dvc
git commit -m "Initial commit"
git push origin main
dvc add SQuAD_it*
dvc add squad_it_dataset.hf
git add .gitignore
git add *.dvc
git commit -m "Add SQuAD-It dataset to DVC"
git push origin main

# Add dvc remote (only needed once)
 dvc remote add -d storage s3://llm-finetune-data-dsagar/dvcstore
 dvc push
```
One of the has files can be viewed [here](https://llm-finetune-data-dsagar.s3.us-east-1.amazonaws.com/dvcstore/files/md5/f6/cdd6847ed104c2cd32d80980a652d4)