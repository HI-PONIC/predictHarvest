# Predicting Hydroponic Plant Harvest Using Time series


The model that being used in app represents a **time series** prediction model using a neural network implemented with TensorFlow and Keras. Here's a detailed breakdown of its components and the type of model it.
This model was built  with dataset that you can access in here [lettuce dataset](https://www.kaggle.com/datasets/santoshshaha/lettuce-plant-disease-dataset?select=lettuce)
we use lettuce as an example of the subject for our product (HI PONIC)

----------------------------------------------------------------------------------------------------
1. Model Architecture
   The model is defined as a Sequential model in Keras.
   It uses three dense (fully connected) layers:
      - The first dense layer has 64 units and takes an input shape of (N_PAST, N_FEATURES).
      - The second dense layer has 32 units.
      - The final dense layer has 1 unit with a linear activation function to predict the future value.
  
    The model summary looks like this    
        
   |   Layer (type)  | Output Shape  | Param # |
   | --------------- | ------------- | ------- |
   | dense (Dense)   | (None, 1, 64) | 320     |
   | dense_1 (Dense) | (None, 1, 32) | 2080    |
   | dense_2 (Dense) | (None, 1, 1)  | 33      |


   Total params: 2433 (9.50 KB)              
   Trainable params: 2433 (9.50 KB)          
   Non-trainable params: 0 (0.00 Byte)
   
3. Type Of Model
   
     This model is a simple feedforward neural network (FNN) designed for
   time series forecasting. Unlike more complex models such as Long Short-
   Term Memory (LSTM) networks or Convolutional Neural Networks (CNNs)
   often used in time series forecasting, this model uses dense layers to
   make predictions.
   
4. Model Results
   
   Here is the grafik about training MAE and validation MAE with Traing loss (MSE) with validation loss
   
   ![grafik summary](https://github.com/HI-PONIC/predictHarvest/blob/master/images/Screenshot%202024-06-19%20202341.png)
   
5. Suitability

   The model is suitable for situations where:

      - The time series data is relatively simple, and the relationship between past and future values can be captured with a few dense layers.  
      - Computational resources are limited, and a simpler model is preferable.
      - Real-time prediction is required with minimal lag, as dense layers are generally faster to compute than LSTM or other recurrent layers.
        
6. How to use

   To use this model here [predict Harvest](https://github.com/HI-PONIC/predictHarvest/blob/master/saved_model/mlp13_yGRnoFeaEng(nDate).tflite), the inpute shape needs 3D array
   with the example like this
   > [[[ 20  55 150   8]]]
   
   The index input from the 3D array must contain sensor inputs sequentially from temperature, humidity, TDS, and ending with pH (each sensor input is separated by a space line)
   
   If the raw inputs are not in 3D array shape, you need to reshape it using numpy library

   ```
   inputs.reshape(1,1,4)

   ```

------------------------------

### THANK YOUUUUUUUUU !!
   
