---
layout: post
title: Simple Finance Prediction using Deep Learning
date: 2018-05-06 00:00:00 +0300
description: A simple algorithm in Python to predicte the finance # Add post description (optional)
img: machine-learning-finance_title.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Deep Learning, Finance, Prediction, Python]
---

Currently, a big amount of financial negotiations are already made by computers, which take into account several factors (news, market turmoil, past quotations) and try to predict future movements of the assets. These algorithms add liquidity money to the market.

This project is a just simple prediction using Deep Learning. The data used for training and network accuracy testing are a historical data that it was get from Yahoo finance.


The neural network was designed to predict the quotation of the day using the past 30 adj. close (the features). However, it does not make sense to judge the network based only on the adj. close price, because many factors can influence the closing value.
This neural network has 2 internal layers, the first with 10 and the second with 5 neurons, the learning rate of 0.001, with cost function Mean Squared Error, iterating 7000 times. The modification of the biases's layers are constant and the wheight use the normal distribution with 0 mean and 0.1 of standard deviation.
it was used the libraries Pandas, Tensorflow, numpy and others.


## Code

{% highlight python %}


import datetime as dt
from datetime import datetime
from matplotlib import style
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import tensorflow as tf

import os
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '2'

import time

#plot the OHLC CHART FINANCES
#from matplotlib.finance import candlestick_ohlc
from mpl_finance import candlestick_ohlc
import matplotlib.dates as mdates



#data -> is the read data from the file chosen
#new_data -> is the new data with just the item in the period of time chosen





data = pd.read_csv('sp500.csv')  #reading the file for analysis
start_date = dt.datetime(2010, 1, 1)  # start date of the period of time for analysis
end_date = dt.datetime(2017, 6, 16)   # end date of the time's period for analysis
new_data = pd.DataFrame(columns=['Date', 'Open', 'High', 'Low', 'Close', 'Adj Close', 'Volume'])  # Titles

id = 0 #id is the variable to do the adjustiment of the new datas ID
data['Date'] = pd.to_datetime(data['Date'])
for i, r in enumerate(data['Date']):
    if r > start_date and r < end_date:
        new_data.loc[id] = data.loc[i]
        id += 1


#print(new_data)
#new_data.plot(x='Date', y='Volume')
#plt.show()

#Spliting Test, Train

close_data = new_data['Adj Close']
n_input = 30
training = 0.8
n_data = len(close_data)
x_data=[]
y_data=[]
x_train=[]
y_train=[]
x_test=[]
y_test=[]

#  getting the features and labels
for i in range(n_data-n_input):
    x_data.append(close_data[i:(i+n_input)])
    y_data.append(close_data[n_input+i])

n_training = int(n_data*training)
x_train = x_data[0:n_training]
y_train = y_data[0:n_training]

x_test = x_data[n_training+1:]
y_test = y_data[n_training+1:]

x_train = np.array(x_train)
#y_train = np.array(y_train)
y_train = np.array(y_train).transpose().reshape((len(y_train),1))
x_test = np.array(x_test)
y_test = np.array(y_test).transpose().reshape((len(y_test),1))


# REDE NEURAL FEEDFORWARD
n_nodes_hl1 = 10
n_nodes_hl2 = 5

n_classes = 1

batch_size = x_train.shape[0]
hm_epochs = 7000

x = tf.placeholder('float')
y = tf.placeholder('float')

