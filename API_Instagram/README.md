<!DOCTYPE html>
<html lang="en">
<body class="jp-Notebook" data-jp-theme-light="true" data-jp-theme-name="JupyterLab Light">
<main>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># First you need to get an access_token, read more here:</span>
<span class="c1"># https://developers.facebook.com/docs/instagram-basic-display-api/guides</span>
<span class="n">access_token</span> <span class="o">=</span> <span class="s1">'Your access token'</span>
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
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Request data</span>
<span class="n">res_data</span> <span class="o">=</span> <span class="n">requests</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="s1">'https://graph.instagram.com/me'</span><span class="p">,</span> <span class="n">params</span><span class="o">=</span><span class="p">{</span><span class="s1">'access_token'</span><span class="p">:</span> <span class="n">access_token</span><span class="p">,</span> <span class="s1">'fields'</span><span class="p">:</span> <span class="s1">'account_type,id,username,media_count,media'</span><span class="p">})</span>
<span class="n">res_data</span><span class="o">.</span><span class="n">status_code</span>
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
<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain" tabindex="0">
<pre>200</pre>
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
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># data about your profile:</span>
<span class="n">data</span> <span class="o">=</span> <span class="n">res_data</span><span class="o">.</span><span class="n">json</span><span class="p">()</span>
<span class="n">List</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">data</span><span class="o">.</span><span class="n">keys</span><span class="p">())</span>
<span class="n">profile_data</span> <span class="o">=</span> <span class="p">{</span><span class="n">key</span><span class="p">:</span> <span class="n">data</span><span class="p">[</span><span class="n">key</span><span class="p">]</span> <span class="k">for</span> <span class="n">key</span> <span class="ow">in</span> <span class="n">List</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="mi">4</span><span class="p">]}</span>
<span class="n">profile_data</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="o">.</span><span class="n">from_dict</span><span class="p">(</span><span class="n">profile_data</span><span class="p">,</span> <span class="n">orient</span><span class="o">=</span><span class="s1">'index'</span><span class="p">)</span><span class="o">.</span><span class="n">T</span>
<span class="n">profile_data</span>
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
<th>account_type</th>
<th>id</th>
<th>username</th>
<th>media_count</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>MEDIA_CREATOR</td>
<td>7085366198187459</td>
<td>dariaverart</td>
<td>696</td>
</tr>
</tbody>
</table>
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
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># get IDs of 25 most recent posts:</span>
<span class="n">media</span> <span class="o">=</span> <span class="n">data</span><span class="p">[</span><span class="s1">'media'</span><span class="p">][</span><span class="s1">'data'</span><span class="p">]</span>
<span class="n">media</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">media</span><span class="p">)</span>
<span class="n">media</span> <span class="o">=</span> <span class="n">media</span><span class="o">.</span><span class="n">rename</span><span class="p">(</span><span class="n">columns</span><span class="o">=</span><span class="p">{</span><span class="s1">'id'</span><span class="p">:</span><span class="s1">'media_id (post_id)'</span><span class="p">})</span>
<span class="n">media</span>
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
<th>media_id (post_id)</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>18366779269075643</td>
</tr>
<tr>
<th>1</th>
<td>18019441633857389</td>
</tr>
<tr>
<th>2</th>
<td>17986308410439878</td>
</tr>
<tr>
<th>3</th>
<td>18292668379176780</td>
</tr>
<tr>
<th>4</th>
<td>18393503263034510</td>
</tr>
<tr>
<th>5</th>
<td>17972649833460061</td>
</tr>
<tr>
<th>6</th>
<td>17926234196684223</td>
</tr>
<tr>
<th>7</th>
<td>17979361361525701</td>
</tr>
<tr>
<th>8</th>
<td>18087239866375607</td>
</tr>
<tr>
<th>9</th>
<td>18058914745449094</td>
</tr>
<tr>
<th>10</th>
<td>18007105288821697</td>
</tr>
<tr>
<th>11</th>
<td>17876414525938940</td>
</tr>
<tr>
<th>12</th>
<td>18017686240661397</td>
</tr>
<tr>
<th>13</th>
<td>18376841887058258</td>
</tr>
<tr>
<th>14</th>
<td>17997652588884703</td>
</tr>
<tr>
<th>15</th>
<td>17998285165987500</td>
</tr>
<tr>
<th>16</th>
<td>18000809131938278</td>
</tr>
<tr>
<th>17</th>
<td>18002658691881413</td>
</tr>
<tr>
<th>18</th>
<td>17904184871713094</td>
</tr>
<tr>
<th>19</th>
<td>18005484004700760</td>
</tr>
<tr>
<th>20</th>
<td>18075958423371734</td>
</tr>
<tr>
<th>21</th>
<td>18004205518748450</td>
</tr>
<tr>
<th>22</th>
<td>18213160696242325</td>
</tr>
<tr>
<th>23</th>
<td>17995097449796427</td>
</tr>
<tr>
<th>24</th>
<td>18222229546175069</td>
</tr>
</tbody>
</table>
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
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Get detailed data about your most recent posts:</span>
<span class="n">res</span> <span class="o">=</span> <span class="n">requests</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="s1">'https://graph.instagram.com/me/media'</span><span class="p">,</span> <span class="n">params</span><span class="o">=</span><span class="p">{</span>
        <span class="s1">'access_token'</span><span class="p">:</span> <span class="n">access_token</span><span class="p">,</span>
        <span class="s1">'fields'</span><span class="p">:</span> <span class="s1">'caption,id,is_shared_to_feed,media_type,media_url,permalink,thumbnail_url,timestamp,username,children'</span>
        <span class="p">})</span>
