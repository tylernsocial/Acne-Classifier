# Acne Image Classification Project

## Project Overview

This project focuses on building a custom image classification model for acne-related images. The main goal was to create a model that can take an image and classify it into the correct acne category.

The project went through multiple stages, starting with a simple baseline model, then moving to a custom CNN model, and finally using transfer learning to improve performance. Each stage helped me understand what the previous model was missing and what needed to be changed to improve the classifier.

The final model was saved along with the class names so it can be reused later for predictions or connected to a future acne tracking application.

<img width="415" height="458" alt="image" src="https://github.com/user-attachments/assets/dc0cbddf-40a4-4e6f-9fa5-28326fcc11a1" />

---

## Dataset

The dataset used in this project was manually collected by scraping acne-related images from online sources. Since this was not a ready-made dataset, I had to gather, organize, and prepare the images before using them for model training.

The images were separated into different acne-related classes. Each class represented a category that the model needed to learn. After collecting the images, I organized the dataset into folders, where each folder represented one acne class. This folder structure made it easier to load the images into the model using image classification tools.

The dataset was split into three main parts:

- **Training data:** Used to teach the model.
- **Validation data:** Used to check how the model performed during training.
- **Testing data:** Used at the end to evaluate the final model on unseen images.

This split was important because it allowed me to evaluate the model more fairly instead of only measuring how well it performed on images it had already seen.

Since the dataset was manually scraped, one important challenge was that the images were not perfectly consistent. Images could vary in lighting, angle, image quality, skin tone, background, and how clearly the acne was shown. This made the classification task more realistic, but also more difficult.

---

## Project Life Cycle

The project followed a full model development process. Instead of building one model and stopping there, I created multiple versions and compared their performance.

The main stages were:

1. Baseline model
2. Custom CNN model
3. Transfer learning model
4. Final model evaluation
5. Saving the final model and class names

Each stage helped improve the project and gave me a better understanding of what the model needed.

---

# 1. Baseline Model

## Purpose of the Baseline Model

The first model I created was the baseline model. The purpose of this model was to create a simple starting point.

The baseline model helped answer basic questions such as:

- Is the dataset loading correctly?
- Are the class labels working properly?
- Can the model learn anything from the images?
- Is the training pipeline working?
- What level of performance can I get before making improvements?

The baseline model was important because it gave me a reference point. Without a baseline, it would be harder to tell whether later models were actually improving.

## What I Learned From the Baseline Model

The baseline model showed that the project pipeline was working, but it was not strong enough to be the final model.

It was able to train, but its performance was limited. This made sense because the baseline model was simple and did not have enough ability to learn complex image patterns.

Acne images can be difficult to classify because different acne types can look visually similar. Lighting, skin tone, camera quality, image angle, and background can also affect the image. The baseline model was not powerful enough to handle all of these differences well.

## What Changed After the Baseline Model

After the baseline model, I needed a stronger model that could learn image features more effectively.

This led me to build a custom Convolutional Neural Network.

---

# 2. Custom CNN Model

## Why I Used a CNN

After the baseline model, I created a custom CNN model.

CNNs are commonly used for image classification because they are designed to learn visual features from images. They can detect patterns such as edges, textures, shapes, and more detailed image features.

This made a CNN a better fit for acne classification compared to the simpler baseline model.

## What Changed

The project moved from a basic baseline model to a custom CNN architecture.

The CNN used convolutional layers and pooling layers to learn visual patterns from the images. This allowed the model to focus more on important image features instead of treating the image like simple raw data.

This was an important improvement because acne classification depends heavily on small visual details such as texture, redness, bumps, and skin patterns.

## What I Learned From the CNN

The CNN performed better than the baseline model because it had a better structure for image classification.

However, the custom CNN still had limitations. Since it was trained from scratch, it had to learn all image features only from my acne dataset.

This can be difficult when the dataset is not extremely large. A model trained from scratch usually needs a lot of images to learn strong and general features.

From this stage, I learned that CNNs are much better for image data than a simple baseline model, but training a CNN from scratch can still be limited when working with a smaller manually collected dataset.

## What Changed After the CNN

