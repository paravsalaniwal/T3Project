---
keywords: fastai
description: Testing CSV Files
title: Testing CSV Files
toc: true
categories: []
type: ap
week: 29
nb_path: _notebooks/2023-5-18-TestingCSVFiles.ipynb
layout: notebook
---

<!--
#################################################
### THIS FILE WAS AUTOGENERATED! DO NOT EDIT! ###
#################################################
# file to edit: _notebooks/2023-5-18-TestingCSVFiles.ipynb
-->

<div class="container" id="notebook-container">
        
    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">csv</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">from</span> <span class="nn">datetime</span> <span class="kn">import</span> <span class="n">datetime</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>

<span class="n">data</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;files/celtics.csv&#39;</span><span class="p">)</span>
<span class="n">x_pos</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">data</span><span class="p">))</span>
<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">data</span><span class="p">)</span>

<span class="n">X</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">iloc</span><span class="p">[:,</span> <span class="mi">0</span><span class="p">])</span>
<span class="n">Y</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">iloc</span><span class="p">[:,</span> <span class="mi">1</span><span class="p">])</span>

<span class="c1"># Plot the data using bar() method</span>
<span class="n">plt</span><span class="o">.</span><span class="n">bar</span><span class="p">(</span><span class="n">X</span><span class="p">,</span> <span class="n">Y</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;g&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s2">&quot;Points of each Atlanta Hawks Player&quot;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s2">&quot;Players&quot;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s2">&quot;Statistics&quot;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="n">rotation</span><span class="o">=</span><span class="mi">90</span><span class="p">)</span>

<span class="c1"># Show the plot</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">



<div class="output_png output_subarea ">
<img src="data:image/png;base64,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"
>
</div>

</div>

</div>
</div>

</div>
    {% endraw %}

</div>
 
