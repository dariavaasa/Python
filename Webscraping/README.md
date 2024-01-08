<!DOCTYPE html>

<html lang="en">
<body class="jp-Notebook" data-jp-theme-light="true" data-jp-theme-name="JupyterLab Light">
<main>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<p>Instabot logins to Instagram and performs profile analytics.</p>
<p>At the moment:</p>
<ul>
<li>Only copypastes my followers and who I follow:</li>
<li>Returns an Excel with:<ul>
<li>Who I follow but they do not follow me back (I am are their fan)</li>
<li>Those who follow me mutually (we are each other's fans)</li>
<li>Those who follow me, but I do not follow them back (they are my fans)</li>
</ul>
</li>
</ul>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">selenium</span> <span class="kn">import</span> <span class="n">webdriver</span>
<span class="kn">from</span> <span class="nn">selenium.webdriver.common.by</span> <span class="kn">import</span> <span class="n">By</span>
<span class="kn">from</span> <span class="nn">selenium.webdriver.common.keys</span> <span class="kn">import</span> <span class="n">Keys</span>
<span class="kn">from</span> <span class="nn">selenium.webdriver</span> <span class="kn">import</span> <span class="n">ActionChains</span>
<span class="kn">from</span> <span class="nn">time</span> <span class="kn">import</span> <span class="n">sleep</span>
<span class="kn">import</span> <span class="nn">random</span>
<span class="kn">import</span> <span class="nn">time</span>
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
</pre></div>
</div>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<div class="highlight"><pre><span></span><span class="c1"># Start the browser</span>
<span class="n">driver</span> <span class="o">=</span> <span class="n">webdriver</span><span class="o">.</span><span class="n">Chrome</span><span class="p">()</span>

<span class="c1"># Start web driver</span>
<span class="n">driver</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="s1">'https://www.instagram.com/'</span><span class="p">)</span>

<span class="c1"># Manually in browser:</span>
<span class="c1"># 1. Decline optional cookies</span>
<span class="c1"># 2. Login</span>
<span class="c1"># 3. Accept "Save your login info?"</span>

<span class="c1"># Get login cookie not to login every time I run the robot</span>
<span class="n">cookie</span> <span class="o">=</span> <span class="n">driver</span><span class="o">.</span><span class="n">get_cookie</span><span class="p">(</span><span class="s1">'sessionid'</span><span class="p">)</span>
<span class="c1"># - returns a dictionary with my sessionid</span>

<span class="c1"># Print my cookie dictionary</span>
<span class="nb">print</span><span class="p">(</span><span class="n">cookie</span><span class="p">)</span>

<span class="c1"># Copy-paste login dictionary into a separate code block</span>
<span class="c1"># or save it into a separate txt and import (more preferable, for data security reasons).</span>
<span class="c1"># Usually typing directly into code in plain text (hardcoding) my login info or sessionid is not recommended</span>
<span class="c1"># My sessionid is in 'value'</span>

<span class="n">login_cookie</span> <span class="o">=</span> <span class="p">{</span>
    <span class="s1">'domain'</span><span class="p">:</span> <span class="s1">'.instagram.com'</span><span class="p">,</span>
    <span class="s1">'expiry'</span><span class="p">:</span> <span class="nb">int</span><span class="p">,</span>
    <span class="s1">'httpOnly'</span><span class="p">:</span> <span class="nb">bool</span><span class="p">,</span>
    <span class="s1">'name'</span><span class="p">:</span> <span class="s1">'sessionid'</span><span class="p">,</span>
    <span class="s1">'path'</span><span class="p">:</span> <span class="s1">'/'</span><span class="p">,</span>
    <span class="s1">'sameSite'</span><span class="p">:</span> <span class="s1">'str'</span><span class="p">,</span>
    <span class="s1">'secure'</span><span class="p">:</span> <span class="nb">bool</span><span class="p">,</span>
    <span class="s1">'value'</span><span class="p">:</span> <span class="s1">'str'</span>
    <span class="p">}</span>
</pre></div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="n">login_cookie</span> <span class="o">=</span> <span class="p">{</span>
        <span class="c1"># My login cookie</span>
    <span class="p">}</span>
</pre></div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Start the browser (again)</span>
<span class="n">driver</span> <span class="o">=</span> <span class="n">webdriver</span><span class="o">.</span><span class="n">Chrome</span><span class="p">()</span>

