---
title: 'Home'
date: 2023-10-24
type: landing

design:
  # Default section spacing
  spacing: "0rem"

sections:

#  - block: cta-image-paragraph
#    id: solutions
#    content:
#      items:
##        - title: 
##          text: 
##          feature_icon: check
##          features:
##          # Upload image to `assets/media/` and reference the filename here
##          image: pipesnake_Logo.png
##          button:
##            text: Get Started
##            url: https://hugoblox.com/templates/
#        - title: _pipesnake_
#          text: The easy-to-install phylogenomics workflow 🐍
#          image: pipesnake_Logo.png
##         features:
##            - "Easy, Fast, Reproducible"
##            - "Fast"
##            - "Reproducible"
#          # Upload image to `assets/media/` and reference the filename here
#          button:
#            text: Get Started
#            url: https://iangbrennan.github.io/pipesnake2/docs


  - block: hero
    content:
      title: _pipesnake_
      image:
        # Reference an image in your `assets/media/` folder
        filename: pipesnake_Logo.png
      text: An all-in-one phylogenomics workflow 🐍
      primary_action:
        text: Get Started
        url: https://iangbrennan.github.io/pipesnake2/docs
        icon: rocket-launch
    design:
#      css_class: dark
      image:
        filename: pipesnake_Logo.png
#      background:
#        color: black
#        image:
#          # Add your image background to `assets/media/`.
#          filename: pipesnake_Logo.png
#          filters:
#            brightness: 1.0
#          size: cover
#          position: center
#          parallax: false
#      secondary_action:
#        text: Read the docs
#        url: /docs/
#      announcement:
#        text: "Announcing the release of version 2."
#        link:
#          text: "Read more"
#          url: "/blog/"
#    design:
#      spacing:
#        padding: [0, 0, 0, 0]
#        margin: [0, 0, 0, 0]
#      # For full-screen, add `min-h-screen` below
#      css_class: ""
#      background:
#        color: ""
#        image:
#          # Add your image background to `assets/media/`.
#          filename: ""
#          filters:
#            brightness: 0.5
#  - block: stats
#    content:
#      items:
#        - statistic: "1M+"
#          description: |
#            Websites built  
#            with Hugo Blox
#        - statistic: "10k+"
#          description: |
#            GitHub stars  
#            since 2016
#        - statistic: "3k+"
#          description: |
#            Discord community  
#            for support
#    design:
#      # Section background color (CSS class)
#      css_class: "bg-gray-100 dark:bg-gray-800"
#      # Reduce spacing
#      spacing:
#        padding: ["1rem", 0, "1rem", 0]
    design:
      spacing:
        padding: [0, 0, 0, 0]
        margin: [0, 0, 0, 0]
      # For full-screen, add `min-h-screen` below


  - block: features
    id: features
    content:
#      title: Features
#      text: Collaborate, publish, and maintain technical knowledge with an all-in-one documentation site. Used by 100,000+ startups, enterprises, and researchers.
# icon names: https://heroicons.com/
      items:
        - name: Easy
          icon: sparkles
          description: Download and launch with one command using [`nextflow`](https://www.nextflow.io/).
        - name: Fast
          icon: bolt
          description: Highly efficient and parallelized for quick results, with flexible stop/start points to suit your needs.
        - name: Reproducible
          icon: arrow-path
          description: Automatic reporting of software and usage statistics, cached results, and easy-to-resume runs. 
#        - name: Optimized SEO
#          icon: magnifying-glass
#          description: Automatic sitemaps, RSS feeds, and rich metadata take the pain out of #SEO and syndication.
#        - name: Highly Rated
#          icon: star
#          description: Rated 5-stars by the community.
#        - name: Swappable Blocks
#          icon: rectangle-group
#          description: Build your pages with blocks - no coding required!
#  - block: cta-card
#    content:
#      title: "Start Writing with the #1 Effortless Documentation Platform"
#      text: Hugo Blox Docs Theme brings all your technical knowledge together in a single, #centralized knowledge base. Easily search and edit it with the tools you use every day!
#      button:
#        text: Get Started
#        url: https://hugoblox.com/templates/details/docs/
#    design:
#      card:
#        # Card background color (CSS class)
#        css_class: "bg-primary-700"
#        css_style: ""
---

