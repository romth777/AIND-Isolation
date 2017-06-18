# AIND Project2 Isolation - Research Review
## elmo
### What is elmo
[Elmo](https://github.com/mk-takizawa/elmo_for_learn) is a shogi program that won [the World Computer Shogi Championship](http://www2.computer-shogi.org/wcsc27/).
In this report, the result of investigation on the algorithm is described.

### algorithm
For the evaluation value, we use logistic regression under the hypothesis that if the winning rate follows the binomial distribution (winning or losing), the evaluation value will follow the logistic distribution.
However, instead of simply applying maximum-likelihood estimation logistic regression, we adopt a method of feeding a deep search result to a shallow search result as a regularization term.

Similarly entropy is used for regularization term.
This is merely because the loss term of logistic regression usually uses cross entropy, so we use it in order to match the order of both terms. Calculation Easy and easy to understand value intuitively is also good.

Teacher generation is basically the same as floating, but the following points are different.
· Output victory or defeat
· Random move is executed only at the time of the first phase generation (noise is added to winning percentage)

It is optimized only once with a search depth of 650 billion weak.

## alpha go
### What is alpha go
Alpha go is a Go program developed by DeepMind and is known for breaking pro and shogi players in China and Korea one by one.
### algorithm
Alpha go basically uses Monte Carlo tree search to search for the next hand.
Furthermore, although it is an evaluation value for the search, two points, a policy function and a value function, are prepared, and the policy function indicates the place to hit next.
Then, the value function expresses the evaluation value.
These two functions are made to output appropriate values ​​by learning using past game records.
In addition, when proceeding with learning, not only learning from past game record data but also a more robust model is constructed by proceeding further learning by playing against themselves.
