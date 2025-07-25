---
# Leave the homepage title empty to use the site title
title: ""
date: 2022-10-24
type: landing

design:
  # Default section spacing
  spacing: "6rem"

sections:
  - block: resume-biography-3
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
      text: ""
      # Show a call-to-action button under your biography? (optional)
      button:
        text: Baixar CV
        url: uploads/cv_acsjunior.pdf
    design:
      css_class: dark
      background:
        # color: black
        # image:
        #   # Add your image background to `assets/media/`.
        #   filename: stacked-peaks.svg
        #   filters:
        #     brightness: 1.0
        #   size: cover
        #   position: center
        #   parallax: false
  - block: markdown
    id: bio
    content:
      title: 'Resumo Profissional'
      subtitle: ''
      text: |-
        Sou especialista em ciência de dados com foco em IA preditiva aplicada ao planejamento de demanda, atuando em uma das maiores operações de supply chain da América Latina.

        Desde 2020, atuo no Grupo Boticário, onde fui responsável por liderar uma evolução significativa na aplicação de modelos de IA preditiva voltados ao processo de S&OP. Fui promovido de cientista de dados a coordenador em 2022 e, atualmente, lidero uma equipe com 10 profissionais (cientistas de dados e engenheiros de ML) dedicada ao desenvolvimento, sustentação e melhoria contínua de modelos de previsão de demanda e soluções analíticas integradas ao processo de planejamento.

        Sob minha liderança, ampliamos o uso de modelos preditivos em diferentes unidades de negócio e canais de venda do grupo, melhoramos métricas como WMAPE e Bias, desenvolvemos ferramentas que aumentaram a aderência dos planejadores de demanda às previsões geradas e evoluímos em engenharia de software e MLOps, atingindo um alto nível de maturidade técnica. Essas práticas têm sido fundamentais para garantir previsões confiáveis, integradas ao fluxo de decisão e com alto valor percebido pelo negócio.

        Me destaco por promover um ambiente leve, colaborativo, tecnicamente exigente e com diversidade de gênero. Além disso, tenho genuína preocupação com o bem-estar e o desenvolvimento das pessoas. Como resultado, mantemos consistentemente elevados índices de engajamento no Team Culture (plataforma para mensuração do engajamento dos colaboradores).

        Sou formado em Análise e Desenvolvimento de Sistemas, Especialista em Data Science & Big Data e Mestre em Otimização Aplicada. Minha trajetória profissional anterior inclui experiências nos setores portuário, de engenharia, óleo e gás, saúde e e-commerce, o que contribuiu para o desenvolvimento de uma visão sistêmica e um perfil generalista e orientado ao negócio. Também considero como meus pontos fortes o raciocínio lógico apurado, a comunicação clara e a facilidade para nutrir boas relações.

        Possuo cidadania europeia (Portugal) e também atuo como mentor e professor, com paixão por compartilhar conhecimento e apoiar o desenvolvimento de profissionais.
    design:
      columns: '1'
  # - block: collection
  #   id: papers
  #   content:
  #     title: Featured Publications
  #     filters:
  #       folders:
  #         - publication
  #       featured_only: true
  #   design:
  #     view: article-grid
  #     columns: 2
  # - block: collection
  #   content:
  #     title: Recent Publications
  #     text: ""
  #     filters:
  #       folders:
  #         - publication
  #       exclude_featured: false
  #   design:
  #     view: citation
  # - block: collection
  #   id: talks
  #   content:
  #     title: Recent & Upcoming Talks
  #     filters:
  #       folders:
  #         - event
  #   design:
  #     view: article-grid
  #     columns: 1
  # - block: collection
  #   id: news
  #   content:
  #     title: Recent News
  #     subtitle: ''
  #     text: ''
  #     # Page type to display. E.g. post, talk, publication...
  #     page_type: post
  #     # Choose how many pages you would like to display (0 = all pages)
  #     count: 5
  #     # Filter on criteria
  #     filters:
  #       author: ""
  #       category: ""
  #       tag: ""
  #       exclude_featured: false
  #       exclude_future: false
  #       exclude_past: false
  #       publication_type: ""
  #     # Choose how many pages you would like to offset by
  #     offset: 0
  #     # Page order: descending (desc) or ascending (asc) date.
  #     order: desc
  #   design:
  #     # Choose a layout view
  #     view: date-title-summary
  #     # Reduce spacing
  #     spacing:
  #       padding: [0, 0, 0, 0]
  - block: cta-card
    demo: true # Only display this section in the Hugo Blox Builder demo site
    content:
      title: 👉 Build your own academic website like this
      text: |-
        This site is generated by Hugo Blox Builder - the FREE, Hugo-based open source website builder trusted by 250,000+ academics like you.

        <a class="github-button" href="https://github.com/HugoBlox/hugo-blox-builder" data-color-scheme="no-preference: light; light: light; dark: dark;" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star HugoBlox/hugo-blox-builder on GitHub">Star</a>

        Easily build anything with blocks - no-code required!
        
        From landing pages, second brains, and courses to academic resumés, conferences, and tech blogs.
      button:
        text: Get Started
        url: https://hugoblox.com/templates/
    design:
      card:
        # Card background color (CSS class)
        css_class: "bg-primary-700"
        css_style: ""
---
