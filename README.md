# Table of contents:

[Dataset Overview](#Dataset-Overview) <br>
[Annotations](#Annotations) <br>
[Video Clips](#Video-Clips) <br>
[Interface](#Interface) <br>
[Usage](#Usage) <br>
[Detection Data](#Detection-Data) <br>
[Citation](#Citation) <br>
[Authors](#Authors) <br>
[License](#License) <br>

# Dataset Overview

Padik dataset is a comprehensive resource designed to explore the behavioral patterns of pedestrians and drivers during crossing events in unstructured, heterogeneous, and dynamic traffic environments. This dataset aims to enhance the accuracy of Advanced Driver Assistance Systems (ADAS) and autonomous vehicle (AV) control systems by providing detailed data on pedestrian-driver interactions. Padik includes 199 high-resolution video clips, ranging from 2 to 21 seconds, extracted from 170 hours of driving in various locations across Ahmedabad and Surat, Gujarat, India. The study spans over two years to encompass various weather conditions and times of day, providing a diverse and representative dataset. This project utilizes YOLOv3 to detect pedestrians in video frames. The script processes the video frame by frame, draws bounding boxes around detected pedestrians, and saves the results in an XML file. This XML file can be used for further analysis or as ground truth data for training models.


# Annotations

This dataset consists informations into three categories: 
Bounding Boxes - Processing frame number, frame shape, width, height and occlusion Information: 0- No occlusion, 1- Occlusion and activities like walking, crossing, standing, carrying objects, riding bicycles, etc.
Demographic and Behavioral Attributes: Gender-Male, Female, etc. Age Group- Categorized based on visual estimates. Crossing Characteristics- Time of crossing, speed, group dynamics, etc.
Traffic and Environmental Factors: Weather Conditions- Rain, fog, clear, etc. Time of Day- Morning, afternoon, evening, night. Traffic Density- High, medium, low. Road Type- Highway, urban, suburban.
Bounding boxes drawn on detected pedestrians, displayed in a window.The coordinates shown in the window, displayed as part of the label above each bounding box, are the top-left corner coordinates (x,y) of the bounding box.

# Video Clips

The folder "PD Videos" contains 199 video clips, which you can download manually.

PDVideos/GOPR7130_clip1.mp4
PDVideos/GOPR7131_clip3.mp4
…

# Interface

Dependencies:

The interface is written and tested using python 3.5. 
The interface also requires the following external libraries:
Opencv(cv2)
NumPy(np)
ElementTree(xml.etree.ElementTree)
OS(os)
The interface requires following YOLO files:
YOLOv3 Weights
YOLOv3 Configuration
Labels File

# Usage

Upon using any method to extract data, the interface first generates a database of all annotations in the form of a dictionary and saves it as a `.pkl` file in the cache directory (default path is `Padik/data_cache`). The interface includes several built-in sequence data generators, accessed via `generate_data_trajectory_sequence()`, with options for custom data generation.

# Detection Data
The interface includes a get_detection_data() method for generating detection data. The following methods are used in the code to process and analyze video frames:
create_xml(frame_data, output_path)
Generates an XML file containing the detection data for each frame in the video.

draw_bounding_boxes(frame, bbox_list)
Draws bounding boxes around detected pedestrians on each frame, with different colors indicating occlusion status.

get_bounding_boxes(detections, frame_width, frame_height, labels, conf_threshold=0.7)
Extracts bounding boxes from detection data, filtering results based on confidence, aspect ratio, and height.

process_video(video_path, output_xml_path, model_path, config_path, labels_path)
Main function that processes the video, detects pedestrians, draws bounding boxes, and saves the detection data in an XML file.

# Citation

If you use the Padik dataset in your research, please cite the following paper:

@inproceedings{kaveshgar2024padik,
  title={Padik - Pedestrian-Driver Interaction Dataset in Heterogeneous, Unstructured Traffic Environments},
  author={Kaveshgar, Maryam and Joshi, Keyur and Zinzuwadia, Parth and Trivedi, Khushal and Shah, Aarsha},
  booktitle={Proceedings of the 2024 Conference on Road Safety and Urban Planning},
  year={2024}
}

# Authors

- Maryam Kaveshgar, Ahmedabad University, Gujarat, India
- Keyur Joshi, Ahmedabad University, Gujarat, India
- Parth Zinzuwadia, Ahmedabad University, Gujarat, India
- Khushal Trivedi, Ahmedabad University, Gujarat, India
- Aarsha Shah, Ahmedabad University, Gujarat, India

For any issues related to the dataset, please contact Maryam Kaveshgar at [maryam.kaveshgar@ahduni.edu.in](mailto:maryam.kaveshgar@ahduni.edu.in).

# License

This project is licensed under the MIT License - see the LICENSE file for details. The video clips are licensed under the Creative Commons Attribution 4.0 International License.
