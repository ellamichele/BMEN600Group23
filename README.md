# Cross-region gene-expression prediction in brain tissue from held-out GTEx donors

**BMEN 600 · Group 23**  
Arai Jenkins, Dianna Prawdzik, Ella Stokowski, and Jake Gibbs

## Research question

**How accurately can gene expression in one human brain region predict expression in another in unseen GTEx donors, and how does predictive performance vary across region pairs?**

When target-region measurements are unavailable, regional expression proxies could support transcriptomic research. We used ridge regression to compare six prediction directions across caudate/putamen, cortex/frontal cortex (BA9), and cerebellum/cerebellar hemisphere. Prediction performance was evaluated in donors excluded from model development.

## Repository files

| File | Purpose |
| --- | --- |
| [GTEx_Final_Analysis_.ipynb](GTEx_Final_Analysis_.ipynb) | Complete preprocessing, modelling, evaluation, sensitivity analysis, and output generation. |
| `README.md` | Dataset access, setup, reproduction steps, and output map. |

The notebook filename includes an underscore before `.ipynb`. Generated files are saved in the runtime. The paper is submitted separately.

## Dataset and access

We used GTEx V11 gene-read-count data, with 3,030 tissue records from 385 donors across 12 brain regions. Cervical spinal cord was excluded. Donors are independent cases and can contribute samples from multiple regions. Models use donor-matched region pairs.

- Official source: [GTEx bulk tissue expression downloads](https://gtexportal.org/home/downloads/adult-gtex/bulk_tissue_expression).
- Exact input: [gene_reads_GTEx.zip](https://github.com/ellamichele/BMEN600Group23/releases/download/v1.0-data/gene_reads_GTEx.zip), release `v1.0-data`.
- SHA-256: `b5e3418a3b880796845a6bd5f7fd01f4856dfc97655bfb4fea6502c8721533b4`.

Processed counts and de-identified annotations are open access. Raw sequences and full donor metadata require separate authorization. The [GTEx licence](https://gtexportal.org/home/license) requires acknowledgement, prohibits implying endorsement, and requires current redistributed data or clear disclosure that the version differs from current data.

## Software and setup

Use Google Colab with a Python CPU runtime. Required packages are NumPy, pandas, SciPy, scikit-learn, Matplotlib, Requests, threadpoolctl, and IPython. If packages are missing, run this before the imports:

```python
%pip install numpy pandas scipy scikit-learn matplotlib requests threadpoolctl ipython
```

This command installs unpinned packages. The notebook prints active versions and exports exact versions to `requirements.txt` and `audit/run_manifest.json`. Retain these records with the results. The saved execution records Python 3.13.18 and scikit-learn 1.6.1.

## Run the analysis

1. Open the [notebook in Colab](https://colab.research.google.com/github/ellamichele/BMEN600Group23/blob/main/GTEx_Final_Analysis_.ipynb).
2. Connect to a CPU runtime and select **Runtime → Run all**.
3. The notebook downloads and verifies the archive. If downloading fails, upload the exact archive linked above to `/content/gene_reads_GTEx.zip`, then rerun from the verification cell.
4. Confirm Section 5 reports `All 60 evaluations complete; donor separation and reciprocal matching verified.` Allow the remaining cells to finish.
5. Download the archives and save the executed notebook. Colab runtime files are temporary.

Results are written to `/content/gtex_arai_results/`. Five repeated 80/20 donor holdouts use seeds 42, 142, 242, 342, and 442, with three-fold internal cross-validation. Gene selection and scaling use training donors. Seed 42 is the reference split. The common-target analysis evaluates sensitivity to target-gene selection.

## Outputs and paper mapping

Paths below are relative to the results directory.

| Paper output | Where to find it |
| --- | --- |
| Table 1 regional totals | Section 2: `tables/table_1_dataset.csv`. Sex counts are reported separately and are not generated here. |
| Table 2 donor counts | Section 5: `tables/table_2_primary_reference.csv`. |
| Table 3 five-split performance | Section 5: primary rows of `tables/table_3_split_sensitivity.csv`; MAE/RMSE summary cell after Section 6. All individual split metrics are in `tables/all_split_metrics.csv`. |
| Figure 2 reference prediction | `figures/figure_2_primary_prediction.png` and `.svg`; seed-42 values and intervals are in `table_2_primary_reference.csv`. |
| Figure 3 sensitivity | `figures/figure_3_sensitivity.png` and `.svg`; all five splits and both target-selection approaches. |

Section 6 generates figures; the final cell refines their layouts. Section 7 exports settings and software records. Audit files retain donor partitions, selected genes, and tuning losses. Models and predictions are exported separately.

Download `/content/GTEx_Report.zip` for final figure layouts. `/content/GTEx_Arai_Results.zip` includes models and predictions but is assembled before the final layout updates.

## Analysis version

Documented notebook version: [commit c2123c2ca39d82e53c32b2bf0442428420ba09a6](https://github.com/ellamichele/BMEN600Group23/commit/c2123c2ca39d82e53c32b2bf0442428420ba09a6). Record the actual final submitted commit in the paper's Data and Code Availability statement after uploading final revisions.
