# Power and Effect Size Checkpoint

1. What is the relationship between power and the false-negative rate, $\beta$ ?


```python

# Power is simply 1 less the false-negative rate, 1 - beta.
```

Calculate and evaluate Cohen's *d* for two groups.

Suppose we have the following samples of ant body lengths in centimeters, taken from two colonies that are distinct but spatially close to one another.

2. Calculate Cohen's *d* for these groups.


```python

pooled_stdev = np.sqrt((2*group1_var + 2*group2_var) / 4)

d = (group2.mean() - group1.mean()) / pooled_stdev
d
```

3. Is this a large effect size? What conclusion should we draw about these two samples?


```python

# This is a huge effect size, but we have to be careful about drawing
# conclusions about the relationship between the two colonies (that
# the colonies contain distinct populations of ants, for example), since
# we have such small sample sizes.
```

4. We decide we want to collect more data to have a more robust experiment. Given the current effect size, calculate how many observations we need (of each ant colony) if we want our test to have a power rating of 0.9 and a false-positive rate of 5%.


```python

power.TTestIndPower().solve_power(effect_size=d,
                                  alpha=0.05,
                                 power=0.9)
```

Suppose we gather more data on our ants and then re-visit our calculations. 

5. Do a two-tailed t-test on these two colonies' lengths.


```python

stats.ttest_ind(col1['col1_length'], col2['col2_length'])
```

6. What should we conclude about these two collections of ant body lengths?


```python

# The p-value is now quite large, and so we cannot reject the null
# hypothesis that says that there is no difference between the body
# lengths in the two ant colonies.
```
