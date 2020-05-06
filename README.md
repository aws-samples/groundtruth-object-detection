## Streamlining data labeling for YOLO object detection in Amazon SageMaker Ground Truth

Object detection is a common task in computer vision (CV), and the YOLOv3 model is state-of-the-art in terms of accuracy and speed. In transfer learning, you obtain a model trained on a large but generic dataset and retrain the model on your custom dataset. One of the most time-consuming parts in transfer learning is collecting and labeling image data to generate a custom training dataset. This post explores how to do this in Amazon SageMaker Ground Truth.

Ground Truth offers a comprehensive platform for annotating the most common data labeling jobs in CV: image classification, object detection, semantic segmentation, and instance segmentation. You can perform labeling using Amazon Mechanical Turk or create your own private team to label collaboratively. You can also use one of the third-party data labeling service providers listed on the AWS Marketplace. Ground Truth offers an intuitive interface that is easy to work with. You can communicate with labelers about specific needs for your particular task using examples and notes through the interface.

Labeling data is already hard work. Creating training data for a CV modeling task requires data collection and storage, setting up labeling jobs, and post-processing the labeled data. Moreover, not all object detection models expect the data in the same format. For example, the Faster RCNN model expects the data in the popular Pascal VOC format, which the YOLO models can’t work with. These associated steps are part of any machine learning pipeline for CV. You sometimes need to run the pipeline multiple times to improve the model incrementally. This post shows how to perform these steps efficiently by using Python scripts and get to model training as quickly as possible. This post uses the YOLO format for its use case, but the steps are mostly independent of the data format.

The image labeling step of a training data generation task is inherently manual. This post shows how to create a reusable framework to create training data for model building efficiently. Specifically, you can do the following: 

* Create the required directory structure in Amazon S3 before starting a Ground Truth job
*	Create a private team of annotators and start a Ground Truth job
*	Collect the annotations when labeling is complete and save it in a pandas dataframe
*	Post-process the dataset for model training

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

