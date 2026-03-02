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
