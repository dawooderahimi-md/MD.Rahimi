# Online release checklist: Deployability Access

## 1. Prepare the local folder

Confirm that the folder contains the final versions of:

- `DA_complete_colab_perspective.ipynb`
- `README.md` (use the corrected README supplied with this checklist)
- `TableS1a_connectivity_W.csv`
- `TableS1b_tau_theta.csv`
- `CITATION.cff`
- the licence file(s) you have decided to use

Run the notebook from a clean session, inspect all 13 code checks, confirm the selected input source in `Table2_parameters.csv` and `MANIFEST.json`, and inspect the generated figures and tables. Download `DA_outputs.zip` and preserve a copy. Do not make claims about a successful validation run until you have performed it.

## 2. Create the GitHub repository

1. Sign in to GitHub and create a new repository, for example `deployability-access-cmd`.
2. Make it **Public** if you want the normal GitHub–Zenodo DOI workflow.
3. Upload the notebook, both CSVs, corrected `README.md`, `CITATION.cff`, and the finalized licence file(s). Add generated outputs only after checking them; a separate release attachment is also possible.
4. Check that the public notebook and both CSV files open from the repository and that no private files, tokens, or unrelated personal data were included.
5. Copy the repository URL and replace the repository placeholder in the README. Add the `repository-code` field to `CITATION.cff` using that URL.

GitHub’s official instructions for uploading files through the website are here: https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository

## 3. Create a versioned release

1. In GitHub, create a release named `v1.0.0` after the files and notebook have passed your checks.
2. Use release notes to state what is included, the notebook revision, and any known limitations.
3. Avoid changing the contents after tagging without creating a new version.

## 4. Archive the release with Zenodo and obtain a DOI

1. Sign in at Zenodo using your GitHub account, or link the accounts through Zenodo’s Linked accounts settings.
2. Open Zenodo’s GitHub integration and enable the public repository; use **Sync now** if the repository does not appear.
3. Once enabled, a new GitHub release is ingested and archived by Zenodo. Check the record metadata and the list of files before treating the deposit as complete.
4. Copy the **version-specific DOI** from the resulting Zenodo record. Update the repository README, `CITATION.cff`, manuscript Data Availability Statement, and any repository badges with that DOI. Keep the DOI for the exact version used in the paper; the concept DOI can be cited when referring to the project across versions.
5. Check that the public Zenodo record opens and that it contains the intended source files and, if included, the verified output archive.

Official documentation: https://help.zenodo.org/docs/github/enable-repository/ and https://docs.github.com/en/repositories/archiving-a-github-repository/referencing-and-citing-content

## Important limitation

This checklist prepares the release workflow; it does not upload files or create a GitHub account, Zenodo record, or DOI on your behalf. The current local Windows paths are accessible only on your computer. To audit the actual implementation rather than the README alone, upload the notebook and the two CSV files into the chat or make the repository available at its public URL.
