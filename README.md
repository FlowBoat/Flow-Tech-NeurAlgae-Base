# FlowTech | NeurAlgae-Base
## 2017 CWSF | HAB Prediction Using Machine Learning Algorithms

Provides a web application for interacting with NeurAlgae neural nets and displaying project information
Copyright (C) 2017 Atif Mahmud and Zachary Trefler

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

If you have comments, questions, concerns, or you just want to say 'hi',
email Zachary Trefler at zmct99@gmail.com or Atif Mahmud at atifmahmud101@gmail.com

### Introduction:
Harmful algal blooms (HABs) are sudden, rapid overgrowths of algae that can damage coastal and lakeshore ecosystems, cause socioeconomic harm to areas dependent on them, and cause serious human health issues. HAB incidence has increased worldwide in recent decades, with escalating associated costs and damage. Accurately predicting HABs before they occur could significantly mitigate these costs; however they are dependent on complex interactions among many variable factors. We investigate whether an artificial neural network could yield accurate HAB predictions. NeurAlgae is a system of Artificial Neural Networks (ANNs) that uses nine measurements from real-time ocean monitoring stations taken at 15-minute intervals over three years to train its predictions. We used a first set of networks to expand our dataset, and then a second set of recurrent networks to generate more accurate pr edictions. We tested our system with a separate subset of the data to prevent overfitting. Our system produced predictions 10 times more accurate than the only comparable machine learning-based HAB prediction tool we were able to find in the scientific literature (Zhang et al. 2016). NeurAlgae thus constitutes a novel and robust tool for HAB prediction that demonstrates the utility of ANNs in approaching a complex multivariate problem with profound human and ecological consequences.

### Method:
We developed NeurAlgae, a system of neural networks which aims to predict HAB occurrences in a given region using oceanographic data concerning that region. NeurAlgae parses nine separate water measurements (water surface level, pressure, chlorophyll concentration, temperature, electrical conductivity, oxygen and nitrate concentrations, salinity, and turbidity) taken at 15-minute intervals for three years. These measurements are correlated to three indicators of a HAB event: the probability of Pseudo-nitzschia diatoms being present in concentrations exceeding 10 000 cells per litre; the probability of the neurotoxin domoic acid (DA), being present within cells in concentrations exceeding 10 picograms per cell; and the probability of DA being present in the surrounding water in concentrations exceeding 500 nanograms per litre. The water measurements are first fed through three densely-connected ANNs of REctified Linear Units (RELUs) (with dropout and L2 regularization) trained to predict each of the three probabilities at the same time that the measurement is taken (a nowcast). The entire set of data points and correlated nowcast predictions are then fed through three more networks, each designed to make predictions for various future times. These networks took in sequential data using a Long Short-Term Memory (LSTM) layer. Combining separate neural network models allows for accurate predictions to be made on many parameters, without encountering potential training difficulties of training one large model, which the computer might not recognize as having multiple components.
	To enhance accessibility, a progressive web app (PWA) was created to host the NeurAlgae system. The web server can access and download data in real time, using a combination of client-side and server-side computation for fast and accurate results. The PWA combines the functionality of the NeurAlgae system with supplementary information to increase user understanding of the HAB issue and the NeurAlgae tool.
Training data was taken from the Central and Northern California Ocean Observing System (CENCOOS) database, measured near Morro Bay, California. The source code for NeurAlgae is available at https://github.com/FlowBoat/Flow-Tech-NeurAlgae under the GNU GPL.


### Findings and Next Steps:
Although the likeliness of our training algorithm to improve from this point on is minimal; however, moving forward we look to imrpove the accessibiltiy of our webapp by eagerly awaiting, and immediately updating to the latest patch of Keras.js. Also, by implementing a node module like Synaptic.js or TensorFlow in the web, we will be able to train our network in realtime, with a constant stream of data from CENCOOS (or other databases). Currently our only limitations are our budget, and and the scope of our imaginations. If provided access to a dedicated server, the management of the NeurAlgae database and Neural network operation becomes much more stable. As of now a standard Firebase or Heroku deployment wouldn't fit our needs as data scientists. We hope to move towards a dedicated server soon, and with it a safer future for coastlines globally.