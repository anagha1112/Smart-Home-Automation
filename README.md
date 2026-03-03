# Smart-Home-Automation

Built an intelligent smart home system that recognizes what a person is doing, predicts what they will do next based on time and behavior patterns, and automatically prepares the home — while learning from feedback.



Sensor Events
      ↓
Deep HAR (Transformer / CNN-LSTM)
      ↓
Current Activity + Confidence
      ↓
Time-Aware Probabilistic Transition Model
      ↓
Next Activity Probability
      ↓
Uncertainty Fusion
      ↓
Decision Engine
      ↓
Automation
      ↓
Feedback Update (Adaptive Learning)



## Human Activity Recognition (HAR)

Activity-driven segmentation (Best for Aruba)

Use begin/end markers.

Sample = true activity segment.

Label = activity.

No B/I/E needed.




BiLSTM HAR

       ↓
   
Current Activity + Duration

       ↓
   
Hazard Model → Leave Decision

       ↓
   
Router Model → Next Activity

       ↓
   
Gap Model → Expected Start Time

       ↓
   
Automation Trigger


current

      Next Activity Prediction Accuracy: 0.3396887159533074
      Mean Absolute Error (minutes): 0.3424128415289663


🔵 Important Tradeoff

As order increases:

1st order → simple, stable
2nd order → better accuracy
3rd order → sparse data problem


With Aruba size,
second order is ideal.

Third order may overfit.

🔥 Even Stronger Version (Very Smart)

Instead of hard second-order only,
you can do:

𝑃
=
𝜆
𝑃
(
𝑛
𝑒
𝑥
𝑡
∣
𝑐
𝑢
𝑟
𝑟
𝑒
𝑛
𝑡
)
+
(
1
−
𝜆
)
𝑃
(
𝑛
𝑒
𝑥
𝑡
∣
𝑝
𝑟
𝑒
𝑣
,
𝑐
𝑢
𝑟
𝑟
𝑒
𝑛
𝑡
)
P=λP(next∣current)+(1−λ)P(next∣prev,current)

This is called:

Backoff smoothing

It prevents sparsity problems.

Very research-level idea.


