import pandas as pd
import numpy as np
import plotly.graph_objs as go
from sklearn.preprocessing import StandardScaler

# Load the data
file_path = "/Users/Perso/Desktop/PCA variables.xls"
df = pd.read_excel(file_path)

# List of variables to include in PCA
variables = [
    'stdpercapffl', 'stdhunting', 'stdpercapgunsandammo', 
    'stdratioamericanhunter', 'stdpercaplonggunchecks', 'stdpercapnra', 
    'stdpercaphandgunchecks', 'stdsyg', 'stdratioamericanrifleman', 
    'stdratioa1f', 'stdassault'
]


# Renaming variables for understandable names
variable_names = {
    'stdpercapffl': 'Per Capita Federally Licensed Gun Dealers',
    'stdhunting': 'Per Capita Licensed Hunters',
    'stdpercapgunsandammo': 'Per Capita Guns & Ammo Subscribers',
    'stdratioamericanhunter': 'Ratio of American Hunter Readers',
    'stdpercaplonggunchecks': 'Per Capita Long Gun Background Checks',
    'stdpercapnra': 'Per Capita NRA Membership',
    'stdpercaphandgunchecks': 'Per Capita Handgun Background Checks',
    'stdsyg': 'Presence of Stand-Your-Ground Law',
    'stdratioamericanrifleman': 'Ratio of American Rifleman Readers',
    'stdratioa1f': 'Ratio of America’s 1st Freedom Readers',
    'stdassault': 'Presence of State Assault Weapon Ban'
}

# Standardize the data
scaler = StandardScaler()
X_std = scaler.fit_transform(df[variables])

# Compute the correlation matrix
corr_matrix = np.corrcoef(X_std, rowvar=False)

# Eigen decomposition
eigen_values, eigen_vectors = np.linalg.eigh(corr_matrix)

# Sort the eigenvalues and eigenvectors in descending order
sorted_index = np.argsort(eigen_values)[::-1]
sorted_eigenvalue = eigen_values[sorted_index]
sorted_eigenvectors = eigen_vectors[:, sorted_index]

# Select the top n eigenvectors (n=3 here)
n_components = 3
eigenvector_subset = sorted_eigenvectors[:, 0:n_components]

# Plot PCA loadings
loadings = eigenvector_subset

# Create a 3D scatter plot with Plotly
fig = go.Figure()

# Adding PCA loadings with variable names as hover text
for i, var in enumerate(variables):
    hover_text = f"{variable_names[var]}<br>Recreational: {loadings[i, 0]:.2f}<br>Self-defense: {loadings[i, 1]:.2f}<br>Second Amendment: {loadings[i, 2]:.2f}"
    fig.add_trace(go.Scatter3d(
        x=[loadings[i, 0]],
        y=[loadings[i, 1]],
        z=[loadings[i, 2]],
        mode='markers',
        marker=dict(size=5, opacity=0.8),
        text=hover_text,
        hoverinfo='text'
    ))

# Update the layout
fig.update_layout(
    scene=dict(
        xaxis_title='Recreational',
        yaxis_title='Self-defense',
        zaxis_title='Second Amendment'
    ),
    title='PCA Loadings using Correlation Matrix'
)

# Update the layout to remove the legend
fig.update_layout(showlegend=False)

# Show the plot
fig.show()