<span class="c1"># Pass username</span>
<span class="c1"># I can analyse any user when logged on (unless private and they did not accept me as a follower)</span>
<span class="c1"># username = input("Which Instagram username would you like to analyse?: @")</span>
<span class="c1"># I want analyse myself</span>
<span class="n">username</span> <span class="o">=</span> <span class="s1">'abc'</span>

<span class="c1"># Open a webpage:</span>
<span class="n">driver</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="s1">'https://www.instagram.com/'</span> <span class="o">+</span> <span class="n">username</span> <span class="o">+</span> <span class="s1">'/'</span><span class="p">)</span>

<span class="c1"># Wait about 6 to 7 sec to load the page</span>
<span class="n">sleep</span><span class="p">(</span><span class="n">random</span><span class="o">.</span><span class="n">uniform</span><span class="p">(</span><span class="mi">6</span><span class="p">,</span><span class="mi">7</span><span class="p">))</span>
<span class="c1"># Randomness is used to imitate human-like behaviour between clicks &amp; refreshes.</span>
<span class="c1"># Instagram recognises robots well, otherwise I can get my profile blocked.</span>

<span class="c1">#Decline cookies</span>
<span class="n">button</span> <span class="o">=</span> <span class="n">driver</span><span class="o">.</span><span class="n">find_element</span><span class="p">(</span><span class="n">By</span><span class="o">.</span><span class="n">XPATH</span><span class="p">,</span> <span class="s2">"/html/body/div[5]/div[1]/div/div[2]/div/div/div/div/div[2]/div/button[2]"</span><span class="p">)</span>

<span class="c1"># Click the button</span>
<span class="n">button</span><span class="o">.</span><span class="n">click</span><span class="p">()</span>

<span class="c1"># Pass login cookie</span>
<span class="n">driver</span><span class="o">.</span><span class="n">add_cookie</span><span class="p">(</span><span class="n">login_cookie</span><span class="p">)</span>

<span class="c1"># Refresh the page</span>
<span class="n">driver</span><span class="o">.</span><span class="n">refresh</span><span class="p">()</span>

<span class="c1"># Wait about 2 sec to load the page</span>
<span class="n">sleep</span><span class="p">(</span><span class="n">random</span><span class="o">.</span><span class="n">uniform</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">2</span><span class="p">))</span>
</pre></div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Open a webpage with followers:</span>
<span class="n">driver</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="s1">'https://www.instagram.com/'</span> <span class="o">+</span> <span class="n">username</span> <span class="o">+</span> <span class="s1">'/followers'</span><span class="p">)</span>

