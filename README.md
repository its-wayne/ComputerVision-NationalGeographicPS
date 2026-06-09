# 🤝 PROJECT CONTRIBUTORS:

I want to start off by crediting all of the contributors of this project: 
<br>
* **Sean Li** – [@seanli05](https://github.com/seanli05)
* **Ming Shen** – [@miingsh](https://github.com/miingsh)
* **Luis Flores** – [@LuisF1238](https://github.com/LuisF1238)
* **Lauren Henderson** – [@LaurenMaiH](https://github.com/LaurenMaiH)
* **Waynstan Aung** – [@its-wayne](https://github.com/its-wayne)
<br>
Thank you all for making this happen! :)
## 🌊 Project Overview: 
This completed project was developed in collaboration with the National Geographic Pristine Seas initiative to revolutionize how marine biodiversity is assessed. The Pristine Seas research team collects extensive deep-sea video footage—using baited underwater video systems, drop cameras, and submersibles—which traditionally required hours of manual review by researchers to document organisms.
<br>
By applying machine learning and data science principles, we were able to engineer an automated, unsupervised computer vision pipeline that processes raw underwater footage, detects marine life, and clusters visually similar species together. This system drastically reduces the time scientists spend on manual annotation while simultaneously extracting quantitative taxonomic data, such as identifying the maximum number of a given species observed in a single frame (MaxN).

## 🛠️ Technical Workflow & Architecture
To address the unique challenges of underwater computer vision and the sheer volume of expedition footage, we split the architecture into an autonomous background pipeline and a researcher-driven clustering interface:

1. Autonomous Overnight Pipeline (Detection, Extraction & Embedding)
Designed to run overnight on entire mission datasets, this fully autonomous phase handles the heavy lifting of video processing:
<br>
Detection & Tracking: We utilized YOLO-World for robust, zero-shot object detection of pelagic taxa, paired with ByteTrack to maintain accurate, persistent tracking of individual organisms across sequential video frames. We also applied preprocessing techniques like CLAHE and Median Blurring to normalize murky deep-sea lighting.
<br>
Segmentation & Feature Embedding: We integrated BiRefNet for highly accurate background removal and boundary segmentation of the detected marine life. Following extraction, BioClip was used to generate rich, biologically relevant visual embeddings from the cropped images.

2. Sequential Clustering & Manual Refinement
While the feature extraction is autonomous, the final clustering workflow is manual to ensure scientific accuracy:
<br>
Sequential Clustering Scheme: To group these crop extractions into species, we implemented a sequential scheme that builds clusters off of sequential videos. This temporal context significantly improves the baseline accuracy of the groupings.
<br>
Interactive Frontend Interface: To put the final control in the hands of the researchers, we designed an intuitive web application using React and Tailwind CSS. This UI allowed scientists to review the sequential clusters, empowering them to edit, create, or remove clusters at their will.

## Project Demo Video: 
https://drive.google.com/file/d/1Aem_o-zYZ28ES1braV6HydOA8ZkIuO_J/view?usp=sharing