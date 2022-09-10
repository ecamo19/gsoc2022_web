__Tasks to do:__ 

- [ ] Add the capacity to save ensemble members for all inputs, not just met drivers.

- [ ] Create a basic data frame where rows are ensemble members and columns are different inputs.

- [ ] Feed the basic data frames back into write.ensemble.configs as the sampling design and then to use that design (rather than generating samples) when that argument is present (I'd say the default would be to make that argument NULL and to generate new samples when it's NULL).

- [ ] With those first 3 tasks in place you should be well-positioned at a higher-level to work on generating the Sobol designs and postprocessing the outputs.

[Work done](https://github.com/ecamo19/gsoc_project_2022_vm/issues){ .md-button .md-button--primary }