<span class="c1"># Wait about 2 sec to load the page</span>
<span class="n">sleep</span><span class="p">(</span><span class="n">random</span><span class="o">.</span><span class="n">uniform</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">2</span><span class="p">))</span>
</pre></div>
</div>
</div>
</div>
</div>
</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
<div class="highlight"><pre><span></span><span class="c1"># Div appears as a pop-up and is wrapped. In order to scrape it, we need to scroll it to unwrap.</span>
</pre></div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Navigate to the frame with TAB clicks (Key_down presses the button, and key_up releases it)</span>
<span class="n">ActionChains(driver)\
    .key_down(Keys.TAB)\
    .key_up(Keys.TAB)\
    .key_down(Keys.TAB)\
    .key_up(Keys.TAB)\
    .key_down(Keys.TAB)\
    .key_up(Keys.TAB)\
    .perform()</span>
</pre></div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Scrolling until there no new results, scraping.</span>
<span class="n">Followers</span> <span class="o">=</span> <span class="n">driver</span><span class="o">.</span><span class="n">find_element</span><span class="p">(</span><span class="n">By</span><span class="o">.</span><span class="n">XPATH</span><span class="p">,</span> <span class="s2">"/html/body/div[5]/div[1]/div/div[2]/div/div/div/div/div[2]/div/div/div[3]"</span><span class="p">)</span>
<span class="n">Followerstext</span> <span class="o">=</span> <span class="n">Followers</span><span class="o">.</span><span class="n">text</span>
<span class="n">timeout</span> <span class="o">=</span> <span class="n">time</span><span class="o">.</span><span class="n">time</span><span class="p">()</span> <span class="o">+</span> <span class="mi">60</span><span class="o">*</span><span class="mi">5</span>   <span class="c1"># Timeout 5 minutes from now</span>

<span class="k">while</span> <span class="kc">True</span><span class="p">:</span>
    <span class="n">ActionChains(driver)\\
    .key_down(Keys.PAGE_DOWN)\\
    .key_up(Keys.PAGE_DOWN)\\
    .key_down(Keys.PAGE_DOWN)\\
    .key_up(Keys.PAGE_DOWN)\\
    .key_down(Keys.PAGE_DOWN)\\
    .key_up(Keys.PAGE_DOWN)\\
    .key_down(Keys.PAGE_DOWN)\\
    .key_up(Keys.PAGE_DOWN)\\
    .perform()</span>
    <span class="n">sleep</span><span class="p">(</span><span class="n">random</span><span class="o">.</span><span class="n">uniform</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">3</span><span class="p">))</span>
    <span class="n">Followerstext1</span> <span class="o">=</span> <span class="n">Followers</span><span class="o">.</span><span class="n">text</span>
    <span class="k">if</span> <span class="n">Followerstext1</span> <span class="o">==</span> <span class="n">Followerstext</span> <span class="ow">or</span> <span class="n">time</span><span class="o">.</span><span class="n">time</span><span class="p">()</span> <span class="o">&gt;</span> <span class="n">timeout</span><span class="p">:</span>
        <span class="k">break</span>
    <span class="k">else</span><span class="p">:</span> 
        <span class="n">Followerstext</span> <span class="o">=</span> <span class="n">Followerstext1</span>

<span class="n">Followerstext</span> <span class="o">=</span> <span class="n">Followerstext1</span>
</pre></div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Converting string with results to the list of sub-lists, to convert it to a DataFrame later</span>
<span class="n">Followers</span> <span class="o">=</span> <span class="p">[</span><span class="n">row</span><span class="o">.</span><span class="n">split</span><span class="p">(</span><span class="s2">"</span><span class="se">\n</span><span class="s2">"</span><span class="p">)</span> <span class="k">for</span> <span class="n">row</span> <span class="ow">in</span> <span class="n">Followerstext</span><span class="o">.</span><span class="n">split</span><span class="p">(</span><span class="s2">"</span><span class="se">\n</span><span class="s2">Remove</span><span class="se">\n</span><span class="s2">"</span><span class="p">)]</span>
<span class="n">Followers</span><span class="p">[</span><span class="nb">len</span><span class="p">(</span><span class="n">Followers</span><span class="p">)</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">remove</span><span class="p">(</span><span class="s1">'Remove'</span><span class="p">)</span>

<span class="c1"># The sub-lists appear to be of different lenth: 1 to 4 values, separating them to different lists.</span>
<span class="c1"># 1 to 2 values: We mutually follow each other</span>
<span class="c1"># 3 to 4 values: I do not follow them (my fans)</span>
<span class="n">I_do_not_follow_back</span> <span class="o">=</span> <span class="p">[]</span>
<span class="n">I_do_not_follow_back2</span> <span class="o">=</span> <span class="p">[]</span>
<span class="n">Mutual</span> <span class="o">=</span> <span class="p">[]</span>
<span class="n">Mutual2</span> <span class="o">=</span> <span class="p">[]</span>

<span class="k">for</span> <span class="n">each</span> <span class="ow">in</span> <span class="n">Followers</span><span class="p">:</span>
    <span class="k">if</span> <span class="nb">len</span><span class="p">(</span><span class="n">each</span><span class="p">)</span> <span class="o">==</span> <span class="mi">2</span><span class="p">:</span>
        <span class="n">Mutual</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">each</span><span class="p">)</span>
    <span class="k">elif</span> <span class="nb">len</span><span class="p">(</span><span class="n">each</span><span class="p">)</span> <span class="o">==</span> <span class="mi">1</span><span class="p">:</span>
        <span class="n">Mutual2</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">each</span><span class="p">)</span>
    <span class="k">elif</span> <span class="nb">len</span><span class="p">(</span><span class="n">each</span><span class="p">)</span> <span class="o">==</span> <span class="mi">3</span><span class="p">:</span>
        <span class="n">I_do_not_follow_back2</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">each</span><span class="p">)</span>
    <span class="k">else</span><span class="p">:</span>
        <span class="n">I_do_not_follow_back</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">each</span><span class="p">)</span>
</pre></div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Converting mutual to a combined DataFrame</span>

<span class="n">Mutual</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">Mutual</span><span class="p">,</span> <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">'Id'</span><span class="p">,</span><span class="s1">'Desc'</span><span class="p">])</span>

<span class="n">Mutual2</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">Mutual2</span><span class="p">,</span> <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">'Id'</span><span class="p">])</span>

