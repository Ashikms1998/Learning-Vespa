# Type of Distance Metric
euclidean -  use for Straight-line distance - When absolute position matters
angular - Cosine similarity in disguise - Best for sentence embeddings (like BERT, GPT vectors)
dotproduct - Measures alignment (no normalization) - Used in recommendation, scoring models
hamming - For binary (0/1) vectors only - Very rare; used for binary feature comparisons
prenormalized-angular - Angular but assumes you already normalized the vectors - You normalize them yourself, Vespa just compares angles

# Example for Indexing and Querying using Distance Metric

Index time(We store this)

{
  "name": "Sony WH-1000XM5",
  "description": "Noise-canceling headphones",
  "embedding": [0.05, 0.9, 0.2] //the developer — have to generate the embeddings yourself using a model like sentence-transformers or OpenAI or Cohere or Train your own model, and then include them in your document JSON like this
}

Query time (user types)

"ANC headphones for travel"
→ Convert to vector → [0.07, 0.85, 0.25]


Now Vespa compares the query vector with all stored product vectors using a distance function in our case Euclidean.

