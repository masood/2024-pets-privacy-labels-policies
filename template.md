# Artifact Appendix

Paper title: **Honesty is the Best Policy: On the Accuracy of Apple Privacy Labels Compared to Apps' Privacy Policies**

Artifacts HotCRP Id: **#3**

Requested Badge: **Reproducible**

## Description

This artifact contains all of the code and dataset used in our paper to collect and evaluate privacy labels and privacy policies of apps on the Apple App Store.

Our artifacts facilitates:

- Gathering metadata, including privacy labels, for apps on the Apple App Store.
- Crawling and parsing the text contents of privacy policies.
- Classifying privacy policies to identify declared data collection practices.
- Creating App Store-like privacy labels based on privacy policies.
- Evaluating if a privacy policy is similar to a popular privacy policy template.

### Security/Privacy Issues and Ethical Concerns

While the artifact demos themselves do not crawl the entire Apple App Store, the crawl that we performed for the paper used exponential backoffs while sending requests to the App Store’s APIs.  

## Basic Requirements

---

### Hardware Requirements

The classification models require the use of a GPU. We provide Google Colab links for code that requires GPU access.

To run a notebook using a GPU in Google Colab, from the menu options at the top of the tab, choose `Runtime > Change runtime type`. In the resulting pop-up, choose `T4 GPU`  as the Hardware accelerator and click Save.

### Software Requirements

We primarily performed our evaluation on an Ubuntu 22.04 VM. Our code depends on various Python libraries which we import using pip. The notebooks in our artifact include commands within cells to download and import required libraries.

### Estimated Time and Storage Consumption

Our overall crawl, classification, and analysis can be quite lengthy to fully replicate, but the demos describe use cases which facilitate a quick evaluation.

- Time: Around 45m for a quick evaluation using Colab notebooks.
- Storage: Around 4GB of storage considering models and dataset CSV files.

## Environment

---

### Accessibility

Our artifact is accessible through this GitHub repository: https://github.com/masood/2024-pets-privacy-labels-policies.
While pre-trained models and datasets are stored as large files on HuggingFace, we provide code to download these files within the demo notebooks.

### Set up the environment
Click on the `Open in Colab` button at the top of each `ipynb` file to run the code within Google Colab.

## Artifact Evaluation

### Main Results and Claims / Experiments

List all your paper's main results and claims that are supported by your submitted artifacts.

### Main Result 1: Metadata and Privacy Labels of Apps on the Apple App Store

We referred to the sitemap of the Apple App Store to gather a list of app URLs.
For each app URL, we visit the page and parse its contents to gather metadata about the app.
We then send requests to Apple's API to gather details about the privacy labels associated with the app.
Our artifact provides a demo of gathering the metadata of an app, given its URL. (`app-store-crawl.ipynb`)

### Main Result 2: Privacy Policy Crawl and Classify

We developed a framework that considers the text of a privacy policy as individual segments and infers data collection practices declared within these segments.
We then translate these machine-learning-based inferences into equivalent privacy labels.
Our artifact provides a demo of gathering a privacy policy based on its URL, and demonstrates using our BERT-based models to classify practices (and privacy labels) from text segments. (`policy_crawl.ipynb`) 

### Main Result 3: Template Matching

We collected the text of 15 popular privacy policy templates.
We used a Cosine-similarity approach to detect if the text of a given privacy policy is similar to one of the popular templates.
Our artifact provides a demo of gathering the text of a privacy policy, converting the text into word vectors, and comparing these vectors against templates. (`template_detection.ipynb`)

### Main Result 3: Dataset of Crawled Apps and Privacy Policies

Our paper discusses the collection of (i) App Store Metadata, (ii) Collection of Privacy Policies, (iii) Classification of Policies, (iv) Creation of Policy-based Privacy Labels, and (v) Comparison of App Store Labels and Privacy Policy-based Labels.
We provide the data associated with our crawl and classifier results from January 2024, and we provide demo code for accessing and parsing the data that we share. (`dataset.ipynb`)

...

### Experiments

#### Experiment 1: App Store Crawl

We provide a notebook (`app-store-crawl.ipynb`) which demonstrates the collection of the metadata and privacy label for an app on the App Store.
We estimate the notebook to run from scratch in around 2 minutes.

#### Experiment 2: Privacy Policy Crawl and Classification

We provide a demo in a notebook (`policy_crawl.ipynb`) which demonstrated the collection and classification of a privacy policy.
The demo downloads trained BERT models from HuggingFace, which can take around 4GB of space. However, the notebook downloads the model files to a temporary folder (in around 5-10 minutes), and the storage will be within resource limits enforced by Google Colab.
We estimate evaluating the notebook to take around 15-20 minutes.

#### Experiment 3: Template Matching

We provide a demo in a notebook (`template_detection.ipynb`) that compares an example privacy policy against the templates we used in our evaluation.
The notebook downloads templates from the same GitHub repository associated with our artifact.
We estimate evaluating the demo notebook to take around 10 minutes.

#### Experiment 4: Dataset

We provide a demo notebook (`dataset.ipynb`) that demonstrates accessing and downloading the App Store and Privacy Policy data (from crawls in Jan 2024).
The notebook downloads the data from HuggingFace.
We show example code to parse the downloaded data and to generate comparison figures (e.g., Privacy Types [Fig. 4], Purposes [Fig. 5]) similar to those we include in our paper.

---