<span class="n">Mutual</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">Mutual</span><span class="p">,</span> <span class="n">Mutual2</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
<span class="n">Mutual</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[ ]:</div>
<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html" tabindex="0">
<div>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>Id</th>
<th>Desc</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>abc</td>
<td>abc</td>
</tr>
<tr>
<th>1</th>
<td>abc</td>
<td>abc</td>
</tr>
<tr>
<th>2</th>
<td>abc</td>
<td>Savva</td>
</tr>
<tr>
<th>3</th>
<td>abc</td>
<td>Януш</td>
</tr>
<tr>
<th>4</th>
<td>nk</td>
<td>Kata</td>
</tr>
<tr>
<th>...</th>
<td>...</td>
<td>...</td>
</tr>
<tr>
<th>0</th>
<td>abc</td>
<td>NaN</td>
</tr>
<tr>
<th>1</th>
<td>len</td>
<td>NaN</td>
</tr>
<tr>
<th>2</th>
<td>anna</td>
<td>NaN</td>
</tr>
<tr>
<th>3</th>
<td>shai</td>
<td>NaN</td>
</tr>
<tr>
<th>4</th>
<td>vki</td>
<td>NaN</td>
</tr>
</tbody>
</table>
<p>133 rows × 2 columns</p>
</div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Converting my fans to a combined DataFrame</span>

<span class="n">I_do_not_follow_back</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">I_do_not_follow_back</span><span class="p">,</span> <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">'Id'</span><span class="p">,</span><span class="s1">'·'</span><span class="p">,</span> <span class="s1">'Follow'</span><span class="p">,</span> <span class="s1">'Desc'</span><span class="p">])</span>
<span class="n">I_do_not_follow_back</span> <span class="o">=</span> <span class="n">I_do_not_follow_back</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s1">'·'</span><span class="p">,</span> <span class="s1">'Follow'</span><span class="p">],</span> <span class="n">axis</span> <span class="o">=</span> <span class="mi">1</span><span class="p">)</span>

<span class="n">I_do_not_follow_back2</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">I_do_not_follow_back2</span><span class="p">,</span> <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">'Id'</span><span class="p">,</span><span class="s1">'·'</span><span class="p">,</span> <span class="s1">'Follow'</span><span class="p">])</span>
<span class="n">I_do_not_follow_back2</span> <span class="o">=</span> <span class="n">I_do_not_follow_back2</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s1">'·'</span><span class="p">,</span> <span class="s1">'Follow'</span><span class="p">],</span> <span class="n">axis</span> <span class="o">=</span> <span class="mi">1</span><span class="p">)</span>

<span class="n">I_do_not_follow_back_3</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">I_do_not_follow_back</span><span class="p">,</span> <span class="n">I_do_not_follow_back2</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
<span class="n">I_do_not_follow_back_3</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[ ]:</div>
<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html" tabindex="0">
<div>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>Id</th>
<th>Desc</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>alex</td>
<td>David</td>
</tr>
<tr>
<th>1</th>
<td>helsinki</td>
<td>КЛИНИКА</td>
</tr>
<tr>
<th>2</th>
<td>gorge</td>
<td>Gorge</td>
</tr>
<tr>
<th>3</th>
<td>aka</td>
<td>Mary</td>
</tr>
<tr>
<th>4</th>
<td>chan</td>
<td>Chan</td>
</tr>
<tr>
<th>...</th>
<td>...</td>
<td>...</td>
</tr>
<tr>
<th>17</th>
<td>tampere</td>
<td>NaN</td>
</tr>
<tr>
<th>18</th>
<td>philip</td>
<td>NaN</td>
</tr>
<tr>
<th>19</th>
<td>hello</td>
<td>NaN</td>
</tr>
<tr>
<th>20</th>
<td>natashka</td>
<td>NaN</td>
</tr>
<tr>
<th>21</th>
<td>diana</td>
<td>NaN</td>
</tr>
</tbody>
</table>
<p>433 rows × 2 columns</p>
</div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Open a webpage with those who I follow:</span>
<span class="n">driver</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="s1">'https://www.instagram.com/'</span> <span class="o">+</span> <span class="n">username</span> <span class="o">+</span> <span class="s1">'/following'</span><span class="p">)</span>

