# Introduction
This project introduces the concept of Markov Models with the goal of learning the transitions between states, orders, and incorporating probabilities. 
Markov Models are a system that uses its core "memoryless-ness" to predict the likelihood that another state will happen, given the first state, and no other state prior. 
With the concept of orders, the current state can be made up of multiple elements, thereby increasing the likelihood of a specific next state. 
This is useful for bioinformatics applications, such as genome annotation. 

The program operates in a Jupyter notebook, having functions defined in cells. 
We first create a Markov model using a dictionary of dictionaries, and then train the model, testing it with a short string. 
Next, we re-build the Markov Model, but with order as an additional argument. 
Then, we generate random text, first calculating the probability of the next word, by seeding the function.
After this, we train the model some more, but with the entirety of "One Fish, Two Fish".
Finally, we run everything we've built on the entirety of the provided texts, and we tested it on both "Sonnets" and "The Odyssey."


# Pseudocode
```
1. build_markov_model (markov_model, new_text, order)
    Inputs:
     markov model - Dictionary of Dictionary containing words and count.
     new_text -  string of text
     order -  Order of the markov model
    Output:
     markov_model with updated counts from new_text

    1. split new_text into words
    2. Add N order of copies of the state *S*, start of the sequence.
    3. At the End of list, add one copy of *E* to mark end.
    4. Use sliding frame approach, the current state as the group of order words starting at position i. The next word as the word at position i + order. 
    5. Update the model with each observed transition:
        a. Never encountered current state, add it to the model with a new inner dictionary the `{next_word : 1}`
        b. if the current state exists in model, but the next word does not, then add only next word to inner dictionary with count 1.
        c. if both current state and next word exists, only increment the count. 
    6. Return markov_model

2. get_next_word(current_word, markov_model, seed)
    Inputs:
     current word - present state, a single word or tuple depending on state.
     markov model - trained model dict of dict produced by build_markov_model
     seed - testing and reproudcibility
    Outputs:
     A single word selected based on observed transition. 
    
    1. Use current_word as key in markov_model to get list next word and counts
    2. From inner dictionary, build two list, one is list of possible words and other is list of counts
    3. Convert the counts to probabilities. 
    4. Return the chosen the word based on probabilities. 

3. generate_random_text(markov_model, seed):
    Inputs:
     markov_model - model generated from build_markov_model
     seeds- testing and reproducibility
    Outputs: 
     full generated random text made by looping the get_next_word() and stitching all the words together. 
    
    1. Determine the order of the model. First it runs a type check if type is string then order  is set to 1 but if the type is tuple or else then it checks the len of the tuple, and  then len decides the order.
    2. Set up the starting state. simple enough for order 1, with *S* as string, but incase of    Nth order, we create tuple of *S* with len of the tuple equivalent to Nth order.
    3. Create an empty list to hold the sentence.
    4. Loop:
        a. Call get_next_word(current_state, markov_model, seed) to pick a next word.
        b. If the returned word is "*E*", stop the loop.
        c. Otherwise, append the word to the sentence list.
        d. Update the current state: drop the oldest word and append the newly generated word to the end. The state stays the same length as the order. 
    5. Join the sentence list into a single string with spaces between words and return it.
```

# Successes
We all wrote out pseudocode and combined them together, adding or removing elements, to create a cohesive structure for the overall program. 
We then wrote the code individually and compared it for each cell. For the most part, we all had similar approaches to the code, which made sense with the way we wrote the pseudocode together. 
We elected to keep the group leaders Jupyter notebook as the one to edit, since it was already in the GitHub, and we once again changed things around as needed, and explained code where there may have been confusion. 

The times where one of us explained what we were doing, or how we did it, was very beneficial, since teaching others is an excellent way to reinforce your own knowledge. 
We all felt that through our collaboration with coding, that we understood how it should come together much easier than if we were doing it alone. 


# Struggles
We originally struggled with scheduling times to meet, since one member is on the West Coast, while the other two are on the East Coast, meaning a 3 hour time difference. 
On top of this, all three members are employed and taking multiple classes, heavily constraining meet times. 

We next had a hard time conceptualizing the logic flow of the functions between different cells, and what should go where. After writing and re-writing pseudocode, we figured out a good structure. 

We then had to reconceptualize what order meant for a markov model and how it doesn't invalidate the memoryless-ness, but we talked through it. 


# Personal Reflections
## Group Leader
I found the GitHub portion of the project to be much easier this time, despite being a group leader for the first time. 
After walking through it during Project 01, I felt I had a good handle of it, and there were no conflicts between the other collaborators.
At first, PyCharm was extremely glitchy with the notebook, making it almost unusable, but I read some resources and found it to be a common problem, and I changed some settings, completely fixing it. 
I do enjoy the troubleshooting aspects of coding, even while I currently find it difficult. 
The project itself, while at first seeming much more involved, was relatively straight-forward, yet my limited Python skills made this more difficult that I would like. 
Using Jupyter notebooks was new to me too, and I found that being able to prototype without breaking the rest of my code was highly beneficial. 

Ultimately, I am proud of what this group accomplished, and I am glad that I got the chance to be a leader. 

## Other member

Dhaivat - It gave me an much clearer idea on the concept of memorylessness concept of markov model. Initially I found it a bit difficult about how to work with Nth order of markov model but discussing it with my peers helped me understand it better. I wish to try dealing the with punctuations of the data given. For this project I got used to Github workflow, got better at pushing and committing my work to the repo. It was fascinating to use tuples so that markov property is not violated. The group meetings and active discussion helped me to look at the problems from different perscpectives. 
Bessie - Working on this project  gave me an insight on how the Markov chain algorithim is built . It showed me how you determine the current state and how you navigate to other transition states using probabilities . I also learnt how to use Jupyter notebooks and incorparate them on Github . I had difficulties in how you write code for determining the Nth order and other group members helped me understand that part . I hope to increase my coding skills so that I am better prepared in wriiting my algorithims
# Generative AI Appendix
As per the syllabus
