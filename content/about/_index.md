---
build:
  render: always
  list: local
cascade:
  # Hugo removed `headless: true`; use build options instead so the
  # header/main/sidebar fragments aren't rendered as standalone pages but their
  # images/audio still publish. The section landing (this page) still renders.
  build:
    render: never
    list: never
    publishResources: true
description: |
  A website template for Hugo developed by RStudio & Formspree and available for free.
show_header: false
sidebar_left: false
title: About
---

** index doesn't contain a body, just front matter above.
See the header / main / sidebar folders to edit the index.md files **