<span class="c1"># Wait 2 sec to load the page</span>
<span class="n">sleep</span><span class="p">(</span><span class="n">random</span><span class="o">.</span><span class="n">uniform</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">2</span><span class="p">))</span>
</pre></div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Div appears as a pop-up and is wrapped. In order to scrape it, we need to scroll it to unwrap.</span>

<span class="c1"># Navigate to the frame</span>

<span class="n">ActionChains(driver)\\
    .key_down(Keys.TAB)\\
    .key_up(Keys.TAB)\\
    .key_down(Keys.TAB)\\
    .key_up(Keys.TAB)\\
    .key_down(Keys.TAB)\\
    .key_up(Keys.TAB)\\
    .perform()</span>
</pre></div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Scrolling until there no new results, scraping.</span>
<span class="n">Following</span> <span class="o">=</span> <span class="n">driver</span><span class="o">.</span><span class="n">find_element</span><span class="p">(</span><span class="n">By</span><span class="o">.</span><span class="n">XPATH</span><span class="p">,</span> <span class="s2">"/html/body/div[5]/div[1]/div/div[2]/div/div/div/div/div[2]/div/div/div[4]/div[1]"</span><span class="p">)</span>
<span class="n">Followingtext</span> <span class="o">=</span> <span class="n">Following</span><span class="o">.</span><span class="n">text</span>
<span class="n">timeout</span> <span class="o">=</span> <span class="n">time</span><span class="o">.</span><span class="n">time</span><span class="p">()</span> <span class="o">+</span> <span class="mi">60</span><span class="o">*</span><span class="mi">2</span>   <span class="c1"># Timeout 2 minutes from now</span>

<span class="k">while</span> <span class="kc">True</span><span class="p">:</span>
    <span class="n">ActionChains(driver)\\
        .key_down(Keys.PAGE_DOWN)\\
        .key_up(Keys.PAGE_DOWN)\\
        .key_down(Keys.PAGE_DOWN)\\
        .key_up(Keys.PAGE_DOWN)\\
        .key_down(Keys.PAGE_DOWN)\\
        .key_up(Keys.PAGE_DOWN)\\
        .key_down(Keys.PAGE_DOWN)\\
        .key_up(Keys.PAGE_DOWN)\\
        .perform()</span>
    <span class="n">sleep</span><span class="p">(</span><span class="n">random</span><span class="o">.</span><span class="n">uniform</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">3</span><span class="p">))</span>
    <span class="n">Followingtext1</span> <span class="o">=</span> <span class="n">Following</span><span class="o">.</span><span class="n">text</span>
    <span class="k">if</span> <span class="n">Followingtext1</span> <span class="o">==</span> <span class="n">Followingtext</span> <span class="ow">or</span> <span class="n">time</span><span class="o">.</span><span class="n">time</span><span class="p">()</span> <span class="o">&gt;</span> <span class="n">timeout</span><span class="p">:</span>
        <span class="k">break</span>
    <span class="k">else</span><span class="p">:</span> 
        <span class="n">Followingtext</span> <span class="o">=</span> <span class="n">Followingtext1</span>

<span class="n">Followingtext</span> <span class="o">=</span> <span class="n">Followingtext1</span>
</pre></div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Converting string with results to the list of sub-lists, to convert it to a DataFrame later</span>
<span class="n">Following</span> <span class="o">=</span> <span class="p">[</span><span class="n">row</span><span class="o">.</span><span class="n">split</span><span class="p">(</span><span class="s2">"</span><span class="se">\n</span><span class="s2">"</span><span class="p">)</span> <span class="k">for</span> <span class="n">row</span> <span class="ow">in</span> <span class="n">Followingtext</span><span class="o">.</span><span class="n">split</span><span class="p">(</span><span class="s2">"</span><span class="se">\n</span><span class="s2">Following</span><span class="se">\n</span><span class="s2">"</span><span class="p">)]</span>
<span class="n">Following</span><span class="p">[</span><span class="nb">len</span><span class="p">(</span><span class="n">Following</span><span class="p">)</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span><span class="o">.</span><span class="n">remove</span><span class="p">(</span><span class="s1">'Following'</span><span class="p">)</span>

<span class="c1"># Converting to a DataFrame</span>
<span class="n">Following</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">Following</span><span class="p">,</span> <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">'Id'</span><span class="p">,</span><span class="s1">'Desc'</span><span class="p">])</span>

<span class="c1"># Excluding those who follow me back, to find out who I follow but they who does not follow me back (I am their fan)</span>
<span class="n">Do_not_follow_back</span> <span class="o">=</span> <span class="n">Following</span><span class="p">[</span><span class="o">~</span><span class="n">Following</span><span class="p">[</span><span class="s1">'Id'</span><span class="p">]</span><span class="o">.</span><span class="n">isin</span><span class="p">(</span><span class="n">Mutual</span><span class="p">[</span><span class="s1">'Id'</span><span class="p">]</span><span class="o">.</span><span class="n">values</span><span class="o">.</span><span class="n">tolist</span><span class="p">())]</span>
<span class="n">Do_not_follow_back</span>
</pre></div>
</div>
</div>
</div>
</div>
<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>
<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">
<div class="jp-OutputPrompt jp-OutputArea-prompt">Out[ ]:</div>
<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html" tabindex="0">
<div>
<table border="1" class="dataframe">
<thead>
<tr style="text-align: right;">
<th></th>
<th>Id</th>
<th>Desc</th>
</tr>
</thead>
<tbody>
<tr>
<th>33</th>
<td>emmi</td>
<td>Emmi</td>
</tr>
<tr>
<th>42</th>
<td>pika</td>
<td>Sofiya</td>
</tr>
<tr>
<th>56</th>
<td>qua</td>
<td>Qua</td>
</tr>
<tr>
<th>58</th>
<td>madi</td>
<td>Madi</td>
</tr>
<tr>
<th>60</th>
<td>artturi</td>
<td>Artturi</td>
</tr>
<tr>
<th>...</th>
<td>...</td>
<td>...</td>
</tr>
<tr>
<th>220</th>
<td>moods</td>
<td>Moods</td>
</tr>
<tr>
<th>221</th>
<td>franck</td>
<td>Franck</td>
</tr>
<tr>
<th>222</th>
<td>moll</td>
<td>Möller</td>
</tr>
<tr>
<th>223</th>
<td>daniel</td>
<td>Daniel</td>
</tr>
<tr>
<th>224</th>
<td>dachshund</td>
<td>🐶DACHSHUND LOVER 🐶</td>
</tr>
</tbody>
</table>
<p>92 rows × 2 columns</p>
</div>
</div>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Create a new excel workbook</span>
<span class="n">writer</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">ExcelWriter</span><span class="p">(</span><span class="s1">'Instagram.xlsx'</span><span class="p">,</span> <span class="n">engine</span><span class="o">=</span><span class="s1">'xlsxwriter'</span><span class="p">)</span>

<span class="c1"># Write DataFrames to Excel without index, set column length</span>
<span class="n">Do_not_follow_back</span><span class="o">.</span><span class="n">to_excel</span><span class="p">(</span><span class="n">writer</span><span class="p">,</span> <span class="n">sheet_name</span><span class="o">=</span><span class="s1">'They not follow back'</span><span class="p">,</span> <span class="n">index</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
<span class="n">worksheet</span> <span class="o">=</span> <span class="n">writer</span><span class="o">.</span><span class="n">sheets</span><span class="p">[</span><span class="s1">'They not follow back'</span><span class="p">]</span>
<span class="n">worksheet</span><span class="o">.</span><span class="n">set_column</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">25</span><span class="p">)</span>

<span class="n">Mutual</span><span class="o">.</span><span class="n">to_excel</span><span class="p">(</span><span class="n">writer</span><span class="p">,</span> <span class="n">sheet_name</span><span class="o">=</span><span class="s1">'Mutual'</span><span class="p">,</span> <span class="n">index</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
<span class="n">worksheet</span> <span class="o">=</span> <span class="n">writer</span><span class="o">.</span><span class="n">sheets</span><span class="p">[</span><span class="s1">'Mutual'</span><span class="p">]</span>
<span class="n">worksheet</span><span class="o">.</span><span class="n">set_column</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">25</span><span class="p">)</span>

<span class="n">I_do_not_follow_back</span><span class="o">.</span><span class="n">to_excel</span><span class="p">(</span><span class="n">writer</span><span class="p">,</span> <span class="n">sheet_name</span><span class="o">=</span><span class="s1">'I do not follow back'</span><span class="p">,</span> <span class="n">index</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
<span class="n">worksheet</span> <span class="o">=</span> <span class="n">writer</span><span class="o">.</span><span class="n">sheets</span><span class="p">[</span><span class="s1">'I do not follow back'</span><span class="p">]</span>
<span class="n">worksheet</span><span class="o">.</span><span class="n">set_column</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">25</span><span class="p">)</span>

<span class="c1"># Save workbook</span>
<span class="n">writer</span><span class="o">.</span><span class="n">close</span><span class="p">()</span>
</pre></div>
</div>
</div>
</div>
</div>
</div>
</main>
</body>
</html>
