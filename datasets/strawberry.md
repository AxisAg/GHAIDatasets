# `strawberry`

## Dataset Metadata

| Metadata | Value |
| --- | --- |
| **Classes** | 'Bud', 'Calyx', 'Detached Fruit', 'Flower', 'Large green', 'Leaf', 'Ripe fruit', 'Small Green', 'Stem', 'Unripe fruit' |
| **Machine Learning Task** | object_detection |
| **Agricultural Task** | crops_detection |
| **Location** | USA |
| **Sensor Modality** | RGB |
| **Platform** | ground |
| **Input Data Format** | JPG |
| **Annotation Format** | coco_json |
| **Number of Images** | 500 |

![Example Image for strawberry](https://github.com/AxisAg/GHAIDatasets/blob/main/datasets/sample/strawberry_sample.png)


## Dataset

[strawberry_annotated](https://ghaipublic.s3.us-west-2.amazonaws.com/datasets/strawberry_annotated.zip)


### Quick start
You can easily open the dataset in any application compatible with the COCO format. Here is an example of how
to do that using [FiftyOne](https://voxel51.com/fiftyone/).

* Download the dataset, and extract the archive.
```shell
wget "https://ghaipublic.s3.us-west-2.amazonaws.com/datasets/strawberry_annotated.zip"
unzip strawberry_annotated.zip
```
* You should end up with a folder structure similar to this one:
```
Project/
|--strawberry/
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
    data_path="./strawberry/",
    labels_path="./strawberry/coco.json",
    include_id=True,
)

# Verify that the class list for our dataset was imported
print(dataset.default_classes)
print(dataset)

session = fo.launch_app(dataset)
session.wait()
```

