# Premier_Exercice.R
######Courbe de la fonction
# Pour rendre le graphe interactif
install.packages("plotly")
library(plotly)
library(magrittr)  # Load the magrittr package

# Create the interactive 3D plot
# Expression de la fonction
f <- function(x, y) {
  x*x + cos(x+y) + (y*y + (1/(1 + x*x)))^0.5
}
# Délimitation des intervalles
x <- seq(-10, 10, 0.1)  # Séquence de -10 à 10 avec un pas de 0.1
y <- seq(-10, 10, 0.1)  # Séquence de -10 à 10 avec un pas de 0.1
z <- outer(x, y, f)

# Création du graphique
plot_ly(x = x, y = y, z = z, type = "surface") %>%
  layout(title = "Courbe de la fonction")

######Courbe de la dérivée première par rapport à x
D(expression(x*x + cos(x+y) + (y*y + (1/(1 + x*x)))^0.5), "x")
# Pour rendre le graphe interactif
library(plotly)
library(magrittr)  # Load the magrittr package

# Create the interactive 3D plot
# Expression de la fonction
f <- function(x, y) {
  x + x - sin(x + y) - 0.5 * ((x + x)/(1 + x * x)^2 * (y * y + (1/(1 + x * x)))^-0.5)
}
# Délimitation des intervalles
x <- seq(-10, 10, 0.1)  # Séquence de -10 à 10 avec un pas de 0.1
y <- seq(-10, 10, 0.1)  # Séquence de -10 à 10 avec un pas de 0.1
z <- outer(x, y, f)
# Création du graphique
plot_ly(x = x, y = y, z = z, type = "surface") %>%
  layout(title = "Courbe de la dérivée première par rapport à x")

######Courbe de la dérivée première par rapport à y
D(expression(x*x + cos(x+y) + (y*y + (1/(1 + x*x)))^0.5), "y")
# Pour rendre le graphe interactif
library(plotly)
library(magrittr)  # Load the magrittr package

# Create the interactive 3D plot
# Expression de la fonction
f <- function(x, y) {
  0.5 * ((y + y) * (y * y + (1/(1 + x * x)))^-0.5) - sin(x + y)
}
# Délimitation des intervalles
x <- seq(-10, 10, 0.1)  # Séquence de -10 à 10 avec un pas de 0.1
y <- seq(-10, 10, 0.1)  # Séquence de -10 à 10 avec un pas de 0.1
z <- outer(x, y, f)

# Création du graphique
plot_ly(x = x, y = y, z = z, type = "surface") %>%
  layout(title = "Courbe de la dérivée première par rapport à y")

####minimum et maximum de la fonction
# Créer une grille de points
x_vals <- seq(-8, 8, length.out = 100)
y_vals <- seq(-8, 8, length.out = 100)
grid <- expand.grid(x = x_vals, y = y_vals)

# Calculer les valeurs de la fonction
grid$f_values <- f(grid$x, grid$y)

# Trouver le maximum et le minimum
max_value <- max(grid$f_values)
min_value <- min(grid$f_values)
max_point <- grid[grid$f_values == max_value, c("x", "y")]
min_point <- grid[grid$f_values == min_value, c("x", "y")]

# Afficher le résultat
print(paste("Maximum value of f(x, y):", max_value))
print(paste("Coordinates of maximum point:", max_point))
print(paste("Minimum value of f(x, y):", min_value))
print(paste("Coordinates of minimum point:", min_point))
