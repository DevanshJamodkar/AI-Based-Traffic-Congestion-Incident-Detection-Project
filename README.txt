
PROJECT: AI-Based Traffic Congestion & Incident Detection

OVERVIEW
This project implements a machine learning decision layer to classify road tiles as:
• 0 – Normal Traffic
• 1 – Congestion / Possible Incident

The system uses structured features derived from aerial imagery and supports Intelligent Transportation System (ITS) operations through spatial risk visualization.

PERFORMANCE METRICS

Accuracy : 0.8438

ROC-AUC : 0.9253

Precision : 0.8507

Recall : 0.7917

Note: ROC-AUC, Precision, and Recall are prioritized over accuracy because traffic incidents are relatively rare and threshold selection must be application-driven.

FILE NAVIGATION GUIDE

spatial_heatmap.png
→ Aggregated congestion risk visualization
→ Red = high risk zones, Green = normal flow

confusion_matrix.png
→ Breakdown of true vs predicted classes
→ Used to analyze false alarms vs missed incidents

feature_importance.png
→ Contribution of each feature to the model
→ Demonstrates dominance of speed and queue indicators

roc_curve.png
→ Model discrimination performance across thresholds

Video_Script.txt
→ Explanation script for the required presentation video

INTERPRETATION SUMMARY

The model outputs can support:
• Adaptive traffic signal control during peak congestion
• Emergency dispatch when speed drops with long queues
• Route diversion using Variable Message Signs
• Prioritization of drone re-inspection for high-risk tiles

LIMITATIONS & FUTURE WORK

• Dataset lacks GPS coordinates for real map overlay
• Weather and temporal history not included
• Future scope:
– Temporal fusion with historical patterns
– Weather-aware thresholds
– Multi-camera / multi-sensor integration
