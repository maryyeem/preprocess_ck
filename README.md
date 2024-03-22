## Dataset Pre-processing
This folder contains code that will help you pre-process and save the [extened Cohn-Kanade (CK+)][CK+] and 
the Toronto Face Database (TFD) in ``.npy`` files to be used by our CNN models. 

> :pushpin: **Note:** We assume that you have already downloaded copies of the CK+ and TFD datasets 
on your machine. This code does not download the datasets from the distributors. It only pre-processes 
an already downloaded copy.

## Extended Cohn-Kanade Dataset (CK+)

If you have downloaded the CK+ dataset properly, the folder should contain the following files:
```shell
CK_Agreement_Form.pdf
extended-cohn-kanade-images.zip
Consent-for-publication.doc
CVPR2010_CK.pdf
Emotion_labels.zip
FACS_labels.zip
ReadMeCohnKanadeDatabase_website.txt
```

First, unzip the ``extended-cohn-kanade-images.zip`` and the ``Emotion_labels.zip`` files. Make sure
that the folders that hold the extracted data are named: ``cohn-kanade-images/`` and ``Emotion_labels/``
respectively.

The ``make_ck_plus_dataset.py`` file will help you convert the images in the ``cohn-kanade-images`` folder and the labels in the ``Emotion_labels`` folder to ``.npy`` files. The script requires two arguments. They are:

1. **Input path:** path of CK+ dataset folder
2. **Output/save path:** path to save the ``.npy`` files (default: ``./CK_PLUS_HERE/``)

To run the script, simply type the following:
```python
python make_ck_plus_dataset.py --input_path /path/to/ck+/dataset --save_path /path/to/save/npy/files
```

For example, suppose the CK+ dataset was in ``/data/CK_PLUS/`` and you wanted to save 
the ```.npy``` files to ``./CK_PLUS_HERE/``, then you would use the following command:
```python
python make_tfd_dataset.py --input_path /data/CK_PLUS/ --save_path ./CK_PLUS_HERE/
```

The code will copy the CK+ datset to ``./CK_PLUS_HERE/`` and should now contain a ``npy_files/`` folder.
The ``npy_files/`` folder should contain the following:
```shell
npy_files/
  folds.npy
  subjs.npy
  X.npy
  y.npy
```

The images and the labels are stored in ``X.npy`` and ``y.npy`` respectively, while ``subjs.npy`` denotes 
the subject id of each person in the images and ``folds.npy`` says which image belongs to which fold (0-9).

Now, all you need to do is open the ``data_paths.py`` files in the ``ck_plus`` and ``ck_plus_six_class`` directories of this respository, and set them to the **absolute path** of the ``./CK_PLUS_HERE/npy_files/`` folder.

#
