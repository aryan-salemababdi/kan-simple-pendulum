# Discovering Physical Laws with Kolmogorov-Arnold Networks (KANs)

This project demonstrates the capability of Kolmogorov-Arnold Networks (KANs), a novel AI architecture, to perform **symbolic regression** and uncover the fundamental laws of physics directly from simulated data. As a case study, we successfully rediscovered the formula for the period of a simple pendulum.

This work serves as a practical exploration into the intersection of modern machine learning and computational science, highlighting the potential of **interpretable AI** in scientific discovery.

---

## Objective

The primary goal was to test the hypothesis that a KAN model, unlike traditional "black-box" neural networks, could learn the precise functional relationships between physical variables and express them as a clean, symbolic formula.

> The target formula to rediscover was:
> T = 2 * pi * sqrt(L / g)
> where:
> * `T` is the period of oscillation.
> * `L` is the length of the pendulum.
> * `g` is the gravitational acceleration.

---

## Methodology

The project was conducted in two main phases:

### 1. Physics-Based Data Simulation

A synthetic dataset of 2,000 samples was generated using the exact physical formula. To ensure the model could learn the distinct influence of each variable, they were sampled from **wide, physically meaningful ranges**:
* **Length (`L`):** Uniformly sampled from [0.5, 10.0] meters.
* **Gravity (`g`):** Uniformly sampled from [2.0, 25.0] m/s² (simulating environments from Mars to Jupiter).

A small amount of Gaussian noise was added to the final period (`T`) to simulate experimental measurement errors.

### 2. KAN Model Training and Analysis

A **minimalist KAN architecture** (`width=[2, 1]`) was chosen to force the model to find the simplest possible explanation for the data. The model was trained to predict `T` from `L` and `g`.

The key step involved analyzing the trained model's internal structure to extract the learned mathematical functions. This included a systematic debugging process where the model's architecture and the data distribution were refined to guide the model towards the correct, most interpretable solution.

---

## Results: The Law Was Rediscovered

The KAN model **successfully learned the underlying physical law**. The internal analysis of the trained model revealed the following:

1.  **Correct Functional Forms:** The model correctly identified the two fundamental relationships:
    * The relationship with length (`L`) was found to be **`x^0.5`** (a square root function).
    * The relationship with gravity (`g`) was found to be **`1/x^0.5`** (an inverse square root function).

2.  **Accurate Final Formula:** By combining these learned functions and extracting the model's final scaling coefficient, we arrived at the complete formula:

    ### **Discovered Formula: T ≈ 6.2815 * sqrt(L / g)**

    This is an outstanding result. The learned coefficient **`6.2815`** is an extremely close approximation of the theoretical value of **`2π ≈ 6.2832`**, with a relative error of less than **0.03%**.

The model didn't just fit the data; it discovered the **structure** of the physical law governing the system.



[Image of a simple pendulum diagram]


---

## 🚀 How to Run

1.  **Clone the repository:**


2.  **Install dependencies:**
    ```bash
    pip install torch numpy pandas scikit-learn pykan matplotlib jupyter
    ```

3.  **Launch Jupyter Notebook:**
    ```bash
    jupyter notebook
    ```

4.  **Run the notebook:**
    Open the `simulate_data.ipynb` and `train_kan.ipynb` file and run the cells from top to bottom.

---

## Technologies Used
* Python
* PyTorch
* PyKAN
* NumPy & Pandas
* Scikit-learn
* Matplotlib
* Git & GitHub