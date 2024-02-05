![YouTube logo](yt.png)
[A Hackers' Guide to Language Models](https://www.youtube.com/watch?v=jkrNMKz9pWU) -
**Jeremy Howard**

![YouTube logo](yt.png)
[The End of Finetuning](https://www.youtube.com/watch?v=5Sze3kHAZqE) -
**Jeremy Howard** - domain FT and instruction FT;
the single-shot memorization phenomenon;
catastrophic forgetting;
RAG is such an inefficient hack;
GPT-4 with good prompting plays good chess.

![YouTube logo](yt.png)
[Open Questions for AI Engineering](https://www.youtube.com/watch?v=qw4PrtyvJI0&t=24953s) -
**Simon Willison**

> ChatGPT has no affordances.

> People decided it was hype because they dived in and asked it for arithmetic and facts!

> Moving beyond a chat interface.

[Finetuned language models are zero-shot learners](https://openreview.net/pdf?id=gEZrGCozdqR)

> In this paper, we explore a simple method to improve the zero-shot performance of large language
models, which would expand their reach to a broader audience.

> The idea is that by using supervision to teach an LM to perform tasks described via
instructions, the LM will learn to follow instructions and do so even for unseen tasks.

It doesn't explain what the training is :(

![YouTube logo](yt.png)
[Shane Legg](https://www.youtube.com/watch?v=Kc1atfJkiJU) -
LLMs (even after fine tuning) just blurt out the first thing (like system 1).  They need to have a system 2, together with a good model of the world and people and ethics, as well as robust and reliable reasoning.  Then they can do search.

# Strengths

+ Huge general knowledge.

+ Perfect grammar.

+ Can generate an essay far quicker than a human.

+ Can follow the thread of a conversation.

# Adversarial & Visualization

[Transformer Circuits Thread](https://transformer-circuits.pub/)

[Adversarial Examples Are Not Bugs, They Are Features](https://arxiv.org/abs/1905.02175) - **Ilyas** -
A popular paper, I think

[LLM Lies: Hallucinations are not Bugs, but Features as Adversarial Examples](https://arxiv.org/abs/2310.01469)

## Distill

[A Discussion of Adversarial Examples Are Not Bugs, They Are Features](https://distill.pub/2019/advex-bugs-discussion/)

[Visualizing Weights](https://distill.pub/2020/circuits/visualizing-weights/)

[Zoom In: An Introduction to Circuits](https://distill.pub/2020/circuits/zoom-in/)

[Exploring Neural Networks with Activation Atlases](https://distill.pub/2019/activation-atlas/)

# 2023-11-07 meeting

## The GPT architecture

Things we missed last time:

+ Positional encoding

+ The projection FF layer

+ Layer Norm

+ Residuals and residual streams

+ Multi head

+ The 12,288 giving space for calculations

## Generating text

+ sampling, beam search, top-k, top-p

## Interpreting GPT

+ The nodes are the variables and the weights are the program.

+ IOI

+ Superposition

+ Causal interventions on the internals of a model.

+ Activation patching - run the model twice; replace a node's activation in one run with the activation from the other run.
+ It measures counter-factuals.  What would 

+ Path patching

+ Automatic circuit discovery

+ With patching in general, you have to choose your input distribution carefully.

+ Attention heads (?) can refer to other info by value or by pointer.  They showed that, in their IOI example, the second John was being referred to by (relative) pointer.

## A mechanism for solving relational tasks in transformer language models

in an in-context learning setting

reverse-engineering the data structures and
algorithms that are implicitly encoded in the model’s weights

LLMs implement a basic
vector-addition mechanism which plays an important role in a number of in-context-learning tasks

a distinct processing signature in the forward pass which characterizes
this mechanism

if models need to perform the get capital(x) function, which
takes an argument x and yields an answer y, they first surface the argument x in earlier
layers which enables them to apply the function and yield y as the final output

the vector arithmetic mechanism
is often implemented by mid-to-late layer feedforward networks (FFNs) in a way that is
**modular and supports intervention**

From start to end, *x* is only updated
by additive updates, forming a residual stream. Thus, the token representation
*x<sub>i</sub>* represents all of the additions made into the residual stream up to layer *i*

LMs incrementally
update the token representation x to build and refine an encoding of the vocabulary distribution

Finally, the model enters Saturation, where the model recognizes it has solved
the next token, and ceases updating the token representation for the remaining layers

Saturation events are described in Geva et al. (2022a) where detection of such events is used to “early-exit”
out of the forward pass

Our findings invite
future work aimed at understanding why, and under what conditions, LMs learn to use this mechanism
when they are capable of solving such tasks using, e.g., adhoc memorization

# IOI links

[A Mathematical Framework for Transformer Circuits](https://transformer-circuits.pub/2021/framework/index.html)

[In-context Learning and Induction Heads](https://transformer-circuits.pub/2022/in-context-learning-and-induction-heads/index.html)

[LLM Visualization](https://bbycroft.net/llm)
