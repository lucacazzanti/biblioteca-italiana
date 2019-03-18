
# Book Cover Text Processing
## Contributors : Vamsy Atluri, Ryan Bald, Sayli Dighde and Srinivas Kondepudi
### University of Washington Data Science Masters Capstone Project - Winter 2019

### Requirements

* python>=3.6.5
* tqdm==4.28.1
* fpdf==1.7.2
* setuptools==39.1.0
* opencv_contrib_python==4.0.0.21
* requests==2.18.4
* pandas==0.23.0
* Wand==0.5.0
* matplotlib==2.2.2
* numpy==1.14.3
* beautifulsoup4==4.7.1
* scikit_learn==0.20.3

For convenience these have also been listed in the 'requirements.txt' file. These can be installed directly using ```pip install -r requirements.txt```.

### Project Motivation

Biblioteca Italiana Seattle (BIS), an Italian library in Seattle is missing cover images for some books in its digital catalog. The current process is to manually search and pick the right cover images through photographs of book covers. The aim of our project is to make this process more efficient. 

More specifically, our proposed deliverable is a pipeline that extracts the words on a cover image enabling BIS to search for the right one more quickly by typing in the title and author of a book.

### Data Sources

* For the character extraction model, we generated a set of cover pages (.jpegs) using a combination of Italian authors, titles, font styles and font sizes to mimic real life pages.
* For the character prediction model, we used two data sources:
* a. handwritten letters from the EMNIST dataset.
* b. printed letters of varying fonts and emphases from the Chars74K dataset.

### Approach

* Firstly Computer Vision techniques are used to preprocess the cover image and identify prominent characters.
* Bounding boxes are drawn around these characters which are then cropped.
* A character prediction CNN model predicts the most likely letter for each cropped image.
* The predicted strings are passed through a word segmentation model to get a list of most likely words.

### Code Organization in this Repository

There were so many different techniques we used over the course of this project, that we felt the best way to both implement and document them was to use different notebooks for each step instead of putting everything in a single giant notebook or code file. 

*The notebooks are numbered in the order of intended execution.*

1. The first two modules -- **1_Optional_Cover_Page_Generation.ipynb** and **2_Optional_PDF_to_JPEG.ipynb**, as the names suggest are optional for the purposes of recreating the pipeline. 
    * Both of these modules were used by the team to generate data.
    * A subset of 100 pdfs and jpegs generated by these modules is hosted in the **Data/sample_pdfs** and **Data/sample_jpegs** folders respectively. 
    * Unless more data is required, *executing these steps is not necessary.*
2. The third module -- **3_Character_Extraction.ipynb** is where individual characters are extracted from sample book title images.
    * The inputs for this module are 2 images -- x.jpg and y.jpg, both stored in **Data/demo_cover_images**. 
    * The outputs generated here are the cropped characters extracted from both these inputs. 
    * Outputs for each page are stored in their respective sub-folders in the **Data/demo_extracted_chracters** folder.
3. The fourth module ----TO BE ADDED-----
4. The final module -- "5_Word_Segmentation.ipynb" takes the strings generated in the previous step and gives a list of most likely words as output. 
    * The model has been trained on a corpus of 10k Italian words which is stored in the './Data/italian_corpora' folder. 
    * This folder also has additional corpora which can be used as well to see the difference in results.

### Instructions to Reproduce Results

This section is a general outline on how to execute the text processing pipeline. More detailed instructions and explanations are included as comments in each individual notebook.

1. **NOTEBOOK 3**
    * Change the source image path.
    * Change the destination folder path.
    * Run all cells (-- we have included two demos in this notebook, running the set of commands once is sufficient).
    * Characters from the image will be extracted to the folder specified.
2. **NOTEBOOK 4**
    * Change the source to the folder 
    * and destination directory paths in notebook 4 and execute. -------EDIT---This will generate the output of predicted letters by line in the chosen folder.--------
3. Change the source file path and destination folder path for module 5. This will generate the output of predicted words as a '.txt' file in the chosen folder. This is the final output.


### Model Pipeline

A picture of the entire pipeline at a glance can be seen in the image below:

![Model Pipeline](./Project_Poster.jpg)

### Conclusion

While we did not achieve all the targets we set out for and are not completely satisfied with the results, we have set in place a pipeline that can be built on and improved. Our key takeaway would be the experience gained from working in the areas of Computer Vision, Neural Networks and NLP, especially considering our team had little exposure to these fields before the project.

### References

* [Peter Norvig’s NLP guide](https://techdevguide.withgoogle.com/resources/peter-norvigs-statistical-nlp/) 
* [OpenCV Documentation](https://docs.opencv.org/2.4/modules/refman.html)
* [Software Carpentry Blogs](https://software-carpentry.org/blog/) 
* [The Chars74K image dataset](https://docs.opencv.org/3.0-beta/modules/datasets/doc/datasets/tr_chars.html)
* [The EMNIST Dataset](https://www.nist.gov/itl/iad/image-group/emnist-dataset)
* [Tensorflow Documentation](https://www.tensorflow.org/api_docs)
