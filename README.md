# RAGA Metric Calculator

This project implements a RAGA (Retrieval Augmented Generation Assessment) metric calculator using a combination of predefined adapters.

## Features

- Calculate various RAGA metrics including Noise Sensitivity, Faithfulness, Answer Relevancy, and more.
- Extensible design with adapter pattern to easily add more metrics.
- Metric Learner for calculating unknown metrics using OpenAI's GPT model.
- FastAPI application for API-based interaction.

## Installation

1. Clone this repository:
   ```
   git clone https://github.com/Jasshporwal/RAGA.git
   cd raga-metric-calculator
   ```

2. Install the required dependencies:
   ```
   pip install -r requirements.txt
   ```

## Usage

1. Start the FastAPI server:
   ```
   python main.py 
   ```

2. The API will be available at `http://localhost:8000`. You can use the `/calculate_metrics` endpoint to calculate metrics.

3. Example API request:
   ```
   POST /calculate_metrics
   {
     "metrics": ["Noise Sensitivity", "Faithfulness", "Answer Relevancy"],
     "ground_truth": "The Earth is round",
     "answer": "The Earth is spherical",
     "question": "What is the shape of the Earth?",
     "context": "The Earth is the third planet from the Sun and is approximately spherical in shape."
   }
   ```

## Adding New Metrics

To add a new metric:

1. Create a new adapter class in `adapter.py` that inherits from `MetricAdapter`.
2. Implement the `calculate` method for the new adapter.
3. Add the new adapter to the `adapters` dictionary in the `MetricCalculator` class in `calculator.py`.

For metrics without a specific adapter, the system will use the `MetricLearner` to calculate them using the OpenAI GPT model.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

