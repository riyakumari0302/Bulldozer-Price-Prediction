## Conclusion

- There is some of sort of doubt for `YearMade` column where values are equal to 1000. By contacting subject matter expert help to understand more

- `RandomForestRegressor()` works far better than `Ridge()`, `Lasso()`, `ElasticNet()`
- By applying RandomizedSearchCV and GridSearchCV we get our best parameters for our RandomForestRegressor model.
```
    n_estimators=50,
    min_samples_leaf=1,
    min_samples_split=12,
    max_features=0.5
    
  ```
- Our model's evaluation score:
  - R2_Score => 0.882327
  - MSLE => 0.060891
  - RMSLE => 0.246760
  - MAE => 5955.706156

- **Root mean squared log error is 0.2468
