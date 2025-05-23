# `beets (11"-12")`

## Dataset Metadata

| Metadata | Value |
| --- | --- |
| **Classes** | beets |
| **Machine Learning Task** | object_detection |
| **Agricultural Task** | crops_detection |
| **Location** | USA |
| **Sensor Modality** | RGB |
| **Platform** | ground |
| **Input Data Format** | JPG |
| **Annotation Format** | coco_json |
| **Number of Images** | 1000 |

![Example Image for beets](https://github.com/AxisAg/GHAIDatasets/blob/main/datasets/sample/beets_11-12_sample.png)


## Dataset

[beets_11-12_annotated](https://ghaipublic.s3.us-west-2.amazonaws.com/datasets/beets_11-12_annotated.zip)


### Quick start
You can easily open the dataset in any application compatible with the COCO format. Here is an example of how
to do that using [FiftyOne](https://voxel51.com/fiftyone/).

* Download the dataset, and extract the archive.
```shell
wget "https://ghaipublic.s3.us-west-2.amazonaws.com/datasets/beets_11-12_annotated.zip"
unzip beets_11-12_annotated.zip
```
* You should end up with a folder structure similar to this one:
```
Project/
|--beets_11-12/
|  |--coco.json
|  |--image1.jpg
|  |--...
```
* Create a virtual environment, and install the Python FiftyOne package.
```shell
python -m venv .venv
source .venv/bin/activate
python -m pip install fiftyone
```
* Create and run the following script.
```python
import fiftyone as fo
import fiftyone.zoo as foz


dataset = fo.Dataset.from_dir(
    dataset_type=fo.types.COCODetectionDataset,
    data_path="./beets_11-12/",
    labels_path="./beets_11-12/coco.json",
    include_id=True,
)

# Verify that the class list for our dataset was imported
print(dataset.default_classes)
print(dataset)

session = fo.launch_app(dataset)
session.wait()
```

