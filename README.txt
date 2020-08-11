****** 
We are not submitting any datasets. We are using torch's built in Fashion-MNIST dataset loader.

******

Following instructions are meant for running the code on Google Colab

===============================================================
PREREQUISITE

1. Change runtime environment to GPU on a Google Colab session
2. Open the notebook and run the first cell in the notebook. After it finishes make sure to Restart Runtime. This cell will install PySyft.
3. Run cells 2, 3, and 4 for installing and importing required libraries.
4. Run cell 6, Class Arguments to create an Arguments object. Depending on the scenario that you want to run change following settings:
	a). self.epochs: Set this to the desired number of epochs you want each agent to train. The default value is set to 5.
	b). self.lr: Set this to the desired learning rate. We tested with various learning rates and 0.004 turned out to be the optimum to work with the scenarios.
	c). self.momentum: SGD momentum. The value is set to 0.9 by default. You can choose any value between 0 and 1. We tried with 0.5, 0.9 and 0.99.
	d). self.prevent_attack: If you want to run the code with attack prevention turned on set this paramter to True, otherwise set it to False.
	e). self.shuffle: By default this is set to True. If you don't want to shuffle training examples between timestamps set this to False. Note if you choose "True" for 					self.single_example then set this parameter to "False". This will ensure the malicious agent trains on the same single example in every timestamp.
	f). self.timestamps: This parameter specifies the number of timestamps you want to run the experiment. The default value is 12.
	g). self.single_example: By default this is set to False. If you want to run the test with single example misclassification set this parameter to True.
	h). self.malicious_agents: Specify one or more malicious agents in this parameter. The valid values for this list are "Agent_1", "Agent_2", "Agent_3", "Agent_4", "Agent_5", 				"Agent_6", "Agent_7", "Agent_8", "Agent_9", "Agent_10". The scenarios that we tested had a maximum of 3 malicious agents. You do not need to specify benign agents. Any agent 		that is not specified as malicious is treated as a benign agent.
	i). Leave other parameters to their default values.

3. Run other remaining cells sequentially till you reach the last cell. The last cell will start the code. When it finishes it will print two graphs. One which has global model's accuracy on test data and another that plots distribution of the weight deltas of the benign and malicious agent. Note that the weight delta distribution plot will be plotted only if you have set the self.single_example parameter to True.

===============================================================

We used following settings for the 4 scenarios:

Scenario 1:

self.epochs: 5
self.lr: 0.004
self.momentum: 0.9
self.prevent_attack: True (for attack prevention) and False (for no attack prevention)
self.shuffle: True
self.timestamps: 12
self.single_example: False
self.malicious_agents: [Agent_10]

Scenario 2:

self.epochs: 5
self.lr: 0.004
self.momentum: 0.9
self.prevent_attack: True (for attack prevention) and False (for no attack prevention)
self.shuffle: True
self.timestamps: 12
self.single_example: False
self.malicious_agents: [Agent_10, Agent_5]

Scenario 3:

self.epochs: 5
self.lr: 0.004
self.momentum: 0.9
self.prevent_attack: True (for attack prevention) and False (for no attack prevention)
self.shuffle: True
self.timestamps: 12
self.single_example: False
self.malicious_agents: [Agent_10, Agent_5, Agent_4]

Scenario 4:

self.epochs: 5
self.lr: 0.004
self.momentum: 0.9
self.prevent_attack: True (for attack prevention) and False (for no attack prevention)
self.shuffle: False
self.timestamps: 12
self.single_example: True
self.malicious_agents: [Agent_10]