Because the custom CNN still had room for improvement, I moved to transfer learning.

Transfer learning allowed me to use a model that had already learned useful image features from a much larger dataset.

---

# 3. Transfer Learning Model

## Why I Used Transfer Learning

Transfer learning was used because it can improve image classification performance, especially when working with a smaller custom dataset.

Instead of training a model completely from scratch, transfer learning uses a pre-trained model that has already learned general image features from a large dataset.

These general features can include:

- Edges
- Lines
- Textures
- Shapes
- Color patterns
- Object-level features

The model can then reuse those learned features and adapt them to the acne classification task.

## What Changed

The project moved from a custom CNN trained from scratch to a transfer learning model.

This was a major improvement because the model did not have to learn every image feature from the beginning. Instead, it started with useful pre-trained knowledge and then learned how to apply that knowledge to acne images.

This made the model more powerful and better suited for the dataset.

## What I Learned From Transfer Learning

Transfer learning showed that using a pre-trained model can improve performance compared to building everything from scratch.

This stage helped the model recognize patterns in the images more effectively and generalize better to new images.

The transfer learning model became the strongest version of the project because it combined pre-trained image knowledge with my custom acne dataset.

---

# 4. Training Progress and Model Selection

Throughout the project, I compared different model versions to decide which one should be used as the final model.

The baseline model was useful as a starting point, but it was too simple.

The custom CNN improved the model because it was designed for image data, but it still had limitations because it was trained from scratch.

The transfer learning model performed the best overall and was selected as the final model.

For the final model, I trained it for up to **200 epochs**. This was chosen after comparing earlier training results and noticing that the model was still improving gradually. The final model was selected because it gave the best overall balance between performance and generalization.

---

# 5. Model Comparison

| Model Version | Main Purpose | What Changed | What I Learned |
|---|---|---|---|
| Baseline Model | Create a simple starting point | Used a basic model to test the pipeline | The dataset and training process worked, but the model was too simple |
| Custom CNN | Improve image feature learning | Added convolutional and pooling layers | CNNs are better for image data, but training from scratch has limits |
| Transfer Learning Model | Improve final performance | Used a pre-trained model and adapted it to acne images | Transfer learning worked best for this project |
| Final Model | Best selected version | Trained and evaluated the transfer learning model | This model gave the strongest overall results |

---

# 6. Final Model Evaluation

The final model was evaluated using the test set. This was important because the test set contained images the model had not seen during training.

The final evaluation included:

- Test accuracy
- Test loss
- Confusion matrix
- Classification report
- Precision
- Recall
- F1-score

These evaluation tools helped me understand not only how accurate the model was overall, but also how well it performed for each individual acne class.

---

## Final Results

The final transfer learning model was the strongest model created during this project.

Final model results:

| Metric | Result |
|---|---:|
| Final model type | Transfer learning |
| Final training length | 200 epochs |
| Test accuracy | `ADD YOUR TEST ACCURACY HERE` |
| Test loss | `ADD YOUR TEST LOSS HERE` |
| Best performing class | `ADD CLASS NAME HERE` |
| Most difficult class | `ADD CLASS NAME HERE` |

The final model was selected because it performed better than both the baseline model and the custom CNN model.

---

## Confusion Matrix

The confusion matrix was used to see where the model was making correct and incorrect predictions.

This helped me identify:

- Which acne classes were predicted correctly most often.
- Which acne classes were confused with each other.
- Which classes may need more training images or better image quality.

<img width="718" height="638" alt="9749d9f3-8638-4686-8866-32f0ac431670" src="https://github.com/user-attachments/assets/1cd845e5-7d78-42cd-b4d4-45c9ac43c594" />

This was useful because acne categories can be visually similar, so accuracy alone was not enough to fully understand the model’s performance.

---

## Classification Report

The classification report gave a more detailed breakdown of the final model’s performance.

It included:

- **Precision:** How many images predicted as a class were actually correct.
- **Recall:** How many actual images from a class the model correctly identified.
- **F1-score:** A balanced score between precision and recall.

This helped me understand the model at a class-by-class level.

