
# Slide Stitching Exercise

## Learning Goals

  1) Python Packages: 
     - **pathlib**: https://github.com/chris1610/pbpython/blob/master/extras/Pathlib-Cheatsheet.pdf
     - **shutil**: https://docs.python.org/3/library/shutil.html
     - **tifffile**: ./notebooks/tutorials/read_tiff.ipynb
  
  2) Processes:
     - Extracting metadata from regularly-formatted filenames
     - Batch-processing files
     - File management in pipelines
     - Algorithm Discovery

## Background

A single slide containing four individual, stained mouse brain sections was imaged using a widefield scanner. The slide looks somthing like the following:

![Slide](./imgs/PW162-A06.jpg)

However, the whole slide can't be imaged all at once.  Instead, a robot scanner produces smaller image tiles of this slide, each of constant height and width, saving all of them into one folder, regardless of which section they belong to. As a result, we get a jigsaw-puzzle like set of image tiles to work with, rather than a complete image.

We want images of the brain sections.  How do we reconstruct the image for each section?


Create a program that:

  1) Copies or Symlinks the images into seperate folders, one for each brain section.  (e.g. data/proacessed/A, data/processed/B, etc)

     - The filenames contain metadata that will help with this.
    
     - Naming should happen consistently, with the first directory corresponding to the upper-left-most section, and proceeding left-to-right, top-to-bottom, ending with the lower-right-most section.

  2) Creates a merged section image file for a given section directory.


This program can take the form of a jupyter notebook, a function, or a command-line script.  Regardless of the programs form, it should be organized and easy to modify for other datasets.

## Technical Questions ("Can We / How Can We / How SHould We..." Questions) 

  1) How Do I Get the Data Onto My Computer?
  
  2) How Can We Check the Quality of These Files?  Can We Visualize, Browse the Images in Python?

  3) How Can We Extract the Tile's Position from these files?

  4) How Can we group same-section tiles?

  5) How Should We Implement The File Reorganization?
  
  6) How Can We Merge Multiple Large Files?


## General Questions

  1) Do I have the right data?

  2) Do I have all the data?  (For us, that means, "How many brain complete sections are in this dataset?")

  3) How are the sections in this dataset arranged on the slide?



# Useful Shell Terminal Snippets

## Get a clone of this repository on your computer

```
git clone <the url of this repository>
```

## Installing the Required Packages

```
pip install -r requirements
```

## Downloading the Data

```
dvc pull
```

### Question: How did you set up this dvc system?

Roughly the sequence used: 
```
dvc init  # Have DVC track the project as a repository
dvc add data/raw
git add .dvc data/raw.dvc
# Make a google drive folder, copy-past the folder's ID from the URL
dvc remote add -d gdrive gdrive://<folder-id>
dvc push
# git commit everything dvc-related that's not ignored.
```





# Acknowledgments

Many thanks to Dr. Johannes Kohl (https://www.kohl-lab.org/people) for providing the data and description for this kata!