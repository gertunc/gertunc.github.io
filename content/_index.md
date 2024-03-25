---
# Leave the homepage title empty to use the site title
title: 'Gunes Ertunc'
date: 2022-02-28
type: landing

sections:
  - block: about.biography
    id: about
    content:
      title: 
      username: admin
  - block: skills
    content:
      title: Skills
      text: ''
      username: admin
    design:
      columns: '1'
  - block: experience
    content:
      title: Experience
      # Date format for experience
      #   Refer to https://docs.hugoblox.com/customization/#date-format
      date_format: Jan 2006
      # Experiences.
      #   Add/remove as many `experience` items below as you like.
      #   Required fields are `title`, `company`, and `date_start`.
      #   Leave `date_end` empty if it's your current employer.
      #   Begin multi-line descriptions with YAML's `|2-` multi-line prefix.
      items:
        - title: Geostatistics Advisor
          company: Airth.io
          company_url: 'https://airth.io/'
          company_logo: airth
          location: Tucson, AZ, Remote
          date_start: '2023-11-01'
          date_end: ''
          description:
        - title: Founder
          company: Orekalyptus Mining R&D Software
          company_url: ''
          company_logo: orekalyptus
          location: Hacettepe Teknokent 06800, Ankara, Türkiye 
          date_start: '2023-07-01'
          date_end: ''
          description: 
        - title: Assistant Professor, Mining Engineering
          company: Hacettepe University
          company_url: 'https://maden.hacettepe.edu.tr/en'
          company_logo: hu
          location: Beytepe 06800, Ankara, Türkiye 
          date_start: '2016-01-01'
          date_end: ''
          description: 
        - title: Research Assistant, Mining Engineering
          company: Hacettepe University
          company_url: 'https://maden.hacettepe.edu.tr/en'
          company_logo: hu
          location: Beytepe 06800, Ankara, Türkiye 
          date_start: '2007-12-01'
          date_end: '2016-12-01'
          description:
    design:
      columns: '2'
  - block: collection
    id: posts
    content:
      title: Recent Posts
      subtitle: ''
      text: ''
      # Choose how many pages you would like to display (0 = all pages)
      count: 5
      # Filter on criteria
      filters:
        folders:
          - post
        author: ""
        category: ""
        tag: ""
        exclude_featured: false
        exclude_future: false
        exclude_past: false
        publication_type: ""
      # Choose how many pages you would like to offset by
      offset: 0
      # Page order: descending (desc) or ascending (asc) date.
      order: desc
    design:
      # Choose a layout view
      view: compact
      columns: '2'
  - block: portfolio
    id: projects
    content:
      title: Projects
      filters:
        folders:
          - project
      # Default filter index (e.g. 0 corresponds to the first `filter_button` instance below).
      default_button_index: 0
      # Filter toolbar (optional).
      # Add or remove as many filters (`filter_button` instances) as you like.
      # To show all items, set `tag` to "*".
      # To filter by a specific tag, set `tag` to an existing tag name.
      # To remove the toolbar, delete the entire `filter_button` block.
      buttons:
        - name: All
          tag: '*'
        - name: Research
          tag: Research Project
        - name: Graduate
          tag: Graduate Project
    design:
      # Choose how many columns the section has. Valid values: '1' or '2'.
      columns: '1'
      view: showcase
      # For Showcase view, flip alternate rows?
      flip_alt_rows: true
  - block: tag_cloud
    content:
      title: Tag Cloud
    design:
      columns: '2'
---
