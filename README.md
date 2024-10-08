[![TESTS](https://github.com/VirtualPatientEngine/literatureSurvey/actions/workflows/tests.yml/badge.svg)](https://github.com/VirtualPatientEngine/literatureSurvey/actions/workflows/tests.yml)
[![RELEASE](https://github.com/VirtualPatientEngine/literatureSurvey/actions/workflows/release.yml/badge.svg)](https://github.com/VirtualPatientEngine/literatureSurvey/actions/workflows/release.yml)
[![mkdocs-deploy](https://github.com/VirtualPatientEngine/literatureSurvey/actions/workflows/mkdocs-deploy.yml/badge.svg)](https://github.com/VirtualPatientEngine/literatureSurvey/actions/workflows/mkdocs-deploy.yml)
[![pages-build-deployment](https://github.com/VirtualPatientEngine/literatureSurvey/actions/workflows/pages/pages-build-deployment/badge.svg)](https://github.com/VirtualPatientEngine/literatureSurvey/actions/workflows/pages/pages-build-deployment)

<h1 align="center" style="border-bottom: none;">🚀 Literature Survey</h1>

Welcome to Team VPE's Literature Survey Template Repository! 📚✨ This repository provides you with a quick setup to create your very own automated literature survey website using Semantic Scholar's [Recommendation API](https://api.semanticscholar.org/api-docs/recommendations), and provides an option to import the recommended articles to your [Zotero](https://www.zotero.org/) account.

### Types of Recommendations
Semantic Scholar provides 2 types of recommendations:

1. ```Single-paper recommendations```: Each article you provide will be used to generate recommendations specifically for that article.
2. ```List-based recommendations```: Up to 10 articles related to the topic will be selected as positive articles. Additional articles may be provided beyond this count but they shall not be considered to retrieve the recommendations. Negative articles will be selected by sampling the top N articles from other topics, ensuring that the total number of sampled articles is 10 and equal from each topic whenever possible. These positive and negative articles will be used to retrieve recommendations from Semantic Scholar.

### Example Usage
For demonstration purposes, this template repository uses some of the articles related to the simulator module of Team VPE as an example. You can easily customize it to your own fields of interest by following the steps outlined below. To see how the automated literature survey repo looks like, visit this [link](https://virtualpatientengine.github.io/literatureSurvey).

Let's dive in and set up your own literature survey adventure!

### Getting Started
Follow these simple steps to set up your literature survey website:

1. Click on the ```Use this template``` button to create your own repository based on this template. If you would like to access your repository via URL, please make created repository public.

2. Open up the ```app/data/query.tsv``` file in your favorite code editor or Excel.

3. Under the `Title` column, give titles to your topics. Under the `Use` column, write <kbd>1</kbd> if you want to use the article for recommendations or <kbd>0</kbd> if you just want to display the article. **Under the URL column, specify the corresponding URLs to [Semantic Scholar](https://www.semanticscholar.org/) article.** Submit your edited file by clicking on `Commit changes...`. In the `Commit message` add a prefix by using one of these keywords **feat:, fix: or chore:**, e.g., "feat: added one paper". After committing changes to the `main` branch directly, the workflows should start automatically.

4. (Optional) Create a venv:
```
> python -m venv env
# On Windows
> .\env\Scripts\activate

# On macOS and Linux
> source env/bin/activate
```

5. (Optional) Install all the necessary requirements:
```
> pip3 install -r requirements.txt
```

6. (Optional) It's time to fetch some literature! Run the ```literature_fetch_recommendation_api.py``` script to grab the recommended articles from Semantic Scholar:
```
> cd app/code
> python3 literature_fetch_recommendation_api.py
```

7. (Optional) Now, fire up MkDocs locally to view the recommended articles:
```
> mkdocs serve
```
Head over to the localhost link that pops up in your terminal. 

8. This repository includes a `mkdocs-deploy.yml` [workflow](https://github.com/VirtualPatientEngine/literatureSurvey/blob/main/.github/workflows/mkdocs-deploy.yml) that uses GitHub Actions to automatically execute the specified script **once a week** and deploy the literature survey system as a [GitHub Pages website](https://virtualpatientengine.github.io/literatureSurvey/). Feel free to edit to based on your project needs or use it as it is.

> To host your literature survey system online, you must place the YML file in the `.github/workflows/` folder. Once you have pushed you code to GitHub, under the [Actions](https://github.com/VirtualPatientEngine/literatureSurvey/actions) tab, you'll find the ongoing `mkdocs-deploy.yml` workflow (this might take even 1h or more depending on the current workload of compute servers and length of the publication list). Once this workflow finishes, head over to the [Settings/Pages](https://github.com/VirtualPatientEngine/literatureSurvey/settings/pages) tab. From there, choose `Deploy from a branch` in the Source section. Under the Branch subsection, select `gh-pages` and root from the dropdown menus, then click `Save`.

9. Under `About` section of your repository, head to the gear symbol and check the box `Use your GitHub Pages website` and `Save changes`. You will see an URL to your literature survey repository under `About` section of the `Code` tab. 

10. Change <kbd>site_url</kbd>, <kbd>theme:/logo:</kbd>, <kbd>repo_url</kbd>, and <kbd>repo_name</kbd> in ```base.yml``` to the values related to your project.

11. If you'd like to edit the home page of the website, head over to `docs/index.md` to make the changes.

12. (Optional) Edit custom.css if you'd like to change the styling of web pages.

### Zotero Plugin
If you'd like to read the recommended articles in your Zotero Account:
1. Create an account with Zotero
2. Under the `Settings` tab in your GitHub repo, click on `Secrets and variables`, and select `Actions`
3. Set the following `Repository secrets`:
    - `ZOTERO_API_KEY` as Zotero API key (you can get it [here](https://www.zotero.org/settings/keys/new))
    - `LIBRARY_ID` as your group ID (this can be found by opening the group's page: https://www.zotero.org/groups/groupname , and hovering over the group settings link. The ID is the integer after /groups/)
    - `TEST_COLLECTION_KEY` as your collection's key (enter `https://api.zotero.org/groups/<LIBRARY_ID>/collections?key=<ZOTERO_API_KEY>` in your browser to view all the collections in your group; choose the key of the collection in which you'd like the recommended articles to be sotred)
4. The changes take effect only when the code is re-run. This can happen either the next time the code is scheduled for a run (Mondays) or under the `Actions` tab, select `mkdocs-deploy` from the left panel, and click on `Run workflow`.

### Bugs? Feature Requests?
If you encounter any bugs or have brilliant ideas for new features, please head over to the [Issues](https://github.com/VirtualPatientEngine/literatureSurvey/issues) and let us know.

### Happy surveying! 📖🔍
