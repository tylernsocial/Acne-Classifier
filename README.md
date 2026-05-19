# Acne Image Classification Project

## Project Overview

This project focuses on building a custom image classification model for acne-related images. The main goal was to train a deep learning model that can classify acne images into different categories based on visual patterns in the dataset.

The project followed a full machine learning development cycle, starting from a basic baseline model and gradually improving it through experimentation, training adjustments, callbacks, and evaluation. Throughout the process, different versions of the model were tested to understand how changes such as the number of epochs, learning rate behaviour, and validation performance affected the final results.

By the end of the project, a final trained model was selected, saved, and prepared for future use in an acne-based application.

---

## Project Goal

The goal of this project was to create an acne image classifier that could accurately recognize different acne-related image classes.

This classifier is intended to become part of a larger acne tracking application, where users may eventually be able to upload images and receive classification results. The app idea also includes tracking lifestyle factors such as diet, sleep, routines, and other changes that may influence acne over time.

---

## Dataset

The dataset used for this project contained images organized into different acne-related classes. Each class represented a specific category that the model needed to learn to identify.

The dataset was split into separate training, validation, and testing sets so that the model could be trained, tuned, and evaluated fairly.

The general purpose of each split was:

- **Training set:** Used to teach the model patterns from the images.
- **Validation set:** Used during training to monitor performance and help detect overfitting or underfitting.
- **Testing set:** Used only after model development to evaluate how well the final model performs on unseen data.

Keeping the test set separate was important because it allowed the final model to be evaluated more fairly.

---

## Project Life Cycle

The project went through multiple stages. Each stage helped us understand what the model was doing and what needed to be improved.

---

# 1. Baseline Model

## Purpose of the Baseline Model

The first model created was the baseline model. The purpose of the baseline model was not necessarily to get the best possible accuracy right away, but to create a starting point.

The baseline model helped answer questions such as:

- Can the model learn from the dataset at all?
- Are the images and labels loading correctly?
- Is the training pipeline working?
- Is the model underfitting, overfitting, or learning normally?
- What accuracy can we get before making improvements?

This gave us something to compare future models against.

## What We Learned From the Baseline Model

From the baseline model, we learned that the model was able to train and recognize some patterns in the dataset, but it was not yet strong enough to be considered the final version.

The baseline model gave us an important first look at the behaviour of the training and validation curves. These curves helped us understand whether the model was improving, struggling, or memorizing the training data too much.

The baseline model also showed that simply training a model once is not enough. Model performance depends heavily on training time, validation behaviour, learning rate, and how well the model generalizes to new images.

## Why the Baseline Model Was Not Enough

The baseline model was useful, but it likely had limitations such as:

- Lower accuracy compared to later models.
- Less stable validation performance.
- Possible underfitting if the model had not trained long enough.
- Possible overfitting if training accuracy improved but validation accuracy did not.
- No learning rate adjustment to help the model improve more carefully over time.

Because of this, more experiments were needed.

---

# 2. Improving the Training Process

After the baseline model, the next step was to improve the training process instead of only changing the model architecture.

One of the major improvements was adding a learning rate callback.

## ReduceLROnPlateau Callback

A `ReduceLROnPlateau` callback was added during training.

This callback watches the model’s validation performance. If the model stops improving for a certain number of epochs, the callback reduces the learning rate.

This is useful because a high learning rate may help the model learn quickly at the beginning, but later in training, a smaller learning rate can help the model make more careful adjustments.

## Why This Was Important

Adding `ReduceLROnPlateau` helped the model continue improving instead of getting stuck too early.

In image classification projects, the learning rate can have a major impact on performance. If the learning rate is too high, the model may jump around and miss better solutions. If it is too low, the model may learn very slowly.

The callback allowed the model to automatically lower the learning rate when improvement slowed down.

## What We Learned

From using the learning rate callback, we learned that training is not only about increasing epochs. The way the model learns during those epochs matters.

