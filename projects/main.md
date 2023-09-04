# NPC Personality Generator - Code Implementation

This section showcases the Python code that powers the NPC Personality Generator:

```python

import matplotlib.pyplot as plt
import numpy as np

# Define personality traits and their corresponding weights
personality_traits = {
    'Openness': np.array([0.46326522, 0.49815938, 0.5232513]),
    'Conscientiousness': np.array([0.49659102, 0.55880883, 0.47493406]),
    'Extraversion': np.array([0.62529508, 0.60376414, 0.64862753]),
    'Agreeableness': np.array([0.3501991, 0.40582699, 0.36729816]),
    'Emotional Stability': np.array([0.39978606, 0.39042894, 0.47266514]),
    'Honesty & Integrity': np.array([0.57642762, 0.54153208, 0.64065366]),
    'Modesty & Humility': np.array([0.54443489, 0.55671311, 0.4900716]),
    'Emotional Intelligence': np.array([0.59740321, 0.55693556, 0.5127789]),
    'Assertiveness & Drive': np.array([0.4361213, 0.50289647, 0.45638604]),
    'Spirituality & Values': np.array([0.63962121, 0.53348699, 0.61198887]),
    'Individuality & Identity': np.array([0.26296978, 0.31951532, 0.36699213]),
    'Cognitive Abilities & Creativity': np.array([0.52969734, 0.46141854, 0.55550368]),
    'Social Skills & Positivity': np.array([0.54214469, 0.53815497, 0.5309366]),
    'Sensuality & Physicality': np.array([0.81717103, 0.61703708, 0.62026159])
}

# Generate the 3D points for the graph
num_traits = len(personality_traits)
theta = np.linspace(0, 2 * np.pi, num_traits)
x = np.cos(theta)
y = np.sin(theta)
z = np.array([trait_value[2] for trait_value in personality_traits.values()])

# Create the figure and 3D axis
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')

# Create the 3D complete weighted graph
for i in range(num_traits):
    for j in range(i + 1, num_traits):
        xs, ys, zs = [x[i], x[j]], [y[i], y[j]], [z[i], z[j]]
        ax.plot(xs, ys, zs, color='b', alpha=0.3)

# Plot the points representing the personality traits
ax.scatter(x, y, z, c='r', s=60)

# Set labels for each point
for i, trait in enumerate(personality_traits):
    ax.text(x[i], y[i], z[i], trait, fontsize=8)

# Set graph properties
ax.set_xlabel('X')
ax.set_ylabel('Y')
ax.set_zlabel('Z')
ax.set_xlim(-1, 1)
ax.set_ylim(-1, 1)
ax.set_zlim(0, 1)

# Show the 3D complete weighted graph
plt.show()
