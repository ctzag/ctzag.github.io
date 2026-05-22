---
title: 'Experience'
date: 2023-10-24
type: landing

design:
  spacing: '5rem'

# Note: `username` refers to the user's folder name in `content/authors/`

# Page sections
sections:
  - block: resume-experience
    content:
      username: me
    design:
      # Hugo date format (year-only, so dates render like "2024" / "2017")
      date_format: '2006'
      # Education or Experience section first?
      is_education_first: false
  - block: markdown
    content:
      title: 'Skills'
      subtitle: ''
      text: |-
        **Programming:** Python, Matlab, C, C++, SQL

        **Deep Learning:** TensorFlow, Keras, PyTorch

        **ML & Data Science:** scikit-learn, Pandas, NumPy, SciPy, Matplotlib, Seaborn

        **Signal Processing & Statistics:** time-series analysis, anomaly detection, estimation theory, sparse representation, predictive analytics, statistical signal processing

        **Tools:** Git, LaTeX, RESTful API design, Jupyter
    design:
      columns: '1'
---
