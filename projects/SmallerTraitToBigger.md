# Trait Generator for Non-Player Characters

```python
# This script defines smaller personality traits as 3D vectors and groups them under larger personality traits.
# Traits are represented using correlated multivariate normal distributions.
# The main goal is to visualize both the smaller and larger traits in a 3D scatter plot using matplotlib.

import matplotlib.pyplot as plt
import numpy as np

# Define smaller personality traits as 3D vectors
smaller_traits_list = [
    'Artistry', 'Curiosity', 'Innovation', 'Imagination', 'Whimsy', 'Wonderment',
    'Perception', 'Visionariness', 'Mental Flexibility', 'Bulk Apperception',
    'Meticulousness', 'Decisiveness', 'Tenacity', 'Coordination', 'Fastidiousness', 'Cleanliness',
    'Determination', 'Focus', 'Patience', 'Perseverance', 'Industry', 'Temperance',
    'Confidence', 'Expressivity', 'Leadership', 'Competitiveness', 'Wanderlust', 'Gregariousness',
    'Adventurousness', 'Vivacity', 'Extroversion',
    'Congeniality', 'Consideration', 'Courtesy', 'Kindness', 'Tenderness', 'Gentleness',
    'Generosity', 'Affection', 'Charm', 'Empathy',
    'Fragility', 'Timidity', 'Self-Preservation', 'Vindictiveness', 'Capriciousness', 'Lugubriousness',
    'Inhibition', 'Stoicism', 'Passivity', 'Reticence',
    'Candor', 'Integrity', 'Fidelity', 'Morality', 'Skepticism', 'Deceptiveness',
    'Humility', 'Reserve', 'Hubris', 'Meekness', 'Decorum',
    'Intuition', 'Empathy', 'Sensitivity', 'Wisdom', 'Emotional Acuity', 'Reflectiveness',
    'Assurance', 'Bellicosity', 'Brusqueness', 'Stubbornness', 'Brazenness', 'Aggression',
    'Courage', 'Grit', 'Endurance', 'Willingness', 'Self-Esteem', 'Restraint',
    'Faith', 'Spirituality', 'Patriotism', 'Peacefulness', 'Temperance', 'Paternalism', 'Morality',
    'Individualism', 'Introversion', 'Masculinity', 'Fashionableness', 'Femininity', 'Narcissism', 'Egocentricism',
    'Facility', 'Education', 'Literalism', 'Rhythm', 'Sarcasm', 'Knowledgeableness', 'Comprehensiveness', 'Articulateness',
    'Judiciousness', 'Imagination', 'Musicality', 'Delicacy',
    'Humor', 'Whimsy', 'Sarcasm', 'Ribaldry', 'Charm', 'Poise', 'Decorum', 'Articulateness',
    'Joy', 'Peacefulness', 'Contentment',
    'Sensuality', 'Rhythm', 'Tenderness', 'Sexuality', 'Physicality', 'Physical Flexibility'
]

# Set mean and standard deviation for the normal distribution
mean = 0.5
std_dev = 0.4

# Create a covariance matrix for high correlation and high variance
corr = 0.8
covariance_matrix = np.array([[std_dev ** 2, corr * std_dev ** 2, corr * std_dev ** 2],
                              [corr * std_dev ** 2, std_dev ** 2, corr * std_dev ** 2],
                              [corr * std_dev ** 2, corr * std_dev ** 2, std_dev ** 2]])


# Group the smaller personality traits under the larger personality traits
larger_traits = {

    'Openness': [
        'Artistry', 'Curiosity', 'Innovation', 'Imagination', 'Whimsy', 'Wonderment',
        'Perception', 'Visionariness', 'Mental Flexibility', 'Bulk Apperception'
    ],

    'Conscientiousness': [
        'Meticulousness', 'Decisiveness', 'Tenacity', 'Coordination', 'Fastidiousness',
        'Cleanliness', 'Determination', 'Focus', 'Patience', 'Perseverance', 'Industry', 'Temperance'
    ],
    'Extraversion': [
        'Confidence', 'Expressivity', 'Leadership', 'Competitiveness', 'Wanderlust',
        'Gregariousness', 'Adventurousness', 'Vivacity', 'Extroversion'
    ],

    'Agreeableness': [
        'Congeniality', 'Consideration', 'Courtesy', 'Kindness', 'Tenderness', 'Gentleness',
        'Generosity', 'Affection', 'Charm', 'Empathy'
    ],

    'Emotional Stability': [
        'Fragility', 'Timidity', 'Self-Preservation', 'Vindictiveness', 'Capriciousness',
        'Lugubriousness', 'Inhibition', 'Stoicism', 'Passivity', 'Reticence'
    ],

    'Honesty & Integrity': [
        'Candor', 'Integrity', 'Fidelity', 'Morality', 'Skepticism', 'Deceptiveness'
    ],

    'Modesty & Humility': [
        'Humility', 'Reserve', 'Hubris', 'Meekness', 'Decorum'
    ],

    'Emotional Intelligence': [
        'Intuition', 'Empathy', 'Sensitivity', 'Wisdom', 'Emotional Acuity', 'Reflectiveness'
    ],

    'Assertiveness & Drive': [
        'Assurance', 'Bellicosity', 'Brusqueness', 'Stubbornness', 'Brazenness', 'Aggression',
        'Courage', 'Grit', 'Endurance', 'Willingness', 'Self-Esteem', 'Restraint'
    ],

    'Spirituality & Values': [
        'Faith', 'Spirituality', 'Patriotism', 'Peacefulness', 'Temperance', 'Paternalism', 'Morality'
    ],

    'Individuality & Identity': [
        'Individualism', 'Introversion', 'Masculinity', 'Fashionableness', 'Femininity', 'Narcissism', 'Egocentricism'
    ],

    'Cognitive Abilities & Creativity': [
        'Facility', 'Education', 'Literalism', 'Rhythm', 'Sarcasm', 'Knowledgeableness',
        'Comprehensiveness', 'Articulateness', 'Judiciousness', 'Imagination', 'Musicality', 'Delicacy'
    ],

    'Social Skills & Positivity': [
        'Humor', 'Whimsy', 'Sarcasm', 'Ribaldry', 'Charm', 'Poise', 'Decorum', 'Articulateness',
        'Joy', 'Peacefulness', 'Contentment'
    ],

    'Sensuality & Physicality': [
        'Sensuality', 'Rhythm', 'Tenderness', 'Sexuality', 'Physicality', 'Physical Flexibility'
    ],

}


# Generate random values from correlated multivariate normal distributions for each trait
smaller_traits = {}
for larger_trait, smaller_trait_group in larger_traits.items():
    for trait in smaller_trait_group:
        trait_values = np.random.multivariate_normal([mean, mean, mean], covariance_matrix)
        trait_values_clipped = np.clip(trait_values, 0, 1)
        smaller_traits[trait] = trait_values_clipped


print(smaller_traits)


# Calculate the weighted values for the larger personality traits
def calculate_weighted_value(small_traits, larger_trait_group):
    weighted_sum = np.zeros(3)
    for trait in larger_trait_group:
        weighted_sum += small_traits[trait]
    return weighted_sum / len(larger_trait_group)


def print_larger_trait_values(larger_traits_weights):
    for trait, vec in larger_traits_weights.items():
        print(f"{trait}: {vec}")


larger_traits_weights = {
    trait: calculate_weighted_value(smaller_traits, group) for trait, group in larger_traits.items()
}

print_larger_trait_values(larger_traits_weights)

# Create a 3D scatter plot of the smaller and larger personality traits
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')

# Plot smaller traits
for trait, vec in smaller_traits.items():
    ax.scatter(vec[0], vec[1], vec[2], marker='o', label=trait)

# Plot larger traits
for trait, vec in larger_traits_weights.items():
    ax.scatter(vec[0], vec[1], vec[2], marker='^', label=trait)

ax.set_xlabel('X')
ax.set_ylabel('Y')
ax.set_zlabel('Z')
ax.legend(loc='upper left', fontsize=8)
plt.show()
