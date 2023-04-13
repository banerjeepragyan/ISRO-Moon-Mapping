# THE CHANDRAYAAN MOON MAPPING CHALLENGE 

Amongst the eight payloads that the Chandrayaan-2 Orbiter carries, it carries some imaging payloads too. We use them and the abilities of machine learning and artificial intelligence to create a high-resolution map of the moon.

## Important Files and Folders

HAT folder consists of the super-resolution model.

super_resolved_images consists of pre-existing lower resolution and higher resolution images, which we've upscaled by our model.

submission.ipynb consists of an inference notebook which would take in a tmc and super-resolve it 16x.

Project overview:
	submission.ipynb will take TMC image present in .tif format from 'tmc_input' folder. TMC .tif file will be broken into .png patches of size 16x16 all of which will be super-resolved by our HAT-L model trained from scratch. The upscaled images along with the original .tif data will be used to create the upscaled .tif data which will be found in 'upscaled_output' folder. Once upscaled .tif files are available, place them in 'ATLAS FOLDER' and run 'atlas/atlas.ipynb' which will stitch and create an atlas.

How to run submission.ipynb:
	- Download the following python dependencies, preferably in a conda environment:
		- patchify
		- unpatchify
		- matplotlib
		- numpy
		- cv2
		- PIL
		- skimage
		- gdal
		- BeautifulSoup4
	- Open https://drive.google.com/drive/folders/14xCeZjR1H3LIC7r2LT0nqC1sBFD9nICP?usp=sharing
	- Download model weights 'net_g_20000.pth', put it in the folder alongside submission.ipynb.
	- Open HAT directory in terminal and run the following commands
		- pip install -r requirements.txt
		- python setup.py develop
		- mv /content/HAT/options/test/HAT-L_SRx4_ImageNet-pretrain.yml /content/HAT/options/test/HAT-L_SRx16_config.yml
	- Put the input .tif file and .xml file in the tmc_input folder. Make sure that both of them have the same name before the extension.
	- In the second cell, set the variable file name to the name of the input file.
	- Run the submission.ipynb cell by cell.
	- The super-resolved output image would be found in upscaled_output folder.

atlas.ipynb stitches multiple .tif images together to form an atlas.

atlas folder consists of code to merge multiple .tif files to create an atlas.

The main code to create an atlas resides in atlas.ipynb

How to run atlas.ipynb
	- Put all the .tif files inside the input_tiffs folder.
	- Run all the cells of the atlas.ipynb.
	- See the magic!

atlas_final.tif is the sample atlas we've made by merging two tif files. This is a crop version of size 1 deg x 1 deg.

The tmc images used to make atlas_final.tif are: 
ch2_tmc_ndn_20220708T1115585981_d_oth_d32 and ch2_tmc_ndn_20220708T1314261067_d_oth_d32.
LAT, LONG = (49.2, 48.3) , (48.2, 49.3) 

