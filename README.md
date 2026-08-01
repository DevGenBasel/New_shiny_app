# Single-Cell RNA-Seq Data Visualization SOP

This document guides you through using the Shiny app to explore single-cell RNA sequencing (scRNA-seq) data. The app allows you to select local or server dataset files, visualize gene expression, compare cell groups, and identify differentially expressed genes.

---

## Part 1: Setting Up Your Environment (One-Time Setup)

1. **Install R:**
   * Go to [CRAN](https://cran.r-project.org/).
   * Select the link for your operating system (Windows, macOS, or Linux).
   * Download and install the latest version of R following the on-screen instructions.

2. **Install RStudio:**
   * Go to [Posit RStudio Desktop](https://posit.co/download/rstudio-desktop/).
   * Download and install the free RStudio Desktop version for your operating system.

3. **Install Xcode (macOS users):**
   * Go to the Mac App Store and download Xcode. Install the application.

---

## Part 2: Running the App

1. Open **RStudio**.
2. Run the App: In the RStudio Console (usually the bottom-left panel), copy and paste the following command, then press **Enter**:

```r
install.packages("shiny") #only do it once
shiny::runGitHub("New_shiny_app", "DevGenBasel", ref = "main")

## Part 3: Using the App

The app interface consists of a **Sidebar** on the left and a **Main Panel** on the right.

### Sidebar (Left Side)

* **Load Dataset:**
  * **Select .rds File:** Click to open the interactive file browser. Navigate to your dataset file (`.rds` or `.RData`) on your local machine or mounted server volume and click select. 
  * Below the button, a status message will confirm the loaded file name.
* **Download Dimplot:** Download the main UMAP DimPlot as a PDF.
* **Differential Expression:**
  * **Select Identity:** Choose a cell type or cluster to analyze (e.g., `C1`, `C2`, `M1`). *Options load automatically after dataset selection.*
  * **Genotype 1:** Select the baseline comparison group (e.g., `1_wt`).
  * **Genotype 2:** Select the target comparison group (e.g., `2_E1C8`).
  * **Run Differential Expression:** Click to calculate differentially expressed genes between the two selected groups (a progress bar will track computation).
  * **Download DE Results:** Download the DE analysis table as a CSV.
  * **Download DE Volcano Plot:** Download the current volcano plot as a PDF.
* **FeaturePlot & VlnPlot Inputs:**
  * **Enter Gene Name:** Type the gene name (e.g., `Tfap2b`). Ensure correct capitalization.
  * **Update Plot:** Click to update both the FeaturePlot and VlnPlot.
  * **Download Featureplot / Vlnplot:** Save the individual plots as PDFs.
* **Scatter Plot Inputs:**
  * **X-axis Gene / Y-axis Gene / Color by Gene:** Enter genes for multi-gene expression scattering.
  * **Cells expressing 3 genes:** View cell counts expressing all three genes across genotypes.
  * **Download Scatterplot:** Save the generated scatter plot as a PDF.
* **Total Cells per Genotype:** Displays total cell counts across experimental conditions.
* **Cell Count by Genotype:**
  * **Enter Gene Name:** Type a gene name to generate a summary table of positive expressing cells per genotype.

---

### Main Panel (Right Side)

* **Dimplot:** Primary dimensional reduction plot grouping cells by cluster identity.
  * **Show Heatmap:** Generates a modal displaying a heatmap of the top 10 marker genes per cluster.
  * **Download Markers:** Save the calculated cluster marker table as a CSV.
* **Volcano Plot:** Displays after running Differential Expression. Shows fold changes ($\log\text{FC}$) vs. significance ($-\log_{10}\text{padj}$). Use the numeric input boxes below the plot to adjust X and Y axis bounds dynamically.
* **FeaturePlot:** Maps single-gene expression onto cluster coordinates.
  * **Split view by genotype:** Displays a modal pop-up with expression split across experimental genotypes (downloadable as PDF).
* **VlnPlot:** Visualizes gene expression distribution across clusters.
  * **Split view by genotype:** Displays a modal pop-up with violin distributions separated by genotype (downloadable as PDF).
* **Scatterplot:** Displays co-expression relationship of specified X, Y, and Color genes faceted by genotype.
* **Blended FeaturePlot:** Overlays expression of two distinct genes simultaneously.
  * Enter **Gene 1** and **Gene 2**, customize expression colors, and click **Update Blended Plot**.
  * Use **Split view by genotype** to inspect blended expression side-by-side across conditions.
* **Differential Expression Results:** Interactive data table displaying ranked DE genes, test statistics, and significance values.

---

## ⚠️ Important Notes

* **Load File First:** All plots and dynamic dropdown menus depend on loading your dataset using the **Select .rds File** button first.
* **Case Sensitivity:** Gene names are case-sensitive (e.g., `Sox9` vs `sox9`).
* **Computation Time:** Operations like *Run Differential Expression* and *Show Heatmap* perform real-time calculations. Please wait for the progress bar to finish.
* **Error Messages:** If a plot returns a `"Gene not found"` error, verify the exact spelling and symbol format used in your dataset.
