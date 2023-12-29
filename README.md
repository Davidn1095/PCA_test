# PCA_test

### Reading Data and Setup:

- `datos <- read.table("comprincipales.txt", header = T, row.names = 1)`: Reads data from a text file "comprincipales.txt" into a DataFrame `datos`. The first row is treated as header and the first column as row names.
- `attach(datos)`: Attaches the `datos` DataFrame to the R search path, allowing direct access to its variables.

### Data Summary and Initial Plotting:

- `summary(datos)`: Provides a summary of `datos`, such as min, max, median, mean, and quartiles for each variable.
- `plot(datos)`: Plots the data in `datos`. This will typically produce a multi-panel plot with each variable plotted against every other variable.
- `cor(datos)`: Calculates the correlation matrix for the variables in `datos`.

### Principal Component Analysis (PCA) using ade4 Package:

- `library(ade4)`: Loads the `ade4` package, which provides methods for multivariate data analysis.
- `acp <- dudi.pca(df = datos, scannf = T, nf = 2)`: Performs PCA on `datos`. `scannf = T` prompts the user to choose the number of axes, while `nf = 2` specifies using two dimensions.

### Inertia and Labeling in PCA:

- `acpi <- inertia.dudi(acp, row.inertia = T, col.inertia = T)`: Calculates the inertia for both rows and columns in the PCA.
- `acpi`: Displays the calculated inertia.
- `s.label(acp$li)`: Plots the row scores (individuals) of the PCA.
- `s.label(acp$co)`: Plots the column scores (variables) of the PCA.
- `biplot(acp$co, acp$li)`: Produces a biplot of the PCA showing both individuals and variables.
- `s.corcircle(acp$li)`: Draws a correlation circle for the row scores.
- `s.corcircle(acp$co)`: Draws a correlation circle for the column scores.

### Correlation Visualization and Further PCA Analysis:

- `library(corrplot)`: Loads the `corrplot` package for visualizing correlation matrices.
- `corrplot(cor(datos), sig.level = 0.05, typ = "lower")`: Creates a correlation plot of `datos`, showing only the lower triangle and highlighting significant correlations at the 0.05 level.
- `library(factoextra)`: Loads the `factoextra` package for extracting and visualizing the results of multivariate data analyses.
- `fviz_eig(acp, addlabels = TRUE, ylim = c(0, 85))`: Visualizes the eigenvalues (variances) of the PCA, showing how much variance each principal component captures.
- `fviz_pca_var(acp, col.var = "cos2", gradient.cols = c("#00AFBB", "#E7B800", "#FC4E07"), repel = TRUE)`: Creates a variable plot for the PCA, showing the quality of representation on the principal components and using color gradients to indicate the cos2 (quality of representation).