<span class="n">res</span><span class="o">.</span><span class="n">status_code</span>
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
<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain" tabindex="0">
<pre>200</pre>
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
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Convert data to a DataFrame</span>
<span class="n">data</span> <span class="o">=</span> <span class="n">res</span><span class="o">.</span><span class="n">json</span><span class="p">()</span>
<span class="n">data</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">data</span><span class="p">[</span><span class="s1">'data'</span><span class="p">])</span>
<span class="n">data</span> <span class="o">=</span> <span class="n">data</span><span class="p">[[</span><span class="s1">'id'</span><span class="p">,</span> <span class="s1">'media_type'</span><span class="p">,</span> <span class="s1">'permalink'</span><span class="p">,</span> <span class="s1">'timestamp'</span><span class="p">,</span> <span class="s1">'children'</span><span class="p">,</span> <span class="s1">'media_url'</span><span class="p">,</span> <span class="s1">'caption'</span><span class="p">]]</span>
<span class="n">data</span><span class="p">[</span><span class="s1">'caption'</span><span class="p">]</span> <span class="o">=</span> <span class="n">data</span><span class="p">[</span><span class="s1">'caption'</span><span class="p">]</span><span class="o">.</span><span class="n">str</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="s1">'</span><span class="se">\n</span><span class="s1">'</span><span class="p">,</span> <span class="s1">' '</span><span class="p">)</span>
<span class="n">data</span><span class="p">[</span><span class="s1">'timestamp'</span><span class="p">]</span> <span class="o">=</span> <span class="p">[</span><span class="n">datetime</span><span class="o">.</span><span class="n">fromisoformat</span><span class="p">(</span><span class="n">i</span><span class="p">)</span> <span class="o">+</span> <span class="n">timedelta</span><span class="p">(</span><span class="n">hours</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span> <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="n">data</span><span class="p">[</span><span class="s1">'timestamp'</span><span class="p">]]</span>
<span class="n">data</span><span class="p">[</span><span class="s1">'timestamp'</span><span class="p">]</span> <span class="o">=</span> <span class="n">data</span><span class="p">[</span><span class="s1">'timestamp'</span><span class="p">]</span><span class="o">.</span><span class="n">dt</span><span class="o">.</span><span class="n">tz_convert</span><span class="p">(</span><span class="kc">None</span><span class="p">)</span>
<span class="n">data</span><span class="p">[</span><span class="s1">'media_type'</span><span class="p">]</span> <span class="o">=</span> <span class="p">[</span><span class="s1">'CAROUSEL'</span> <span class="k">if</span> <span class="n">i</span> <span class="o">==</span> <span class="s1">'CAROUSEL_ALBUM'</span> <span class="k">else</span> <span class="n">i</span> <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="n">data</span><span class="p">[</span><span class="s1">'media_type'</span><span class="p">]]</span>
<span class="n">data</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">data</span><span class="p">[</span><span class="s1">'media_type'</span><span class="p">]</span> <span class="o">==</span> <span class="s1">'CAROUSEL'</span><span class="p">,</span> <span class="s1">'media_url'</span><span class="p">]</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">NaN</span>
<span class="c1"></span>
<span class="c1"># Get additional data for each picture of a Carousel</span>
<span class="n">List</span> <span class="o">=</span> <span class="p">[]</span>
<span class="k">for</span> <span class="n">each</span> <span class="ow">in</span> <span class="n">data</span><span class="p">[</span><span class="s1">'id'</span><span class="p">]:</span>
        <span class="k">try</span><span class="p">:</span>
                <span class="n">res2</span> <span class="o">=</span> <span class="n">requests</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="s1">'https://graph.instagram.com/'</span> <span class="o">+</span> <span class="n">each</span> <span class="o">+</span> <span class="s1">'/children'</span><span class="p">,</span> <span class="n">params</span><span class="o">=</span><span class="p">{</span>
                        <span class="s1">'access_token'</span><span class="p">:</span> <span class="n">access_token</span><span class="p">,</span>
                        <span class="s1">'fields'</span><span class="p">:</span> <span class="s1">'data,paging,media_url'</span>
                        <span class="p">})</span>
                <span class="n">child</span> <span class="o">=</span> <span class="n">res2</span><span class="o">.</span><span class="n">json</span><span class="p">()</span>
                <span class="n">child</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">child</span><span class="p">[</span><span class="s1">'data'</span><span class="p">])</span><span class="o">.</span><span class="n">media_url</span><span class="o">.</span><span class="n">tolist</span><span class="p">()</span>
                <span class="n">child</span> <span class="o">=</span> <span class="s1">', '</span><span class="o">.</span><span class="n">join</span><span class="p">(</span><span class="n">child</span><span class="p">)</span>
                <span class="n">List</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">child</span><span class="p">)</span>
        <span class="k">except</span><span class="p">:</span>
                <span class="n">List</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">NaN</span><span class="p">)</span>
