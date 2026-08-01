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
shiny::runGitHub("New_shiny_app", "DevGenBasel", script = "new_shiny_app.R")
