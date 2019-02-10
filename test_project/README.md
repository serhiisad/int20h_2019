 ***A test project*** 
Image classification program to recognize handwritten roman numbers in range 1-8(one per image)

task details:
![](task.jpg)


To setup project run these commands:

'''
python3 -m virtualenv venv

source venv/bin/activate

pip install -r requirements.txt

deactivate

cd src

'''

***(optional)***
to retrain, type in terminal:

``` 
IMAGE_SIZE=224
ARCHITECTURE="mobilenet_0.50_${IMAGE_SIZE}"

  python -m scripts.retrain   \
--bottleneck_dir=tf_files/bottlenecks   \
--how_many_training_steps=500   --model_dir=tf_files/models/   \
--summaries_dir=tf_files/training_summaries/"${ARCHITECTURE}"   \
--output_graph=tf_files/retrained_graph.pb   \
--output_labels=tf_files/retrained_labels.txt   \
--architecture="${ARCHITECTURE}"   \
--image_dir=tf_files/numbers_photos

```

to run classifier, type:

``` 
python -m scripts.label_image --graph=tf_files/retrained_graph.pb  --image=test_images/<your test image name>.jpg

```
