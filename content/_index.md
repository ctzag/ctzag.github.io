---
# Leave the homepage title empty to use the site title
title: ''
summary: ''
date: 2022-10-24
type: landing

design:
  # Default section spacing
  spacing: '6rem'

sections:
  - block: resume-biography-3
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: me
      text: ''
      # Show a call-to-action button under your biography? (optional)
      button:
        text: Download CV
        url: uploads/resume.pdf
      headings:
        about: ''
        education: ''
        interests: ''
    design:
      # Use the new Gradient Mesh which automatically adapts to the selected theme colors
      background:
        gradient_mesh:
          enable: true

      # Name heading sizing to accommodate long or short names
      name:
        size: md # Options: xs, sm, md, lg (default), xl

      # Avatar customization
      avatar:
        size: medium # Options: small (150px), medium (200px, default), large (320px), xl (400px), xxl (500px)
        shape: circle # Options: circle (default), square, rounded
  - block: markdown
    content:
      title: '📚 My Research'
      subtitle: ''
      text: |-
        My research centers on machine learning, signal processing, and data-driven analytics, with a particular emphasis on sparse representation theory, compressed sensing, and dictionary learning.

        My earliest research explored statistical approaches to musical genre classification, using generalized Gaussian and alpha-stable models to capture the non-Gaussian characteristics of audio features. This initial exposure to statistical signal processing shaped much of what followed. From there, I moved into multichannel audio coding for immersive environments, developing sinusoidal models for efficient encoding and transmission of spatial audio signals. This led to contributions in compressed sensing applied to audio, demonstrating that sparsity-aware methods could significantly reduce bitrate requirements while preserving perceptual quality.

        I then focused on robust speaker recognition, developing sparse and low-rank techniques to handle missing or corrupted features in real-world conditions. This included discriminative dictionary learning approaches and matrix completion methods under singular value thresholding frameworks.

        A significant thread of my research has been acoustic source localization, where I designed compressive sensing algorithms for wideband localization and separation. This work resulted in a US patent.

        In more recent years, my academic research broadened into applied AI across several domains. In IoT security, I developed lightweight sparse representation methods for botnet attack detection at the network edge. In social media analysis, I built explainable pipelines for automated bot detection and trend monitoring. In cybersecurity, I designed AI models for threat and vulnerability assessment targeting healthcare IT infrastructures, translating risk indicators into actionable mitigation strategies. In healthcare more broadly, I developed predictive analytics pipelines for mortality prediction in critically-ill patients, combining classical ML with NLP-driven analysis of clinical data. I also explored sound event classification using discriminative dictionary learning, short-term time series forecasting under resource-constrained IoT settings, and probabilistic forecasting methods for electricity price prediction, applying statistical and machine learning techniques to capture the uncertainty and volatility inherent in energy markets.

        Applied & Translational Work: Beyond academic research, a part of my work has been driven by real-world deployment in industrial and startup settings. In social media intelligence, I developed deep learning models for user identification through network traffic analysis and mobile device classification based on behavioral communication patterns. Currently, I am developing deep learning models for breathing pattern analysis in athletes, transforming earbud microphone data into performance insights using audio embeddings and transformer-based architectures. In parallel, I build AI-driven quantitative models for financial time series analysis and real-time decision-making.
    design:
      columns: '1'
      css_class: 'research-section'
  - block: collection
    id: papers
    content:
      title: Featured Publications
      filters:
        folders:
          - publications
        featured_only: true
    design:
      view: article-grid
      columns: 2
  - block: collection
    content:
      title: Recent Publications
      text: ''
      filters:
        folders:
          - publications
        exclude_featured: false
    design:
      view: citation
  - block: collection
    id: talks
    content:
      title: Recent & Upcoming Talks
      filters:
        folders:
          - events
    design:
      view: card
  - block: collection
    id: news
    content:
      title: Recent News
      subtitle: ''
      text: ''
      # Page type to display. E.g. post, talk, publication...
      page_type: blog
      # Choose how many pages you would like to display (0 = all pages)
      count: 10
      # Filter on criteria
      filters:
        author: ''
        category: ''
        tag: ''
        exclude_featured: false
        exclude_future: false
        exclude_past: false
        publication_type: ''
      # Choose how many pages you would like to offset by
      offset: 0
      # Page order: descending (desc) or ascending (asc) date.
      order: desc
    design:
      # Choose a layout view
      view: card
      # Reduce spacing
      spacing:
        padding: [0, 0, 0, 0]
  - block: cta-card
    demo: true # Only display this section in the Hugo Blox Builder demo site
    content:
      title: 👉 Build your own academic website like this
      text: |-
        This site is generated by Hugo Blox Builder - the FREE, Hugo-based open source website builder trusted by 250,000+ academics like you.

        <a class="github-button" href="https://github.com/HugoBlox/kit" data-color-scheme="no-preference: light; light: light; dark: dark;" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star HugoBlox/kit on GitHub">Star</a>

        Easily build anything with blocks - no-code required!

        From landing pages, second brains, and courses to academic resumés, conferences, and tech blogs.
      button:
        text: Get Started
        url: https://hugoblox.com/templates/
    design:
      card:
        # Card background color (CSS class)
        css_class: 'bg-primary-300 dark:bg-primary-700'
        css_style: ''
---
