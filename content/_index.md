---
# Leave the homepage title empty to use the site title
title: ''
summary: ''
date: 2022-10-24
type: landing

design:
  # Default section spacing
  spacing: '0rem'

sections:
  - block: resume-biography-3
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: me
      text: ''
      # Show a call-to-action button under your biography? (optional)
      button:
        text: Download CV
        url: uploads/CV_Andreea_Bodea_(2026_February).pdf
      headings:
        about: 'About me'
        education: ''
        interests: 'Interests'
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
    id: my-research
    content:
      title: 'My Research'
      subtitle: ''
      text: |-
        I am focusing on privacy in NLP and AI systems, particularly how to protect sensitive information when using Large Language Models (LLMs). 

        My current research explores:
        - Privacy risks in RAG systems: systematizing threats and mitigation strategies 
        - Differential privacy for text: studying how LLMs can reconstruct private information from anonymized data, and how to prevent it
        - Privacy-preserving AI applications: building systems that balance utility with strong privacy guarantees

        I believe privacy should be a feature, not an afterthought. 

        Please reach out to collaborate 😊
    design:
      columns: '1'
  - block: collection
    id: research
    content:
      title: Publications
      filters:
        folders:
          - publications
        featured_only: true
    design:
      view: article-grid
      columns: 2
  - block: resume-experience
    id: experience
    content:
      title: Recent Experience
      username: me
      count: 3  # Show only the 3 most recent positions
      button:
        text: View Full Experience
        url: experience/
    design:
      date_format: 'January 2006'
      is_education_first: false
  - block: resume-education
    id: education
    content:
      title: Education
      username: me
    design:
      date_format: 'January 2006'
  - block: resume-skills
    content:
      title: Skills
      username: me
  - block: resume-languages
    content:
      title: Languages
      username: me
---