The callback helped make training more controlled and gave the model a better chance to improve gradually.

---

# 3. Training for 100 Epochs

One of the first longer training experiments was done using 100 epochs with the learning rate callback.

## Why We Tested 100 Epochs

Training for 100 epochs gave the model more time to learn compared to shorter training runs. The goal was to see whether longer training would improve accuracy and validation performance.

## What Happened

The 100-epoch model trained successfully, but the results were not as strong as later experiments. When compared to the model trained for 150 epochs, the 100-epoch version performed worse.

## What We Learned

From the 100-epoch model, we learned that the model still had room to improve. The training and validation results suggested that the model had not fully reached its best performance yet.

This meant that stopping at 100 epochs may have been too early.

The key lesson was that the model was still benefiting from additional training time.

---

# 4. Training for 150 Epochs

After the 100-epoch experiment, the model was trained for 150 epochs.

## Why We Tested 150 Epochs

Since the 100-epoch model still showed room for improvement, 150 epochs was chosen as the next experiment. This allowed the model more time to learn while still avoiding an extreme jump in training time.

## What Improved

The 150-epoch model produced better results than the 100-epoch model.

The training curves showed a more gradual improvement, and the model appeared to be learning better patterns from the images.

This was an important stage because it showed that increasing the number of epochs was helping rather than immediately causing overfitting.

## What We Learned

From the 150-epoch model, we learned that the model was still improving with more training. This suggested that the model had not fully plateaued at 100 epochs.

However, this also introduced an important question:

Should we keep increasing the number of epochs?

At this point, we had to be careful. More epochs can improve performance, but they can also lead to overfitting if the model starts memorizing the training images instead of learning general patterns.

The 150-epoch model became a strong candidate, but we decided to test one more reasonable increase before choosing the final model.

---

# 5. Considering More Epochs

At one point, we considered whether jumping from 150 epochs to 300 epochs would make sense.

## Why We Did Not Immediately Jump to 300 Epochs

Jumping from 150 to 300 epochs would not necessarily be wrong, but it would be a large increase. If the model was still improving, more epochs could help, but doubling the training time could also increase the risk of overfitting.

Instead of making a huge jump, the better approach was to increase gradually.

This is why 200 epochs was tested next.

## What We Learned

This part of the project showed that model development should be experimental, but controlled.

Instead of randomly increasing training time, it is better to compare models step by step:

- 100 epochs
- 150 epochs
- 200 epochs

This makes it easier to understand whether each change actually helps.

---

# 6. Training for 200 Epochs

The model was then trained for 200 epochs.

## Why We Tested 200 Epochs

The 150-epoch model was already performing well, but the results suggested that the model might still be improving gradually. Because of that, 200 epochs was a reasonable next experiment.

This was not as extreme as jumping to 300 epochs, but it still gave the model more time to learn.

## What Happened

The 200-epoch model showed better or more complete learning compared to the previous models. The training and validation results suggested that the model was still benefiting from additional epochs.

After comparing the 150-epoch and 200-epoch models, the 200-epoch model was selected as the final model.

## Why We Chose the 200-Epoch Model

The 200-epoch model was chosen because it provided the best balance between performance and training stability.

It showed that the model was still gradually improving, while not showing enough evidence that training had become harmful or heavily overfit.

The decision was not based only on training accuracy. It was based on looking at the overall behaviour of the model, including:

- Training accuracy
- Validation accuracy
- Training loss
- Validation loss
- Test performance
- Confusion matrix
- Classification report

This made the final model choice more reliable.

---

# 7. Final Model Evaluation

After choosing the 200-epoch model, the next step was to evaluate it on the test set.

The test set was important because it contained images the model had not used during training or validation.

## Evaluation Metrics

Several evaluation methods were used to understand the final model’s performance.

These included:

- Accuracy
- Loss
- Confusion matrix
- Precision
- Recall
- F1-score
- Classification report