<img width="395" height="121" alt="image" src="https://github.com/user-attachments/assets/59a1faf9-8861-4864-be14-019a7684115c" />


---

# 7. What Changed Throughout the Project

## Baseline Model

The baseline model was used as the starting point. It showed that the dataset and training pipeline worked, but it was too simple to capture the visual complexity of acne images.

## Custom CNN Model

The custom CNN was created to improve image feature learning. It was better suited for image classification because it could learn patterns such as textures, shapes, and edges.

However, since it was trained from scratch, it still had limitations. It needed to learn all image features only from my dataset, which made performance harder to improve.

## Transfer Learning Model

The transfer learning model improved on the custom CNN by using a pre-trained model that already understood general image features.

This helped the model perform better on the acne dataset and made it the best choice for the final model.

---

# 8. What I Learned

## A Baseline Model Is Important

The baseline model gave the project a starting point. It helped confirm that the dataset was loading correctly and that the model could train.

It also made it easier to compare later models and see whether the project was improving.

## CNNs Are Better for Image Data

The custom CNN showed that image classification needs a model that can understand visual patterns.

Compared to the baseline model, the CNN was better suited for the task because it could learn features directly from images.

## Training From Scratch Has Limits

The CNN helped improve the model, but it also showed that training from scratch can be difficult when the dataset is limited.

The model had to learn every feature by itself, which can require a lot of images and training time.

## Transfer Learning Is More Effective

Transfer learning helped improve the project by using a pre-trained model that already knew how to detect general image features.

This allowed the model to focus more on learning the acne-specific classes instead of starting from zero.

## Evaluation Needs More Than Accuracy

The final model was evaluated using more than just accuracy.

The confusion matrix and classification report helped show which classes the model performed well on and which classes were more difficult.

This was important because a model can have good overall accuracy but still struggle with certain categories.

---

# 9. Saved Files

The final stage of the project was saving the trained model and the class names.

Saving the model allows it to be loaded later without needing to retrain it.

Saving the class names is also important because the model outputs prediction indexes, and the class names are needed to convert those indexes into readable labels.

---

# 10. How This Project Could Be Improved

Although the final transfer learning model performed the best out of the models tested, there are still several ways this project could be improved in the future.

## Better Dataset Quality

The biggest improvement would be collecting a cleaner and higher-quality dataset. Since the dataset was manually scraped, some images may have issues such as poor lighting, blurry quality, inconsistent angles, unclear acne regions, or backgrounds that distract from the skin itself.

A better dataset would include images that are clearer, more consistent, and more directly focused on the acne being classified. This would help the model learn the actual acne patterns instead of learning noise from the image.

## More Images Per Class

Another major improvement would be increasing the number of images in each acne category.

More images would give the model more examples to learn from, which could improve its ability to generalize to new images. This would be especially helpful for classes where the model struggled or had lower precision, recall, or F1-score.

## Better Class Balance

If some acne classes have more images than others, the model may become biased toward the larger classes. This means it may perform better on categories with more examples and worse on categories with fewer examples.

Balancing the dataset would help the model learn each class more fairly. This could be done by collecting more images for underrepresented classes or using data augmentation carefully.

## More Consistent Image Labelling

Since acne types can look visually similar, another improvement would be making sure the labels are as accurate and consistent as possible.

If some images are mislabeled or unclear, the model may learn the wrong patterns. Having clearer labelling rules, or even getting labels checked by someone with more dermatology knowledge, would improve the reliability of the dataset.

## Stronger Data Cleaning

Before training future models, the dataset could be cleaned more carefully by removing images that are blurry, irrelevant, duplicated, low quality, or not focused on acne.

This would help the model focus on meaningful skin features instead of being affected by unrelated image noise.

## More Real-World Testing

The model should also be tested on real-world images outside of the original dataset.

This is important because images uploaded by real users may have different lighting, camera quality, angles, skin tones, and backgrounds. Testing on real-world images would show whether the model can generalize beyond the scraped dataset.

## Experimenting With More Models

Future work could also include testing other transfer learning architectures, such as EfficientNet, MobileNet, ResNet, or DenseNet.

Different models may perform better depending on the dataset size, image quality, and classification difficulty.


