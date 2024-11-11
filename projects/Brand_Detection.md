# Brand Detection
Visual content, such as videos and images, plays a significant role in modern-day marketing. Traditionally, brands have had to pay content creators to feature their brand logo in their content. However, marketers can now leverage ML-powered computer vision to identify and recognize their products in various forms of content, including videos and images. This technology enables marketers to extract valuable insights from the content and understand the audience's behaviour better. With this understanding, brands can improve their advertising strategies and achieve higher ROI by targeting their audience more effectively and personalizing their messaging. The potential benefits of ML-powered computer vision in marketing make it an exciting area of exploration for brands and marketers.

# Instruction to train the model in Google Colab
```python
!rm -r /content/sample_data; # remove the sample directory from google colab
!git clone https://github.com/07Sada/brand.git # clone the repository
```
```python 
# change the directory
%cd /content/brand 
```
```python
# install the requirements
%pip install -r /content/brand/requirements.txt -q
```
```python
# initiate the training
from BrandRecognition.pipeline.training_pipeline import TrainPipeline
obj = TrainPipeline()
obj.run_pipeline()
```


# Screenshots
![image](https://user-images.githubusercontent.com/112761379/235088788-8aacd18f-cd43-49a2-a501-63b161ebc520.png)



# Demo
![Poject_video_#01](https://user-images.githubusercontent.com/112761379/235087330-d53c1591-ee65-4122-833e-94c6057e56a5.gif)

![Poject_video_#02](https://user-images.githubusercontent.com/112761379/235087455-35c6e4fc-12ad-46ef-98d8-2a3ff5b6ccb7.gif)