Each metric helped explain the model from a different angle.

---

## Accuracy

Accuracy shows the overall percentage of images that the model classified correctly.

A high accuracy means the model is correctly predicting many images overall.

However, accuracy alone is not enough, especially if some classes have more images than others. That is why precision, recall, F1-score, and the confusion matrix were also important.

---

## Loss

Loss measures how far the model’s predictions are from the correct answers.

Even when accuracy is high, loss still matters because it shows how confident or uncertain the model is.

A decreasing loss usually means the model is learning better. However, if training loss keeps decreasing while validation loss increases, that can be a sign of overfitting.

---

## Confusion Matrix

The confusion matrix was used to see how the model performed for each individual class.

It shows:

- Which classes were predicted correctly.
- Which classes were confused with each other.
- Whether the model struggled more with certain categories.

This was important because an acne classifier should not only perform well overall, but should also be checked class by class.

Some classes may be visually similar, which can cause the model to confuse them. The confusion matrix helped identify those problem areas.

---

## Precision

Precision measures how many of the images predicted as a certain class were actually correct.

For example, if the model predicts several images as a specific acne class, precision tells us how often those predictions were right.

High precision means the model does not make many false positive predictions for that class.

---

## Recall

Recall measures how many actual images from a class the model successfully found.

For example, if there are many images of a certain acne class, recall tells us how many of those the model correctly identified.

High recall means the model is not missing many examples of that class.

---

## F1-Score

The F1-score combines precision and recall into one score.

This is useful because it gives a balanced view of performance.

A high F1-score means the model is doing well in both precision and recall.

---

# 8. Final Model

The final selected model was the 200-epoch model trained with the `ReduceLROnPlateau` callback.

## Why This Model Was Selected

This model was selected because it performed better than the earlier versions and showed the strongest overall learning behaviour.

Compared to the earlier models, the final model benefited from:

- More training time.
- A learning rate callback.
- Better validation performance.
- Improved test evaluation.
- More reliable class-level results.

The final model represented the best version developed during this project.

---

## Final Model Files

After training, the final model was saved for future use.

The saved files include:

- The trained model file.
- The class names file.

Saving the model and class names is important because the model needs the same class order when making predictions later.

Without saving the class names, the model may output a prediction index, but it would be harder to know which acne class that index represents.

---

# 9. What Changed Throughout the Project

The project improved through several stages.

## From Baseline Model to Final Model

At the beginning, the baseline model was used to confirm that the image classification pipeline worked. It showed that the model could learn from the dataset, but it was not strong enough to be the final version.

After that, the training process was improved by adding a learning rate callback. This allowed the model to reduce its learning rate when validation performance stopped improving.

Then, different epoch values were tested. The model was trained with 100 epochs, then 150 epochs, and finally 200 epochs.

Each experiment helped answer whether the model needed more training time.

The final model used 200 epochs because it showed the best balance between learning and generalization.

---

## Main Changes Made

The main changes during the project were:

1. Started with a baseline image classification model.
2. Trained the model and checked initial performance.
3. Added `ReduceLROnPlateau` to improve learning rate behaviour.
4. Tested training with 100 epochs.
5. Compared the 100-epoch model to a 150-epoch model.
6. Noticed that the model was still gradually improving.
7. Decided not to immediately jump to 300 epochs.
8. Tested a 200-epoch model instead.
9. Compared the 150-epoch and 200-epoch results.
10. Selected the 200-epoch model as the final version.
11. Evaluated the final model using test results, confusion matrix, and classification report.
12. Saved the final model and class names for future use.

---

# 10. What We Learned

This project showed that building a machine learning model is not a one-step process. It requires experimentation, comparison, and interpretation.

## Lesson 1: A Baseline Model Is Important

The baseline model gave us a starting point. Without it, we would not know whether later models were actually improving.

The baseline helped us understand the initial performance of the model and gave us something to compare against.

