# ROC-AUC-in-the-context-of-TCR-antigen-binding.
Beginner-friendly tutorial to learn ROC–AUC using dummy TCR antigen binding data (binary + multi-class).


#  ROC–AUC Tutorial with Dummy TCR Data

This repository is a **step-by-step tutorial** to understand and apply **ROC–AUC (Receiver Operating Characteristic – Area Under Curve)** in the context of **T-cell receptor (TCR) antigen binding**.  
It is written in **simple language** so even beginners can follow easily.

---

# A Beginner's Guide to ROC and AUC for TCR-Antigen Binding 

This repository contains a Python notebook tutorial designed to teach the concepts of the **Receiver Operating Characteristic (ROC) curve** and the **Area Under the Curve (AUC)** in a simple, hands-on way. We use dummy data that mimics T-cell receptor (TCR) antigen binding to make the examples relevant for immunologists and bioinformaticians.


## 🤔 What are ROC and AUC? (The Simple Explanation)

In machine learning, we need to know how well our model can distinguish between two things. For us, it's "Does this TCR bind to the antigen?" (Yes vs. No). ROC and AUC are tools that help us measure this.

Imagine you have a new medical test to see if a patient has a disease. A good test will correctly identify sick people as "sick" and healthy people as "healthy."

### The ROC Curve: The Story of a Model's Performance

The ROC curve is a graph that tells this story. It plots two things:
1.  **True Positive Rate (Y-axis):** How many of the *actual* binders did our model correctly identify? (e.g., "You correctly found 90% of the true binders.")
2.  **False Positive Rate (X-axis):** How many non-binders did our model *incorrectly* label as binders? (e.g., "You raised a false alarm on 10% of the non-binders.")

<img width="545" height="400" alt="image" src="https://github.com/user-attachments/assets/fa86435c-51be-43d1-bef7-9f98894af21b" />

* **A great model** will have a curve that **hugs the top-left corner**. This means it's finding most of the true binders (high True Positive Rate) without making a lot of mistakes (low False Positive Rate).
* **A terrible model** will have a curve along the **diagonal dashed line**. This line represents random guessing, like flipping a coin.

### The AUC Score: The Final Grade

The AUC score is the **Area Under the (ROC) Curve**. It boils the entire curve down to a single number between 0 and 1. It’s like a final grade for your model's performance.

* **AUC = 1.0:** A perfect model. It correctly distinguishes all binders from non-binders.
* **AUC = 0.8 - 0.99:** An excellent model.
* **AUC = 0.7 - 0.8:** A good model.
* **AUC = 0.5:** A useless model. It has no skill in telling the classes apart (same as random guessing).

The main advantage of AUC is that it shows how good a model is at ranking predictions, regardless of what prediction threshold you choose.

***

##  The Tutorial Walkthrough

This tutorial runs two key examples using our dummy TCR data.

### Part 1: Binary Classification (Binds or Not?)

First, we tackle a simple yes/no question.
1.  **Load Data:** We load `binary_tcr_dummy.csv`, which has 10 feature columns and one label column (`1` for "binds," `0` for "does not bind").
2.  **Train Models:** We train two different models to see which is better: a simple **Logistic Regression** and a more powerful **Random Forest**.
3.  **Plot ROC & Calculate AUC:** We use the trained models to make predictions on our test data, then plot their ROC curves on the same graph to compare them.

### Part 2: Multi-class Classification (Which Antigen?)

Next, we ask a more complex question: which antigen does the TCR bind to? (e.g., Flu, Cancer, or Other).
1.  **The Challenge:** ROC curves are naturally for two classes (binary). To make them work for 3+ classes, we use a clever trick called **One-vs-Rest (OvR)**.
2.  **One-vs-Rest (OvR):** The model learns to solve three separate binary problems:
    * Is this TCR a "Flu" binder vs. everything else?
    * Is this TCR a "Cancer" binder vs. everything else?
    * Is this TCR an "Other" binder vs. everything else?
3.  **Plot & Calculate:** We then plot the ROC curve for each of these "mini-problems" on the same graph. This shows us how well the model can identify each individual class.

***

##  What We Found: The Results

### Binary Results
The plot clearly shows that the **Random Forest model is much better** than the Logistic Regression model. Its curve is much closer to the top-left corner.

* **Random Forest AUC = 0.97** (Excellent)
* **Logistic Regression AUC = 0.88** (Very Good)

This means the Random Forest model is significantly more reliable at distinguishing binding TCRs from non-binding ones.
<img width="613" height="547" alt="image" src="https://github.com/user-attachments/assets/72dcdad9-aa0f-47ab-a410-f6d5e3c6cdb4" />

### Multi-class Results
The model performed reasonably well at identifying each specific antigen class.

* **Class 0 (Flu) AUC = 0.82**
* **Class 1 (Cancer) AUC = 0.80**
* **Class 2 (Other) AUC = 0.83**

All scores are well above 0.5, telling us the model has a good ability to distinguish each class from the others, though there is still room for improvement.

<img width="702" height="547" alt="image" src="https://github.com/user-attachments/assets/dae18e97-7d69-4be6-9ace-ffed75d1103b" />

***

##  How to Run This Code

1.  Download or clone this repository.
2.  Open the `ROC_AUC_Tutorial.ipynb` file in Google Colab or Jupyter Notebook.
3.  If using Colab, run the first code cell to upload the `binary_tcr_dummy.csv` and `multiclass_tcr_dummy.csv` files from your computer.
4.  Run the cells from top to bottom to see the analysis and generate the plots.

##  Files in This Repository

* `ROC_AUC_Tutorial.ipynb`: The main Colab/Jupyter notebook with all the code and explanations.
* `binary_tcr_dummy.csv`: Dummy data for the binary classification task (Binds vs. Not).
* `multiclass_tcr_dummy.csv`: Dummy data for the multi-class classification task (Antigen 0, 1, or 2).
