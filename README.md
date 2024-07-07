
# CaseText Negative Treatment Extractor

## Overview
This project aims to identify negative treatments within a set of legal opinions from CaseText. Negative treatment occurs when one case overrules or otherwise limits the holding of a prior case.

## Setup Instructions
Follow these instructions to set up the project on your local machine.

### Prerequisites
- Python 3.x
- Pip (Python package installer)
- An OpenAI API key

### Installation
1. **Clone the repository**:
   git clone https://github.com/janddtorrecampo/casetext-negative-treatment.git
   cd casetext-negative-treatment

2. **Set up a virtual environment**:
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`

3. **Install dependencies**:
   pip install -r requirements.txt

4. **Set your OpenAI API key**:
   - Create a .env file in the project root and add your API key:
     OPENAI_API_KEY=your-openai-api-key
   - Alternatively, set the environment variable directly:
     export OPENAI_API_KEY=your-openai-api-key

## Usage
To extract negative treatments from a case, use the `extract_negative_treatments` function:
   from main import extract_negative_treatments

   treatments = extract_negative_treatments(slug='littlejohn-v-state-7')
   print(treatments)

To process multiple slugs:
   from main import process_multiple slugs

   slugs = [
       'littlejohn-v-state-7',
       'beattie-v-beattie',
       'travelers-indem-co-v-lake',
       'tilden-v-state',
       'in-re-lee-342013'
   ]

   results = process multiple slugs(slugs)
   for slug, treatments in results.items():
       print(f"Results for {slug}:")
       for treatment in treatments:
           print("Section Text:", treatment['section_text'])
           print("Analysis:", treatment['analysis'])
           print()

## Testing
Run unit tests with:
   python -m unittest discover

## Discussion on Prompting

### Approaches Tried
- **Initial Prompt**: Simple prompt asking for negative treatments.
- **Refined Prompt**: Detailed prompt providing context and examples.

### Challenges
- Distinguishing between different legal terms and their legal meanings versus their nonlegal meanings. For example "negative treatment" has a very specific legal meaning. However, people can be negatively treated and the model was catching that type of meaning as well.

## Known Issues
- Handling of ambiguous cases where the term "overruled" is used but does not constitute negative treatment. For example, overruling an objection may not be negative treatment.

## Google Colab
The project was initially created in Google Colab. You can access the original notebook [here](https://colab.research.google.com/drive/10jXZKHs9AafjRQqFghqTsBmx62nncrRA?usp=sharing).

## License
This project is licensed under the MIT License.
