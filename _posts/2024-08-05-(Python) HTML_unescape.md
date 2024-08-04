---
categories: 
 - Python
layout: single
title: "(Python) HTML Entities"
---

# HTML 특수코드를 문자로 변환


아래와 같이 HTML 특수코드가 문자열에 포함되어 있는 경우 해당 문자로 변환 가능함

<table>
<thead>
<tr><th style="text-align:center">Character</th><th>Entity Name</th><th>Entity Number</th><th>Description</th></tr>
</thead>
<tbody>
<tr><td style="text-align:center"><strong><code></code></strong></td><td></td><td>&amp;#32;</td><td>여백 (Space)</td></tr>
<tr><td style="text-align:center"><strong><code>!</code></strong></td><td></td><td>&amp;#33;</td><td>느낌표 (Exclamation mark)</td></tr>
<tr><td style="text-align:center"><strong><code>"</code></strong></td><td></td><td>&amp;#34;</td><td>큰따옴표 (Quotation mark)</td></tr>
<tr><td style="text-align:center"><strong><code>#</code></strong></td><td></td><td>&amp;#35;</td><td>샵 (Number sign)</td></tr>
<tr><td style="text-align:center"><strong><code>$</code></strong></td><td></td><td>&amp;#36;</td><td>달러 (Dollar sign)</td></tr>
<tr><td style="text-align:center"><strong><code>%</code></strong></td><td></td><td>&amp;#37;</td><td>퍼센트 (Percent sign)</td></tr>
<tr><td style="text-align:center"><strong>&amp;</strong></td><td><code>&amp;amp;</code></td><td>&amp;#38;</td><td>앤드 기호 (Ampersand)</td></tr>
<tr><td style="text-align:center"><strong><code>'</code></strong></td><td></td><td>&amp;#39;</td><td>아포스트로피 (Apostrophe)</td></tr>
<tr><td style="text-align:center"><strong><code>(</code></strong></td><td></td><td>&amp;#40;</td><td>소괄호/왼쪽 (Opening/Left Parenthesis)</td></tr>
<tr><td style="text-align:center"><strong><code>)</code></strong></td><td></td><td>&amp;#41;</td><td>소괄호/오른쪽 (Closing/Right Parenthesis)</td></tr>
<tr><td style="text-align:center"><strong><code>*</code></strong></td><td></td><td>&amp;#42;</td><td>별표 (Asterisk)</td></tr>
<tr><td style="text-align:center"><strong><code>+</code></strong></td><td></td><td>&amp;#43;</td><td>더하기 (Plus sign)</td></tr>
<tr><td style="text-align:center"><strong><code>,</code></strong></td><td></td><td>&amp;#44;</td><td>쉼표 (Comma)</td></tr>
<tr><td style="text-align:center"><strong><code>-</code></strong></td><td></td><td>&amp;#45;</td><td>하이픈 (Hyphen)</td></tr>
<tr><td style="text-align:center"><strong><code>.</code></strong></td><td></td><td>&amp;#46;</td><td>온점, 마침표 (Period)</td></tr>
<tr><td style="text-align:center"><strong><code>/</code></strong></td><td></td><td>&amp;#47;</td><td>슬래시 (Slash)</td></tr>
<tr><td style="text-align:center"><strong><code>0</code></strong> ~ <strong><code>9</code></strong></td><td></td><td>&amp;#48; ~ &amp;#57;</td><td>숫자 0 ~ 9 (Digit 0 - 9)</td></tr>
<tr><td style="text-align:center"><strong><code>:</code></strong></td><td></td><td>&amp;#58;</td><td>쌍점, 콜론 (Colon)</td></tr>
<tr><td style="text-align:center"><strong><code>;</code></strong></td><td></td><td>&amp;#59;</td><td>세미콜론 (Semicolon)</td></tr>
<tr><td style="text-align:center"><strong>&lt;</strong></td><td><code>&amp;lt;</code></td><td>&amp;#60;</td><td>보다 작은 (Less than)</td></tr>
<tr><td style="text-align:center"><strong><code>=</code></strong></td><td></td><td>&amp;#61;</td><td>등호, 같기표 (Equals sign)</td></tr>
<tr><td style="text-align:center"><strong>&gt;</strong></td><td><code>&amp;gt;</code></td><td>&amp;#62;</td><td>보다 큰 (Greater than)</td></tr>
<tr><td style="text-align:center"><strong><code>?</code></strong></td><td></td><td>&amp;#63;</td><td>물음표 (Question mark)</td></tr>
<tr><td style="text-align:center"><strong><code>@</code></strong></td><td></td><td>&amp;#64;</td><td>앳, 골뱅이 (At sign)</td></tr>
<tr><td style="text-align:center"><strong><code>A</code></strong> ~ <strong><code>Z</code></strong></td><td></td><td>&amp;#65; ~ &amp;#90;</td><td>대문자 A ~ Z (Uppercase A - Z)</td></tr>
<tr><td style="text-align:center"><strong><code>[</code></strong></td><td></td><td>&amp;#91;</td><td>대괄호/왼쪽 (Opening/Left square bracket)</td></tr>
<tr><td style="text-align:center"><strong></strong></td><td></td><td>&amp;#96;</td><td>역슬래시, 백슬래시 (Backslash)</td></tr>
<tr><td style="text-align:center"><strong><code>]</code></strong></td><td></td><td>&amp;#93;</td><td>대괄호/오른쪽 (Closing/Right square bracket)</td></tr>
<tr><td style="text-align:center"><strong><code>^</code></strong></td><td></td><td>&amp;#94;</td><td>지수 (Caret)</td></tr>
<tr><td style="text-align:center"><strong><code>_</code></strong></td><td></td><td>&amp;#95;</td><td>언더바 (Underscore)</td></tr>
<tr><td style="text-align:center"><strong>`</strong></td><td></td><td>&amp;#96;</td><td>억음부호(^^?) (Grave accent)</td></tr>
<tr><td style="text-align:center"><strong><code>a</code></strong> ~ <strong><code>z</code></strong></td><td></td><td>&amp;#97; ~ &amp;#122;</td><td>소문자 a ~ z (Lowercase a - z)</td></tr>
<tr><td style="text-align:center"><strong><code>{</code></strong></td><td></td><td>&amp;#123;</td><td>중괄호/왼쪽 (Opening/Left curly brace)</td></tr>
<tr><td style="text-align:center"><strong><code>|</code></strong></td><td></td><td>&amp;#124;</td><td>버티컬바, 파이프 (Vertical bar)</td></tr>
<tr><td style="text-align:center"><strong><code>}</code></strong></td><td></td><td>&amp;#125;</td><td>중괄호/오른쪽 (Closing/Right curly brace)</td></tr>
<tr><td style="text-align:center"><strong><code>~</code></strong></td><td></td><td>&amp;#126;</td><td>물결표 (Tilde)</td></tr>
<tr><td style="text-align:center"><strong><code></code></strong></td><td>&amp;nbsp;</td><td>&amp;#160;</td><td>여백 (Non-breaking space)</td></tr>
<tr><td style="text-align:center"><strong><code>¡</code></strong></td><td>&amp;iexcl;</td><td>&amp;#161;</td><td>거꾸로 느낌표 (Inverted exclamation mark)</td></tr>
<tr><td style="text-align:center"><strong><code>¢</code></strong></td><td>&amp;cent;</td><td>&amp;#162;</td><td>센트 (Cent)</td></tr>
<tr><td style="text-align:center"><strong><code>£</code></strong></td><td>&amp;pound;</td><td>&amp;#163;</td><td>파운드 (Pound)</td></tr>
<tr><td style="text-align:center"><strong><code>¤</code></strong></td><td>&amp;curren;</td><td>&amp;#164;</td><td>정의되지않은 커런시 표시 (Currency)</td></tr>
<tr><td style="text-align:center"><strong><code>¥</code></strong></td><td>&amp;yen;</td><td>&amp;#165;</td><td>엔 (Yen)</td></tr>
<tr><td style="text-align:center"><strong><code>¦</code></strong></td><td>&amp;brvbar;</td><td>&amp;#166;</td><td>파이프 (Broken vertical bar)</td></tr>
<tr><td style="text-align:center"><strong><code>§</code></strong></td><td>&amp;sect;</td><td>&amp;#167;</td><td>단락기호 (Section)</td></tr>
<tr><td style="text-align:center"><strong><code>©</code></strong></td><td>&amp;copy;</td><td>&amp;#169;</td><td>카피라이트 기호 (Copyright)</td></tr>
<tr><td style="text-align:center"><strong><code>®</code></strong></td><td>&amp;reg;</td><td>&amp;#174;</td><td>트레이드 마크 기호 (Registered trademark)</td></tr>
<tr><td style="text-align:center"><strong><code>°</code></strong></td><td>&amp;deg;</td><td>&amp;#176;</td><td>도 단위기호 (Degree)</td></tr>
<tr><td style="text-align:center"><strong><code>±</code></strong></td><td>&amp;plusmn;</td><td>&amp;#177;</td><td>플러스 or 마이너스 (Plus or minus)</td></tr>
<tr><td style="text-align:center"><strong><code>µ</code></strong></td><td>&amp;micro;</td><td>&amp;#181;</td><td>마이크로 단위기호 (Micro)</td></tr>
<tr><td style="text-align:center"><strong><code>¼</code></strong></td><td>&amp;frac14;</td><td>&amp;#188;</td><td>분수 1/4 (Fraction 1/4)</td></tr>
<tr><td style="text-align:center"><strong><code>½</code></strong></td><td>&amp;frac12;</td><td>&amp;#189;</td><td>분수 1/2 (Fraction 1/2)</td></tr>
<tr><td style="text-align:center"><strong><code>¾</code></strong></td><td>&amp;frac34;</td><td>&amp;#190;</td><td>분수 3/4 (Fraction 3/4)</td></tr>
<tr><td style="text-align:center"><strong><code>¿</code></strong></td><td>&amp;iquest;</td><td>&amp;#191;</td><td>거꾸로 물음표 (Inverted question mark)</td></tr>
<tr><td style="text-align:center"><strong><code>×</code></strong></td><td>&amp;times;</td><td>&amp;#215;</td><td>곱하기 부호 (Multiplication)</td></tr>
<tr><td style="text-align:center"><strong><code>÷</code></strong></td><td>&amp;divide;</td><td>&amp;#247;</td><td>나누기 부호 (Divide)</td></tr>
<tr><td style="text-align:center"><strong><code>‘</code></strong></td><td>&amp;lsquo;</td><td>&amp;#8216;</td><td>왼쪽 작은따옴표 (Left single quotation mark)</td></tr>
<tr><td style="text-align:center"><strong><code>’</code></strong></td><td>&amp;rsquo;</td><td>&amp;#8217;</td><td>오른쪽 작은따옴표 (Right single quotation mark)</td></tr>
<tr><td style="text-align:center"><strong><code>‚</code></strong></td><td>&amp;sbquo;</td><td>&amp;#8218;</td><td>쉼표 (Single low-9 quotation mark)</td></tr>
</tbody>
</table>


```python
import html
```


```python
text = "Science &amp; Nature"
print(text)
```




        'Science &amp; Nature'




```python
print(html.unescape(text))
```




        'Science & Nature'


