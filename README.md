# The Canonical Interval Forest (CIF) Classifier for Time Series Classification

Results for the paper "The Canonical Interval Forest (CIF) Classifier for Time Series
Classification" published at the 2020 IEEE International Conference on Big Data, which
introduces CIF, an interval based classifier using the catch22 features, and HIVE-COTE
with CIF replacing TSF (HC-CIF). CIF is evaluated on 112 univariate UCR datasets and 26
multivariate UEA datasets.

The paper is available from [IEEE](https://doi.org/10.1109/BigData50022.2020.9378424)
and [arXiv](https://arxiv.org/abs/2008.09172).

## Contents

| Path | Description |
|---|---|
| [results/univariate](results/univariate) | Test accuracy of CIF and the other classifiers on the UCR datasets, used in the univariate comparisons (i.e. Figures 4, 9 and 11) |
| [results/univariate/AllMetrics.xlsx](results/univariate/AllMetrics.xlsx) | Accuracy, balanced accuracy, AUROC and F1 on the UCR datasets, averaged over 30 resamples and on the default train/test split, with average ranks |
| [results/multivariate](results/multivariate) | Test accuracy of CIF and the other classifiers on the UEA datasets (Figure 8) |
| [results/multivariate/AllMetrics.xlsx](results/multivariate/AllMetrics.xlsx) | Accuracy, balanced accuracy, AUROC and F1 on the UEA datasets on the default train/test split |
| [cif.ipynb](cif.ipynb) | Example of using CIF from `aeon` |

The `<classifier>TestAcc.csv` files have one row per dataset and one column per
resample, with 30 resamples in total. Resample 0 is the default train/test split. The
`MeanTestAcc<classifier>.csv` files have the accuracy averaged over the resamples.
`Hybrid` is the hybrid of TSF and catch22 compared in Figure 3, and `CIF+Bagging` and
`CIF+TrainBagging` are CIF variants using bagging.

More results, the code and a snapshot of the `tsml` toolkit used in the experiments are
available on Google Drive:

- Detailed results files for each classifier and dataset on 30 resamples for the
  [univariate](https://drive.google.com/file/d/1fn_0FS3rWRk10gqfuS8AFTgR2IevhflW/view)
  and [multivariate](https://drive.google.com/file/d/1M4R0ThYK8ozQes-g2VDppT7PfmSvSWqT/view)
  datasets, which can be processed with the `MultipleClassifierEvaluation` class in
  `tsml`
- [Code used to produce the experiments](https://drive.google.com/file/d/1YkGKccWvYU7NWxIQ-g9IfASnDx3vMfQx/view)
  and the [code as a jar](https://drive.google.com/file/d/16QhHAUx19GEA56Pzka34vjgx7Ky_WafT/view)

## Datasets

The 112 equal length univariate datasets without missing values are from the
[UCR Time Series Classification Archive 2018](https://doi.org/10.5281/zenodo.11198697),
and the 26 equal length multivariate datasets are from the
[UEA Multivariate Time Series Classification Archive](https://www.timeseriesclassification.com/dataset.php).
Both are also available as used in the experiments from Google Drive:
[univariate](https://drive.google.com/file/d/1wCXkHAbqWCkzVo6cqf7XDMSVqcfWdQWO/view) and
[multivariate](https://drive.google.com/file/d/1a_2WVTveWdwK7ykzwxofKjr9B8HmCja7/view).

## Running CIF

### aeon

CIF is available in the [aeon](https://github.com/aeon-toolkit/aeon) Python package as
`CanonicalIntervalForestClassifier`, and the catch22 features as `Catch22`. They follow
the `scikit-learn` interface:

    pip install -r requirements.txt

See [cif.ipynb](cif.ipynb) for an example, which can be run online using Binder:

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/time-series-machine-learning/canonical-interval-forest-2020/main?filepath=cif.ipynb)

The example was last checked in November 2026 with `aeon` 1.5.0 on Python 3.12.

### As published

The paper used the Java implementations of CIF and catch22 in the
[tsml](https://github.com/time-series-machine-learning/tsml-java) toolkit, which uses
the WEKA classifier interface. The code and jar used in the experiments are linked
above.

## Citation

If you use this work, please cite the paper:

```bibtex
@inproceedings{middlehurst2020canonical,
  title={The Canonical Interval Forest ({CIF}) Classifier for Time Series Classification},
  author={Middlehurst, Matthew and Large, James and Bagnall, Anthony},
  booktitle={2020 IEEE International Conference on Big Data (Big Data)},
  pages={188--195},
  year={2020},
  publisher={IEEE},
  doi={10.1109/BigData50022.2020.9378424}
}
```

## Contact

For questions about the paper or this repository, feel free to contact any of the
authors. Matthew Middlehurst can be reached at
[m.b.middlehurst@bradford.ac.uk](mailto:m.b.middlehurst@bradford.ac.uk) or on the
[aeon Discord](https://discord.gg/D6rzqHGKRJ) (`matthewmiddlehurst`).