def neural_network_model(data):
    hidden_1_layer = {'f_fum': n_nodes_hl1,
                      'weight': tf.Variable(tf.truncated_normal([len(x_train[0]), n_nodes_hl1], mean=0.0, stddev=0.1)),
                      'bias': tf.Variable(tf.constant(0.1, shape=[n_nodes_hl1]))}

    hidden_2_layer = {'f_fum': n_nodes_hl2,
                      'weight': tf.Variable(tf.truncated_normal([n_nodes_hl1, n_nodes_hl2], mean=0.0, stddev=0.1)),
                      'bias': tf.Variable(tf.constant(0.1, shape=[n_nodes_hl2]))}

    output_layer = {'f_fum': None,
                    'weight': tf.Variable(tf.truncated_normal([n_nodes_hl2, n_classes], mean=0.0, stddev=0.1)),
                    'bias': tf.Variable(tf.constant(0.1, shape=[n_classes])), }

    l1 = tf.add(tf.matmul(data, hidden_1_layer['weight']), hidden_1_layer['bias'])
    l1 = tf.nn.relu(l1)

    l2 = tf.add(tf.matmul(l1, hidden_2_layer['weight']), hidden_2_layer['bias'])
    l2 = tf.nn.relu(l2)

    output = tf.add(tf.matmul(l2, output_layer['weight']), output_layer['bias'])

    return output


def train_neural_network(x):
    prediction = neural_network_model(x)
    # cost = tf.reduce_mean( tf.nn.softmax_cross_entropy_with_logits(logits=prediction,labels=y) )
    cost = tf.reduce_mean(tf.squared_difference(prediction, y))
    optimizer = tf.train.AdamOptimizer(learning_rate=0.001).minimize(cost)

    with tf.Session() as sess:
        sess.run(tf.global_variables_initializer())


        for epoch in range(hm_epochs):
            epoch_loss = 0
            i = 0
            while i + batch_size <= len(x_train):
                start = i
                end = i + batch_size
                batch_x = np.array(x_train[start:end])
                batch_y = np.array(y_train[start:end])
                # if epoch == 0: print 'BATCH_X:', batch_x.shape, batch_x; print 'BATCH_Y:', batch_y.shape, batch_y

                _, c = sess.run([optimizer, cost], feed_dict={x: batch_x,
                                                              y: batch_y})
                epoch_loss += c
                i += batch_size

            print('Iteração %4d' % (epoch + 1), 'de', hm_epochs, 'Erro:', epoch_loss)
            epoch += 1

            #correct = tf.equal(tf.argmax(prediction, 1), tf.argmax(y, 1))
            #accuracy = tf.reduce_mean(tf.cast(correct, 'float'))
            # print('Accuracy:', accuracy.eval({x: y_test, y:prediction}))

        out = sess.run([prediction], feed_dict={x: x_test})

        mse = 0
        points_pred = 0
        t = range(len(out[0]))

        for i in t:
            #print ('CURRENT:  ', x_test[i][0])
            #print ('PREDICTED:', out[0][i])
            #print ('EXPECTED: ', y_test[i], '\n')


            mse = mse + abs((out[0][i] - y_test[i]))
            if abs((out[0][i] - y_test[i])) < (y_test[i]*0.01):
                points_pred += 1

        mse = mse / len(out[0])
        accuracy = (points_pred / len(out[0]))*100

        print("MSE: ", mse)
        print("\n\nAccuracy: ", accuracy, "%")

        plt.plot(t, out[0], color='red', label='Prediction')
        plt.plot(t, y_test, color='blue', label='Data')
        plt.xlabel('Date')
        plt.ylabel('Prices (Close)')
        plt.show()

def plot_OHLC(ohlc_data):
    # convert date format for ohlc to operate
    ohlc_data['Date'] = ohlc_data['Date'].map(mdates.date2num)

    #print(ohlc_data.head(10))
    ohlc = new_data[['Date', 'Open', 'High', 'Low', 'Close']]

    f1, ax = plt.subplots(figsize=(10, 5))

    # plot the candlesticks
    candlestick_ohlc(ax, ohlc.values, width=.6, colorup='green', colordown='red')
    ax.xaxis.set_major_formatter(mdates.DateFormatter('%Y-%m'))

    plt.show()


#plot_OHLC(new_data)

train_neural_network(x)
plot_OHLC(new_data)


#=> prints MSE:  [16.22116169] and Accuracy:  68.98550724637681 %

{% endhighlight %}


## Results


![Prediction]({{site.baseurl}}/assets/img/candle.png)
this is the candle stick of the data


![Prediction]({{site.baseurl}}/assets/img/prediction.png)
the blue line is the adj. close and the red line is the prediction of the adj. close