## Lesson 2: More Epochs Can Help, But Only Up to a Point

Increasing the number of epochs helped improve the model from 100 to 150 and then to 200 epochs.

However, we also learned that increasing epochs should be done carefully. More epochs can improve performance, but too many can lead to overfitting.

That is why we tested 200 epochs instead of immediately jumping to 300.

## Lesson 3: Validation Results Matter

Training accuracy alone is not enough. A model can perform very well on the training data but still perform poorly on new images.

Validation accuracy and validation loss helped us understand whether the model was learning patterns that could generalize beyond the training set.

## Lesson 4: Learning Rate Scheduling Helps

The `ReduceLROnPlateau` callback helped the model continue learning more carefully when improvement slowed down.

This showed that training quality depends not only on the model architecture, but also on how the training process is controlled.

## Lesson 5: Test Set Evaluation Should Come Last

The test set was saved for final evaluation. This helped make sure the final performance was measured on images the model had not seen during training or validation.

This made the final evaluation more trustworthy.

## Lesson 6: Class-Level Performance Matters

The confusion matrix and classification report showed that it is important to look beyond overall accuracy.

Some classes may perform better than others, and some may be confused with visually similar categories.

This is especially important for acne classification because acne types can have overlapping visual features.

---

# 11. Final Results Interpretation

The final model showed that the acne classifier was able to learn meaningful patterns from the image dataset.

The training and validation curves suggested that the model improved over time, especially when trained for more epochs with the learning rate callback.

The confusion matrix helped show which classes the model predicted correctly and where it struggled. The classification report gave a more detailed breakdown of precision, recall, and F1-score for each class.

Overall, the final model was selected because it gave the strongest performance out of the tested versions and showed the best balance between accuracy and generalization.

---

# 12. How to Use the Model

The saved model can be loaded later and used to make predictions on new acne images.

A general prediction workflow would look like this:

1. Load the saved model.
2. Load the saved class names.
3. Preprocess the input image so it matches the format used during training.
4. Pass the image into the model.
5. Get the predicted class index.
6. Match the predicted index to the correct class name.
7. Display the prediction result.

---

# 13. Possible Future Improvements

Although the final model performed better than earlier versions, there are still several ways the project could be improved in the future.

## More Data

Adding more images could help the model learn better and generalize more effectively.

This would be especially useful for classes that the model struggles with or classes that have fewer examples.

## Better Class Balance

If some classes have more images than others, the model may become biased toward the larger classes.

Balancing the dataset could improve performance across all classes.

## Data Augmentation

More image augmentation could help the model become more robust.

Examples include:

- Rotation
- Zooming
- Brightness adjustment
- Horizontal flipping
- Cropping
- Contrast changes

This could help the model handle real-world images taken under different lighting and angle conditions.

## Testing Other Architectures

Future versions could test more advanced models or transfer learning approaches.

For example, models such as MobileNet, EfficientNet, or ResNet could be tested to see whether they improve accuracy.

## Deployment

The model could eventually be connected to a web or mobile application.

In the larger acne app idea, the classifier could be combined with lifestyle tracking features so users can monitor acne changes over time.

---

# 14. Conclusion

This project followed the full life cycle of building an image classification model, starting from a baseline model and gradually improving it through experimentation.

The baseline model helped establish a starting point. From there, the training process was improved using a learning rate callback, and multiple epoch values were tested to understand how longer training affected performance.

The 100-epoch model showed that the model still had room to improve. The 150-epoch model performed better and showed continued learning. The 200-epoch model gave the strongest overall results and was selected as the final model.

The project showed that model development is not just about getting a high accuracy score. It is about understanding how the model learns, checking whether it generalizes well, and using evaluation tools such as confusion matrices and classification reports to understand performance in more detail.

The final saved model and class names now provide a foundation that can be used in the next stage of the project, including prediction scripts, app integration, or future improvements to the acne classification system.
