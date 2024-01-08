
<!DOCTYPE html>

<html lang="en">
<body class="jp-Notebook" data-jp-theme-light="true" data-jp-theme-name="JupyterLab Light">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">random</span> <span class="kn">import</span> <span class="n">shuffle</span>
<span class="kn">from</span> <span class="nn">random</span> <span class="kn">import</span> <span class="n">choice</span>
<span class="kn">import</span> <span class="nn">string</span>

<span class="k">def</span> <span class="nf">LuoSalasana</span><span class="p">():</span>

<span class="n">Password_List</span> <span class="o">=</span> <span class="p">[]</span>

<span class="n">Iso_kirjain_määrä</span> <span class="o">=</span> <span class="n">choice</span><span class="p">(</span><span class="nb">list</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span><span class="mi">5</span><span class="p">)))</span>
<span class="n">Pieni_kirjain_määrä</span> <span class="o">=</span> <span class="n">choice</span><span class="p">(</span><span class="nb">list</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">6</span><span class="p">,</span><span class="mi">15</span><span class="p">)))</span>
<span class="n">Numero_määrä</span> <span class="o">=</span> <span class="n">choice</span><span class="p">(</span><span class="nb">list</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">10</span><span class="p">)))</span>
<span class="n">Erikoismerkki_määrä</span> <span class="o">=</span> <span class="n">choice</span><span class="p">(</span><span class="nb">list</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">5</span><span class="p">)))</span>

<span class="n">counter</span> <span class="o">=</span> <span class="n">Iso_kirjain_määrä</span>
<span class="k">while</span> <span class="kc">True</span><span class="p">:</span>
    <span class="n">Iso_kirjain</span> <span class="o">=</span> <span class="n">choice</span><span class="p">(</span><span class="nb">list</span><span class="p">(</span><span class="n">string</span><span class="o">.</span><span class="n">ascii_uppercase</span><span class="p">))</span>
    <span class="n">Password_List</span> <span class="o">+=</span> <span class="n">Iso_kirjain</span>
    <span class="n">counter</span> <span class="o">-=</span> <span class="mi">1</span>
    <span class="k">if</span> <span class="n">counter</span> <span class="o">==</span> <span class="mi">0</span><span class="p">:</span>
        <span class="k">break</span>

<span class="n">counter</span> <span class="o">=</span> <span class="n">Pieni_kirjain_määrä</span>
<span class="k">while</span> <span class="kc">True</span><span class="p">:</span>
    <span class="n">Pieni_kirjain</span> <span class="o">=</span> <span class="n">choice</span><span class="p">(</span><span class="nb">list</span><span class="p">(</span><span class="n">string</span><span class="o">.</span><span class="n">ascii_lowercase</span><span class="p">))</span>
    <span class="n">Password_List</span> <span class="o">+=</span> <span class="n">Pieni_kirjain</span>
    <span class="n">counter</span> <span class="o">-=</span> <span class="mi">1</span>
    <span class="k">if</span> <span class="n">counter</span> <span class="o">==</span> <span class="mi">0</span><span class="p">:</span>
        <span class="k">break</span>

<span class="n">counter</span> <span class="o">=</span> <span class="n">Numero_määrä</span>
<span class="k">while</span> <span class="kc">True</span><span class="p">:</span>
    <span class="n">Numero</span> <span class="o">=</span> <span class="n">choice</span><span class="p">(</span><span class="nb">list</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">10</span><span class="p">)))</span>
    <span class="n">Password_List</span> <span class="o">+=</span> <span class="nb">str</span><span class="p">(</span><span class="n">Numero</span><span class="p">)</span>
    <span class="n">counter</span> <span class="o">-=</span> <span class="mi">1</span>
    <span class="k">if</span> <span class="n">counter</span> <span class="o">==</span> <span class="mi">0</span><span class="p">:</span>
        <span class="k">break</span>

<span class="n">Erikois</span> <span class="o">=</span> <span class="s2">"!#$%&amp;()*+,-.:;&lt;=&gt;?@[]^_{|}~"</span>
<span class="n">Erikoislista</span> <span class="o">=</span> <span class="p">[]</span>

<span class="k">for</span> <span class="n">merkki</span> <span class="ow">in</span> <span class="n">Erikois</span><span class="p">:</span>
    <span class="n">Erikoislista</span> <span class="o">+=</span> <span class="n">merkki</span>

<span class="n">counter</span> <span class="o">=</span> <span class="n">Erikoismerkki_määrä</span>
<span class="k">while</span> <span class="kc">True</span><span class="p">:</span>
    <span class="n">Erikoismerkki</span> <span class="o">=</span> <span class="n">choice</span><span class="p">(</span><span class="n">Erikoislista</span><span class="p">)</span>
    <span class="n">Password_List</span> <span class="o">+=</span> <span class="n">Erikoismerkki</span>
    <span class="n">counter</span> <span class="o">-=</span> <span class="mi">1</span>
    <span class="k">if</span> <span class="n">counter</span> <span class="o">==</span> <span class="mi">0</span><span class="p">:</span>
        <span class="k">break</span>
    
<span class="n">shuffle</span><span class="p">(</span><span class="n">Password_List</span><span class="p">)</span>

<span class="n">Salasana</span> <span class="o">=</span> <span class="s1">''</span>

<span class="k">for</span> <span class="n">merkki</span> <span class="ow">in</span> <span class="n">Password_List</span><span class="p">:</span>
    <span class="n">Salasana</span> <span class="o">+=</span> <span class="n">merkki</span>

<span class="k">return</span> <span class="n">Salasana</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">'Salasana on:'</span><span class="p">,</span> <span class="n">LuoSalasana</span><span class="p">())</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
<pre>Salasana on: 3@eJfuyp43W8p^n%
</pre>
</div>
</div>
</div>
</div>
</div>
</body>
</html>
