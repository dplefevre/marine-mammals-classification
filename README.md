# marine-mammals-classification



# Data Scrape and Augmentation

## Classes: 


* The date of scrape from Hawkins marine mammal database. Using Docker image mongo server to store content. Creating a marine sound database with each class as a collection within the database. Each class has about 60 audio cuts in which we download via the web scrape to a pre-process data directory for lengthening, duplicating and augmenting. I have two separate data directories. The first is "data" within "webscrape" in which the raw audio is downloadedfrom the website is stored. Second is a training dataset, Which stores each class of audio files to the length of 30 seconds. 

* To achieve this, I implement the audio Concatenate and augmentation python file. This file walks the directories of the raw audio data initially downloaded and aplies two seperates task. The first part of the Python file extends each audio track to 30 seconds And is stored in a new directory call training data. The second half of the Python file iterates through each class and duplicates the audio file to randomly augments +/- 3 dB and +/- 2 semitones. These new augmentant samples are then stored back into the training dataset in the appropriate class. This synthesize data set is approximately 10,800 data points. Each class has original audio and half augmented all at 30 seconds with approximatel 100 - 130 audio clip per class. The classes are balanced. 



# Audio preprocessing:


Once we have our training dataset we will proceed to Pre-process our audio to MFCCs. Here, we will take a MFCCs every 3 seconds of each audio track in each class. The audio is down sampled to 22050 and mono. We will walk through the training data set directories applying pre-processing to each class. The pre-processing python file will export our MFCCs, Labels and mappings for each class into a json file. 