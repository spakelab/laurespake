---
build:
  render: always
  list: local
cascade:
  type: lab
  # Hugo removed `headless: true`; use build options instead so the
  # sidebar fragment isn't rendered as a standalone page but its resources still
  # publish. The section landing (this page) still renders.
  build:
    render: never
    list: never
    publishResources: true
description: |
  A website template for Hugo developed by RStudio & Formspree and available for free.
show_header: false
sidebar_left: false
title: Our Lab
---

** index doesn't contain a body, just front matter above.
See the header / main / sidebar folders to edit the index.md files **
