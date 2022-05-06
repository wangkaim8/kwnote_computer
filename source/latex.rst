Latex notes
===========

Convert Latex to word
---------------------

install pandoc (2.1.10) and pandoc-crossref and

.. code-block::

 $: sudo apt install pandoc pandoc-citeproc
 $: pandoc mylatex.tex --filter pandoc-crossref --bibliography=Refer.bib -o myword.docx
