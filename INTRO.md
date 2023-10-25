# Intro

From writing poetry to giving medical advice, [large language models](https://en.wikipedia.org/wiki/Large_language_model) are shockingly general, giving us a first hint of the G in [artificial general intelligence](https://en.wikipedia.org/wiki/Artificial_general_intelligence).  They are also [surprisingly simple](https://dugas.ch/artificial_curiosity/GPT_architecture.html), and yet, due to their immense size, are deeply inscrutable, despite [some](https://arxiv.org/abs/2211.00593) [heroic](https://arxiv.org/abs/2012.14913) [efforts](https://arxiv.org/abs/2305.16130).

# Timeline

[GPT-2](https://en.wikipedia.org/wiki/GPT-2), [GPT-3](https://en.wikipedia.org/wiki/GPT-3), 

# Weaknesses

As [Dan Piponi](https://mathstodon.xyz/@dpiponi/111116694861297725) noted:

> And yet I think more has been written about what ChatGPT can't do than has been written about what any other tool can't do. It's all very strange.

The biggest weakness is their complete inability to tell if they are [telling the truth](https://en.wikipedia.org/wiki/Hallucination_(artificial_intelligence)).

# Scale

The [GPT-3](https://arxiv.org/abs/2005.14165) paper has this:

![Screenshot of a table of model sizes.](model_sizes.png)

The last row shows that the full GPT-3 has 175 billion parameters, arranged in 96 blocks where each block has an attention layer with 4 * 12288 * 12288 parameters and a couple of feed forward layers for a further 8 * 12288 * 12288 parameters.

The parameter count doesn't depend on the context window size (which, for GPT-3, is 2048), or the number of attention heads, or the vocabulary size (which, for GPT-3, is 50,257).  Instead, it just depends on the number of layers and the model dimension (the embedding size of each token).  However, a larger context window will generally require the model to be bigger.

According to [this](https://github.com/amirgholami/ai_and_memory_wall#nlp-models), GPT-3 needs 740 teraflops to infer a single token, due to each parameter being used many times (which, in turn, allows the model to do more computation than the raw parameter count would imply).  Later versions of GPT-3 had lower inference costs (?).

In the paper, they say:

>  for most tasks we find relatively smooth scaling with model capacity

and then, intriguingly:

> the gap between zero-, one-, and few-shot performance often grows with model capacity, perhaps suggesting that larger models are more proficient meta-learners
