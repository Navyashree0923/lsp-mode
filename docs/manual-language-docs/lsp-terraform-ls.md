---
author: psibi
disqus: emacs-lsp
root_file: docs/manual-language-docs/lsp-terraform-ls.md
---

## Server note

Currently the mode supports two language servers. This [FAQ entry](https://emacs-lsp.github.io/lsp-mode/page/faq/#i-have-multiple-language-servers-registered-for-language-foo-which-one-will-be-used-when-opening-a-project)
shows how to choose a specific one. If you would want to go with the
official Hashicorp's language server, set this:

``` emacs-lisp
(setq lsp-disabled-clients '(tfls))
```

## terraform-ls

### Commands

#### `lsp-terraform-ls-validate`

Runs terraform validate on project root. All the violations are
published back in the buffer.

![](../examples/lsp-terraform-validate.png)

#### `lsp-terraform-ls-init`

Runs `terraform init` using terraform available from `$PATH`. You have
to make sure that that proper credentials are there.

Note that this is a synchronous action and will timeout after a
certain amount of time.

### Code Lens

This is an experimental feature which can be enabled via the option
`lsp-terraform-ls-enable-show-reference`:

``` emacs-lisp
(setq lsp-terraform-ls-enable-show-reference t)
```

This gif demonstrates how this feature is used:

![](../examples/lsp-terraform-code-lens-refs.gif)

### Semantic token support

Make sure to enable these two variables to ensure that you have
semantic token support for terraform mode:

``` emacs-lisp
(setq lsp-semantic-tokens-enable t)
(setq lsp-semantic-tokens-honor-refresh-requests t)
```

This is how the code looks without semantic tokens support:

![](../examples/lsp-terraform-without-semantic-token.png)

And with semantic token support you get more contextual information
via different faces:

![](../examples/lsp-terraform-with-semantic-token.png)

### Treeview controls

For this feature to work, make sure that you have [lsp-treemacs](https://github.com/emacs-lsp/lsp-treemacs)
installed.

#### Providers widget

![](../examples/lsp-terraform-providers-treemacs.png)

#### Module calls widget

![](../examples/lsp-terraform-modules-treemacs.png)
