---
layout: project
type: project
image: img/Business_people_icons.jpeg
title: "NPC Personality Generator"
date: 2022-01-01  # Adjust the date as necessary
published: true
labels:
  - Numpy
  - Matplotlib
  - Python
summary: "Leveraging a 3D visualization of personality traits, this project merges psychology with computational linguistics to dynamically tailor dialogue in virtual environments, creating authentic and diverse interactions that reflect the intricate nuances of human personality. Through weighted personality dictionaries, AI characters adjust their linguistic choices, making digital communication more relatable and lifelike."
---
# 3D Visualization of Personality-Influenced Dialogue: Bridging Traits with Linguistic Patterns

The multifaceted nature of human personality has long fascinated both psychologists and linguists. But what if the subtle nuances of personality could directly influence dialogue patterns in virtual environments? We embark on this journey, introducing a unique method that combines personality modeling with linguistic choices to create a dynamic dialogue system.

## The Personality Dictionaries: A Linguistic Core

At the heart of this project, we've constructed fourteen distinct personality dictionaries, each corresponding to a unique personality trait, such as Openness, Conscientiousness, Extraversion, Agreeableness, Emotional Stability, and nine other integral traits. These dictionaries contain words and phrases that resonate with the characteristics and nuances of each trait.

Each trait is represented with a unique 3D coordinate, with the three dimensions signifying the strength or prominence of that trait. This is not merely a statistical representation but a reflection of the linguistic weight each trait holds in the dialogue system.

## Interpreting the 3D Linguistic Graph

Using matplotlib, we've visualized these traits in a 3D graph. The vibrant red dots represent our core personality categories, while the interconnected lines illustrate the potential overlap or synergy between different traits in influencing dialogue.

However, this is not just a static representation. The weight or intensity of each trait impacts the frequency with which words from its associated dictionary are used in dialogue. The stronger the trait, the more dominant its linguistic patterns become in the conversation.

## Dialogue Creation: The Personality Play

Imagine an AI character with a dominant "Extraversion" trait. The dialogue it generates would predominantly use words from the 'Extraversion' dictionary, infusing the conversation with enthusiasm, energy, and sociability. Conversely, a character with heightened "Emotional Stability" might lean towards words that exude calmness, resilience, and balance.

Thus, by adjusting the weights of these traits, we can craft characters with distinct personalities, making virtual interactions more diverse, relatable, and lifelike.

## Conclusion

With this project, we transcend traditional dialogue systems by introducing a layer of personality-driven linguistic choices. It's a melding of psychology and computational linguistics, aiming to make virtual dialogues more dynamic, authentic, and reflective of the myriad shades of human personality. As we step into an era where virtual interactions become increasingly significant, such innovations can reshape the way we communicate, perceive, and relate in digital spaces.

## Access the Code

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