<span class="n">List</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">List</span><span class="p">)</span>
<span class="n">data</span><span class="p">[</span><span class="s1">'children'</span><span class="p">]</span> <span class="o">=</span> <span class="n">List</span>

<span class="n">data</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">data</span><span class="p">[</span><span class="s1">'media_url'</span><span class="p">]</span><span class="o">.</span><span class="n">isnull</span><span class="p">(),</span> <span class="s1">'media_url'</span><span class="p">]</span> <span class="o">=</span> <span class="n">data</span><span class="p">[</span><span class="s1">'children'</span><span class="p">]</span>
<span class="n">data</span> <span class="o">=</span> <span class="n">data</span><span class="p">[[</span><span class="s1">'id'</span><span class="p">,</span> <span class="s1">'media_type'</span><span class="p">,</span> <span class="s1">'permalink'</span><span class="p">,</span> <span class="s1">'timestamp'</span><span class="p">,</span> <span class="s1">'media_url'</span><span class="p">,</span> <span class="s1">'caption'</span><span class="p">]]</span>

<span class="n">data</span>
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
<th>id</th>
<th>media_type</th>
<th>permalink</th>
<th>timestamp</th>
<th>media_url</th>
<th>caption</th>
</tr>
</thead>
<tbody>
<tr>
<th>0</th>
<td>18366779269075643</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/CzZpSzPNwmm/</td>
<td>2023-11-08 23:48:25</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>Fairytale by @oduvaha Model: @dariaverart  #pu...</td>
</tr>
<tr>
<th>1</th>
<td>18019441633857389</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/CzTByC8A47z/</td>
<td>2023-11-06 10:07:43</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>Fairytale by @oduvaha Model: @dariaverart  #pu...</td>
</tr>
<tr>
<th>2</th>
<td>17986308410439878</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/CzM6xl5tc5d/</td>
<td>2023-11-04 01:11:02</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>Happy birthday to me 🤗  Fairytale by @oduvaha ...</td>
</tr>
<tr>
<th>3</th>
<td>18292668379176780</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/CzF8DYjt0yp/</td>
<td>2023-11-01 08:07:31</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>First snow, November or Halloween will not sto...</td>
</tr>
<tr>
<th>4</th>
<td>18393503263034510</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/Cy_GbH0NCUe/</td>
<td>2023-10-29 16:23:28</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>Fairytale by @oduvaha Model: @dariaverart  #pu...</td>
</tr>
<tr>
<th>5</th>
<td>17972649833460061</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/Cypt5Z8NUfm/</td>
<td>2023-10-21 09:05:06</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>Fairytale by @oduvaha Model: @dariaverart  #pu...</td>
</tr>
<tr>
<th>6</th>
<td>17926234196684223</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/Cx-LiYfA6gg/</td>
<td>2023-10-04 11:17:31</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>Fairytale by @oduvaha Model: @dariaverart</td>
</tr>
<tr>
<th>7</th>
<td>17979361361525701</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/Cx4lxu9NmY0/</td>
<td>2023-10-02 07:11:21</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>Fairytale by @oduvaha Model: @dariaverart</td>
</tr>
<tr>
<th>8</th>
<td>18087239866375607</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/CxcR58vtuYB/</td>
<td>2023-09-21 07:18:59</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>Fairytale series by @oduvaha Model: me, myself...</td>
</tr>
<tr>
<th>9</th>
<td>18058914745449094</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/CxFZ6zDgHT4/</td>
<td>2023-09-12 10:06:28</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>Water treatments for a true lady.  Model: @tat...</td>
</tr>
<tr>
<th>10</th>
<td>18007105288821697</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/CwAp_drtIPK/</td>
<td>2023-08-16 17:19:19</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>In red and blue. Which one is best?  Model: @m...</td>
</tr>
<tr>
<th>11</th>
<td>17876414525938940</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/Cv5Mncrty6s/</td>
<td>2023-08-13 19:47:57</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>Under the ground   Model: @tatjanadenemec Make...</td>
</tr>
<tr>
<th>12</th>
<td>18017686240661397</td>
<td>VIDEO</td>
<td>https://www.instagram.com/reel/CvnbzPigBsD/</td>
<td>2023-08-06 22:15:47</td>
<td>https://scontent-hel3-1.cdninstagram.com/o1/v/...</td>
<td>Kallio Block Party @kallioblockparty</td>
</tr>
<tr>
<th>13</th>
<td>18376841887058258</td>
<td>IMAGE</td>
<td>https://www.instagram.com/p/CvmGN_yg_GB/</td>
<td>2023-08-06 09:46:28</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>Fearless and fierce, a force to be reckoned wi...</td>
</tr>
<tr>
<th>14</th>
<td>17997652588884703</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/CvXabZxNlz7/</td>
<td>2023-07-31 16:54:28</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>Partly cloudy ☁️ Переменная облачность  Model:...</td>
</tr>
<tr>
<th>15</th>
<td>17998285165987500</td>
<td>VIDEO</td>
<td>https://www.instagram.com/reel/CvDJJzet6GD/</td>
<td>2023-07-23 19:59:55</td>
<td>https://scontent-hel3-1.cdninstagram.com/o1/v/...</td>
<td>@7585_berlin at Helsinki Fashion Week</td>
</tr>
<tr>
<th>16</th>
<td>18000809131938278</td>
<td>VIDEO</td>
<td>https://www.instagram.com/reel/CvCo-6kN5d5/</td>
<td>2023-07-23 15:18:10</td>
<td>https://scontent-hel3-1.cdninstagram.com/o1/v/...</td>
<td>@ellishaboie at Helsinki fashion week</td>
</tr>
<tr>
<th>17</th>
<td>18002658691881413</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/CuC49bLtH_3/</td>
<td>2023-06-28 21:05:48</td>
<td>https://scontent-hel3-1.cdninstagram.com/o1/v/...</td>
<td>Tarifa #nofilter   This absolutely amazing pla...</td>
</tr>
<tr>
<th>18</th>
<td>17904184871713094</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/CtG7w6gtTF8/</td>
<td>2023-06-05 14:15:53</td>
<td>https://scontent-hel3-1.cdninstagram.com/o1/v/...</td>
<td>Nerja is a hidden gem located on the Costa del...</td>
</tr>
<tr>
<th>19</th>
<td>18005484004700760</td>
<td>VIDEO</td>
<td>https://www.instagram.com/reel/Cs64mtUgyzo/</td>
<td>2023-05-31 21:58:15</td>
<td>https://scontent-hel3-1.cdninstagram.com/o1/v/...</td>
<td>A horse show.</td>
</tr>
<tr>
<th>20</th>
<td>18075958423371734</td>
<td>VIDEO</td>
<td>https://www.instagram.com/reel/Cs64Bd0gevU/</td>
<td>2023-05-31 21:55:13</td>
<td>https://scontent-hel3-1.cdninstagram.com/o1/v/...</td>
<td>A horse show</td>
</tr>
<tr>
<th>21</th>
<td>18004205518748450</td>
<td>VIDEO</td>
<td>https://www.instagram.com/reel/Cs62uJGgs1A/</td>
<td>2023-05-31 21:46:33</td>
<td>https://scontent-hel3-1.cdninstagram.com/o1/v/...</td>
<td>Flamenco and horse show</td>
</tr>
<tr>
<th>22</th>
<td>18213160696242325</td>
<td>VIDEO</td>
<td>https://www.instagram.com/reel/Cs33ujrpN9U/</td>
<td>2023-05-30 17:53:20</td>
<td>https://scontent-hel3-1.cdninstagram.com/o1/v/...</td>
<td>Watching beautiful creatures in the Butterfly ...</td>
</tr>
<tr>
<th>23</th>
<td>17995097449796427</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/CsyIUxGgQ6b/</td>
<td>2023-05-28 12:21:35</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>RGB ♥️💛💚 Which photo is your favourite?  Model...</td>
</tr>
<tr>
<th>24</th>
<td>18222229546175069</td>
<td>CAROUSEL</td>
<td>https://www.instagram.com/p/CsbyN_YskfI/</td>
<td>2023-05-19 20:05:07</td>
<td>https://scontent-hel3-1.cdninstagram.com/v/t51...</td>
<td>Juicy 🧃 In a world that demands flexibility, s...</td>
</tr>
</tbody>
</table>
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
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Export to Excel</span>
<span class="n">data</span><span class="o">.</span><span class="n">to_excel</span><span class="p">(</span><span class="s1">'Instagram.xlsx'</span><span class="p">,</span> <span class="n">sheet_name</span><span class="o">=</span><span class="s1">'Media'</span><span class="p">,</span> <span class="n">index</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
</pre></div>
</div>
</div>
</div>
</div>
</div>
</main>
</body>
</html>
