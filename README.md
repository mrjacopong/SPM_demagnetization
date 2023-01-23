# :brain: SPM_demagnetization - ML Project
Repository made to host an university project about Machine Learning and Electric Motor Design

## :pushpin: Brief description
This report was made by Jacopo Ferretti for for the exam of Machine Learning.
I was asked to develop a project involving ML with any topic i liked. I decided to mix my knowledge in electrical machine, and to apply it with this new topic.
In this project, a ML is trained to predict how much overload current an electric motor is able to sustain before demagnetization.

## :open_file_folder: Dataset
**Dataset obtained from FEMM and Matlab.**

It was possible to create a script that simulates in FEM a randomly generated electric motor, and measure the magnetic field inside the magnets to check for demagnetization.

**What does it contains?**
It contains pseudo randomly generated motor configuration parameters, and the maximum current overload to avoid rotor demagnetization (max_OL) simulated using FEMM.

The last column (max_OL_analytical) is the maximum current overload accordingly to the analytical formula.

The dataset used has 7000 entries in total, each one representing a simulated motor.

**Main steps of the dataset generation process:**
1. Pseudo randomly generate the motor parameters and values, to be used as features.
2. Generate the motor geometry analytically.
3. Run FEM simulation of the motor.
4. Measure the magnetic field inside the magnets, and extrapolate the point where field is maximum.
5. Compare the measured field to its maximum possible value HCI .
6. Repeat measurements until demagnetization happens.
7. Save the last ”safe” current overload value that will not create overload as a label.

Features have been pseudo randomly generated: a known working motor configu ration has been chosen, where some parameters (the features) have been changed randomly in a specific range.
It was not possible to chose the features completely randomly, or some motor configuration could have been physically impractical.


The features, and their range, are:

||Feature | Mean value | Range |
| --- | --- | --- | ---|
|T_spec|Nominal Torque|150Nm| ± 75Nm|
|W_spec|Rated Speed|3.5krpm|± 1.75k rpm|
|Bmr|Magnetic Loading|0.75T|± 0.375T|
|delta|Electric Loading|4kA/m|± 2kA/m|
|m|Aspect Ratio|1.5| ± 0.75|
|S_o|Slot Opening|5mm|± 1.75mm|
|d_0|Airgap Thickness|1.2mm|± 0.42mm|
|l_magn|Magnet height|l_magn0 from calculation|l_magn0 x 1.5 ± l_magn0 x 0.1|
|h_4|Slot Opening height|2mm|± 0.7mm|
|h_3|Wedge Height|5mm|± 1.75mm|

## :blue_book: jupyter notebook
The .ipynb script shows how Dataset has been used and how the results has been obtained

## :page_facing_up: PDF Report
The attached report better explains how the code works, the engineering background and does illustrate the obtained results.

## :exclamation: disclaimer
*THIS CODE IS FOR EDUCATIONAL PURPOSES*
It is very limited, an may be "worthless" for real application: only one type of motor is used, with limited amount motor specifications, and with fixed materials.

## :star2: EASY-TO-RUN notebook in Kaggle
[Notebook](https://www.kaggle.com/code/mrjacopong/spm-demagnetization-script)
[Dataset](https://www.kaggle.com/datasets/mrjacopong/spm-demagnetization-dataset)
Enjoy it! 
