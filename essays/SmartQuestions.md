---
layout: essay
type: essay
title: "Smart Questions"
date: 2023-09-05
published: true
labels:
  - Programming
---

# Smart Questions for Smart Software Engineers

## Introduction

In an age dominated by digital platforms, where collaboration, learning, and problem-solving take place in online forums, mailing lists, and chat boards, the importance of asking the right question cannot be understated. Smart software engineers know that the answer they get is often only as good as the question they ask. But why is the formulation of a smart question so essential, and how does one ensure that their questions meet the bar?

## The Importance of Smart Questions

- **Efficient Problem Solving:** Smart questions directly and precisely address the issue, leading to quicker, more accurate answers. Time saved is especially vital in the fast-paced world of software development.
- **Reflect Professionalism:** A well-framed question indicates the preparatory work done by the asker, showcasing their dedication and respect for others' time.
- **Better Learning:** Smart questions often lead to detailed explanations, which can expand an engineer's understanding of the topic.

## Evaluating the Precepts for Smart Questions

The guidelines provided give an in-depth understanding of how to approach a problem and seek help. Let's analyze their alignment with the essence of asking smart questions:

- **Research Before Asking:** Ensuring that one has searched for answers before posing a question filters out redundant questions, preserving the community's time and patience.
- **Describe Symptoms, Not Guesses:** Focusing on symptoms ensures that responders get raw, unfiltered data. This increases the chances of an accurate diagnosis. For instance, saying "SIG11 errors during kernel compiles" is far more useful than speculating about a potential motherboard issue.
- **Chronological Description:** Providing a step-by-step account of the problem helps in understanding the sequence of events, which is crucial in debugging.
- **State the Goal:** Describing the end goal ensures that even if the asker is on a wrong path, someone can guide them on the correct one.
- **Be Precise:** Details about the environment, steps taken, and any changes can significantly affect the solution provided. Anticipating potential follow-up questions and answering them upfront saves iterative back-and-forths.

## How Responses Reflect Smartness

Responses to smart questions tend to:

- **Be Direct and Clear:** Precise questions often get straightforward answers.
- **Cover All Bases:** As the question often provides comprehensive information, answers can tackle the problem from all angles.
- **Be Collaborative:** Smart questions can often lead to discussions, bringing in multiple experts to provide insights.

## Insights Gained

- **The Art of Asking:** Understanding how to ask is as essential as knowing what to ask. The precepts offer a structured approach to problem-solving and seeking assistance.
- **Respect for the Community:** Taking the time to craft a smart question shows respect for the community's time and effort.
- **Continuous Learning:** Observing the difference in responses received for well-framed versus poorly framed questions emphasizes the importance of precision and clarity.

## Conclusion

In the realm of software engineering, where solutions often lie in the intricate details, the way a question is posed can be the difference between hours of futile searching and a quick, efficient solution. Smart questions, rooted in research, clarity, and detail, lead to smarter solutions, enhancing the collective knowledge of the community and the individual's understanding. As the adage goes, "The quality of the answer often depends on the quality of the question." And for smart software engineers, this couldn't be truer.

---

### Example : Bad Question
["I'm doing web scraping with Dart and I encountered the problem that I'm not able to get my information with the help of 'html' package because the web page uses dynamically generated web pages. I tried the html-package and used the querySelector which doesn't find anything. I would be happy if someone has a solution for this problem and if someone can give me some sample code.”](https://stackoverflow.com/questions/77050191/solution-for-handling-dynamically-generated-web-pages-in-dart)

#### Evaluation:

1. **Research Before Asking:** The user mentions attempting to use the 'html' package, but it's unclear if they searched for solutions related to issues with this package or dynamically generated content before asking.

2. **Describe Symptoms, Not Guesses:** The user correctly identifies that the 'html' package doesn't work because the website uses dynamically generated web pages. However, they should focus more on describing the exact symptoms encountered, such as specific error messages or unexpected outputs.

3. **Chronological Description:** The steps leading to the discovery of the issue are partially covered, but more detail would be helpful. For example, sharing a bit of the code they tried or explaining how they deduced that the dynamic generation of web pages was the root cause.

4. **State the Goal:** The goal is stated, albeit somewhat implicitly. They want to scrape data from a dynamically generated website using Dart.

5. **Be Precise:** This is where the question falls short:
The user doesn't specify which website they're trying to scrape or provide a snippet of the problematic code.
There's no mention of the environment or Dart's version they're using.
They don’t describe any research or attempts to troubleshoot the issue beyond using the querySelector.
The ask for "sample code" is too broad; specifying what kind of solution or use case they need would narrow it down.


#### Conclusion

  The question could be seen as lacking according to the guidelines in the essay. It's not thoroughly researched, lacks specific details, and the ask is broad. However, it does provide a basic understanding of the problem, which might be enough for someone familiar with Dart and web scraping to offer some general guidance. To align better with the "smart questions" precept, the user should provide more detail, share code snippets, and be precise in their ask.


---

### Example : Good Question
[Why is processing a sorted array faster than processing an unsorted array?](https://stackoverflow.com/questions/11227809/why-is-processing-a-sorted-array-faster-than-processing-an-unsorted-array)

#### Summary 

  The user observed that in a C++ code, sorting an array before processing it in a loop made the primary loop approximately 6x faster. To ensure it wasn't just specific to C++, they replicated the experiment in Java and noticed a similar but less pronounced improvement. The user initially believed sorting might help cache the data but dismissed the idea since the array was freshly generated. They are curious about why processing a sorted array is faster than an unsorted one, given that the code is summing independent terms and order shouldn't matter.
  

#### Evaluation:

1. **Research Before Asking:** The user not only identified a curious behavior in C++ but also went a step further to validate it in Java. They've demonstrated due diligence in verifying the anomaly.

2. **Describe Symptoms, Not Guesses:** The user clearly states what they observed without making unverified assertions. They present the facts (like the change in execution time) and provide both C++ and Java code to reproduce the situation.

3. **Chronological Description:** The step-by-step account of generating the data, optionally sorting it, and then processing it gives a clear picture of the sequence leading up to the observed behavior.

4. **State the Goal:** The user's primary goal is evident: They want to understand the mysterious performance difference between processing sorted and unsorted arrays.

5. **Be Precise:** The question includes all the necessary code to reproduce the behavior.The user provides specific execution times for both scenarios.They mention their initial thoughts on caching and why they dismissed that theory.


#### Conclusion

In conclusion, the user's question aligns well with the "smart questions" criteria. They present a detailed account of their observation, provide all necessary data for reproduction, and clearly state what they're trying to understand.
