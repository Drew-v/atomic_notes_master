1. Insufficient training data: simple problems  require thousands of samples, more complex problems for example [[speech recognition]], require millions of samples
2. Non-representative training data: if data isn't representative of new cases which will be 
    predicted on, then performance will be poor compared to training performance 
	- small samples have **[[sampling noise]]** (non representative data as result of chance)
	- large samples can be non-representative if sampling method was flawed, called **[[sampling bias]]**
3. Poor quality data
	- outliers causing problems
	- samples missing features
		- Delete them or manual fill them
4. Irrelevant features and [[feature engineering]]
	- garbage in garbage out as saying goes
	- must have relevant features, irrelevant features can drag the model down
	- Some models have trouble with features which linearly correlate together
5. **[[machine learning - overfitting data]]** 
	- good performance on training data, poor generalization to new data
6. **[[underfitting training data]]
	- bad performance on training, generalizes poorly as well
7. Data mismatch:
	- when model is not generalizing well, it could be because of overfitting or because training data was not representative of real world data. Usage of the train-dev set can alleviate this ambiguous situation. 