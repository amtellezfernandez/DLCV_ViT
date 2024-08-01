The Caltech-UCSD Birds-200-2011 dataset, limited to 30 categories:
•
Is a significant challenge for bird species classification
•
Has a fine-grained nature
•
Presence of occlusions and distractions in the images
The semester project, a Kaggle competition of classification :
•
Produce a model that gives the highest possible accuracy on a test set containing the same categories
•
Baseline model: A resnet34pretrained on ImageNet achieving a relatively low accuracy of 50%


Assaidbefore,thedatasetprovidedforthecompetitionfacesmultiplechallengestocontrolincluding:
•
Imagesevenlydistributedamong30birdspeciesclasses
•
Variouschallenges,includingoff-centerbirdpositioning,occlusionsbyotherobjectssuchastreesorbirdcages,andvariationsinlightingandbackground.
•
Additionally,thetrainingsetcomprisesover2500imageswithannotations,thevalidationsetcontainsover240imagesformodelevaluation.Thetestset,containingover600images,isusedforfinalmodelinference.

1.
Bird detection and cropping using Deep Learning models:
CreationofanewdatasettofacilitatetheclassificationtaskwithobjectdetectionmodelsofbirdswithintheimageswithDetectron2library,leveragingtwoprominentmodelsMaskR-CNNandRetinaNet:
•
Selectionofthemostconfidentprediction(above85%)ofabirdacrossmodelswiththehighestconfidencedetectionretained
•
Croppingofalltheimagesinthedataset,therebyfocusingontheregionscontainingbirdsforsubsequentclassification
•
Preventionofdistortionandensuringuniformityandconsistencybyexpandingtheboundingboxestofitasquareshape
•
ImplementationofaminimalversionofYOLOv8forbirddetectionduetocomputationalconstraintsandtheprocessingtimesassociatedwithDetectron2
•
Augmentationofthetrainingandvalidationdatasetsbycroppingphotoscenteredonthedetectedbirds,therebystreamliningtheoverallworkflowandenhancingtherobustnessofourclassificationmodel

2.
Data augmentation:
Toenhancethediversityofthetrainingdataandimprovemodelgeneralization,weapplydataaugmentationtechniquesusingbothtorchvisiontransformsandAlbumentationsincluding:
•
randomresizingandcropping
•
horizontalflippingandnormalization
•
additionalaugmentationssuchasGaussiannoiseandmotionblur.Albumentationslibraryoffersawiderangeofaugmentationoptions,allowingustocreatearobustanddiversetrainingdataset.
Dataaugmentationiskeytoavoidoverfittinginourtrainingphase!
PS:Weseparatedthedatatransformationsofthetrainingandvalidationsetinordertointroducealeastrestrictingtransformationforthevalidationset.
