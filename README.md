# Session-based recommendation system - Supermarket use case

This project harnesses the power of recommendation systems to provide highly personalized and context-aware product suggestions based on users' shopping sessions without the existence of user profiles or their entire historical preferences. This report explores a simple, yet powerful, NLP-based approach (word2vec) to recommend the next item to a user.

Session-based recommendation systems rely heavily on the user’s most recent interactions, rather than on the user’s historical preferences. This is especially advantageous because a user could appear anonymously—that is, a user may not be logged in or may be browsing incognito. The method can be implemented even in the absence of historical user data, and doesn’t explicitly rely on user population statistics.

This project demonstrates Bravo supermarket website. Malik, a new customer, has been bought eggs, corn oil, and bread. Her browsing history looks like this:


![alt text](https://github.com/NijatZeynalov/session-based-recommender-bravo-supermarket/assets/31247506/221c92f2-0384-462d-ad8e-3e2230ec0fe3)

What should we recommend to him next?

We’ll consider Malik’s recent browsing history as a “session.” Formally, a session is composed of multiple user interactions that happen together in a continuous period of time—for instance, products purchased in a single transaction.

Our goal is to predict the product within Malik’s session that she will like enough to click on. This task is called next event prediction (NEP): given a series of events (Malik’s browsing history), we want to predict the next event (Malik clicking on a product we recommend to her).

In order to solve this problem we will use word2vec algorithm, where we will treat each session as a sentence, with each item or product in the session representing a “word.” A website’s collection of user browser histories (including Malik’s) will act as the corpus. Word2vec will crunch over the entire corpus, learning relationships between products in the context of user browsing behavior. The result will be a collection of embeddings: one for each product. 

In NEP, we consider a user’s history to recommend items for the future—but, when training models for recommendation, all the data is historical. In order to mimic “real life” behavior, we’ll pretend that we only have access to the user’s first n-1 purchased items, and use those to try to predict the nth item purchased.

To visualize this, let’s go back to Rhonda’s historical browsing information, collected while she was using our site. We’ll use the highlighted items as our training set to learn product representations, which will be used to generate recommendations. Recommendations are typically based on the most recent interaction by the user, called the query item. In this case, we’ll treat the last item (“cap” in our highlighted set of items below) as the query item, and use that to generate a set of recommendations.


![alt text](https://github.com/NijatZeynalov/session-based-recommender-bravo-supermarket/assets/31247506/2a7bc24b-41ba-4154-bbd8-8d2f9126cad2)
