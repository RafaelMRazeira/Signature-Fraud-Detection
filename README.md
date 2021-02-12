# Signature Fraud Detection

## Description

The collection contains offline signature samples. The images were scanned at 600dpi resolution and cropped with a controlled image region where the signature verification is done.

The training dataset contains 209 images. The signatures comprise 9 reference signatures by the same writer “A” and 200 questioned signatures. The 200 questioned signatures comprise 76 genuine signatures written by the reference writer in his/her normal signature style; 104 simulated/forged signatures (written by 27 forgers freehand copying the signature characteristics of the reference writer); 20 disguised signatures written by the reference writer. The disguise process comprises an attempt by the reference writer to purposefully alter his/her signature to avoid being identified or for him/her to deny writing the signature. The simulation/forgery process comprises an attempt by a writer to imitate the reference signature characteristics of a genuine authentic author.

The testing dataset contains 125 signatures. The signatures comprise 25 reference signatures by the same writer “B” and 100 questioned signatures. The 100 questioned signatures comprise 3 genuine signatures written by the reference writer in his/her normal signature style; 90 simulated signatures (written by 34 forgers freehand copying the signature characteristics of the reference writer); 7 disguised signatures written by the reference writer. The testing dataset is NOT provided to the candidate but only used for the evaluation step (by the referee). So be creative to manipulate the providade data as best as possible.

All writings were made using the same make of ballpoint pen and using the same make of paper.

## Training Set

### Folder Structure and File Naming

The signatures of the training set are arranged according to the following folder structure:

- **Disguised:** Contains all the disguised signatures of specimen author ‘A’
- **Genuine:** Contains all the genuine signatures of specimen author ‘A’
- **Reference:** Contains the reference signatures of specimen author ‘A’ which can be used for training the classifiers for author ‘A’.
- **Simulated:** Contains all the skilled forgeries for specimen author ‘A’

Note that the naming convention also reveals the type of signature for the training set. For example, D023: disguised signatures, G003: a genuine signature, S001: a forged/simulated signature, and similarly R001: a reference signature. The signatures of the test set are arranged according to the following folder structure:

- **Reference:** Contains the reference signatures of another specimen author ‘B’. These signatures are used to train the classifier for verifying authorship of the specimen author ‘B’.
- **Questioned:** Contains all the signatures for which the task is to verify authorship of the specimen author ‘B’.

## Objective

The candidate should provide a classification method that correctly states whether a signature can be a fraud/genuine/disguised type.

## Run Solution

To run this solution please: 

1. Install the requirements.txt in python enviroment or not
2. Download the model via drive https://drive.google.com/file/d/1FVVMbf721iQXtA5gBgaR_G04kJLkEK_p/view
3. Run the script in command line using:
	- python3 Classify_Signatures.py -m Siamese_model_all_data.hdf5 -img image_path_to_classify 
		- The spected return is a print of type: "The class of this image is G"

		or

	- python3 Classify_Signatures.py -m Siamese_model_all_data.hdf5 -dir-img directory_path_to_classify_images
		- The spected return is a print of type: "The class of image IMG_PATH is D" for each image in folder
4. Attention: 
	- The directory_path_to_classify_images, has to be ONLY IMAGES to work well
	- The script was run it in Ubuntu 18.4.5 LST and with a 1050Ti GPU desktop
5. The model itself is the file "Siamese_model_all_data.hdf5" which is a only weights of a keras siamese model