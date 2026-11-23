---
layout: single
title: "The Gibbs Phenomenon of the Square Wave"
date: 2026-11-23
excerpt: "Why adding more sine waves never removes the overshoot at a jump, and exactly how big it is."
categories:
  - Fourier Analysis
tags:
  - Fourier series
  - Gibbs phenomenon
  - square wave
author_profile: true
read_time: true
toc: true
toc_label: "Contents"
toc_sticky: true
---

<script>
window.MathJax = {
  tex: { inlineMath: [['\\(', '\\)']], displayMath: [['\\[', '\\]']] },
  startup: {
    ready: function () {
      // Kramdown turns $$...$$ into <script type="math/tex">; convert to delimiters MathJax 3 reads.
      document.querySelectorAll('script[type^="math/tex"]').forEach(function (s) {
        var display = s.type.indexOf('mode=display') !== -1;
        var span = document.createElement(display ? 'div' : 'span');
        span.textContent = display ? '\\[' + s.text + '\\]' : '\\(' + s.text + '\\)';
        s.parentNode.replaceChild(span, s);
      });
      MathJax.startup.defaultReady();
    }
  }
};
</script>
<script async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.2/es5/tex-chtml.js"></script>

Take a function with a jump in it, write it as a sum of sines and cosines, and keep adding terms. Away from the jump the sums settle down nicely. At the jump they do something surprising: they overshoot, and the overshoot does not go away. This post builds the idea from the beginning, using the simplest example, the square wave, and ends with an exact computation of the overshoot.

## 1. Periodic functions

A function $$f$$ is **periodic with period $$2\pi$$** if $$f(x+2\pi)=f(x)$$ for every $$x$$. The basic examples are $$\sin(kx)$$ and $$\cos(kx)$$ for integers $$k\ge 1$$. Because of periodicity, it is enough to describe $$f$$ on one interval such as $$(-\pi,\pi)$$.

## 2. The square wave

Our test function is

$$
f(x)=\begin{cases}-1, & -\pi<x<0,\\ \;\;\,1, & 0<x<\pi,\end{cases}
\qquad f(x+2\pi)=f(x).
$$

It is smooth except at multiples of $$\pi$$, where it **jumps** by $$2$$. The value at the jump itself does not matter for what follows. Everything interesting happens near $$x=0$$.

## 3. Fourier series

The idea of Fourier analysis is to write a periodic function as a sum of sines and cosines:

$$
f(x)\sim \frac{a_0}{2}+\sum_{k=1}^{\infty}\bigl(a_k\cos kx+b_k\sin kx\bigr),
$$

where the **Fourier coefficients** are

$$
a_k=\frac{1}{\pi}\int_{-\pi}^{\pi}f(x)\cos kx\,dx,\qquad
b_k=\frac{1}{\pi}\int_{-\pi}^{\pi}f(x)\sin kx\,dx .
$$

These formulas come from the orthogonality of the trigonometric functions on $$[-\pi,\pi]$$. For example, $$\int_{-\pi}^{\pi}\sin jx\,\sin kx\,dx=0$$ for $$j\neq k$$ and equals $$\pi$$ when $$j=k\ge 1$$. Multiplying the series by $$\sin kx$$ and integrating isolates $$b_k$$.

### Coefficients of the square wave

The square wave is an odd function, so $$f(x)\cos kx$$ is odd and every $$a_k=0$$. For the sine coefficients, since $$f(x)\sin kx$$ is even,

$$
b_k=\frac{2}{\pi}\int_0^{\pi}\sin kx\,dx=\frac{2}{\pi}\cdot\frac{1-\cos k\pi}{k}.
$$

Since $$\cos k\pi=(-1)^k$$, we get $$b_k=\dfrac{4}{\pi k}$$ when $$k$$ is odd and $$b_k=0$$ when $$k$$ is even. Therefore

$$
f(x)\sim\frac{4}{\pi}\left(\sin x+\frac{\sin 3x}{3}+\frac{\sin 5x}{5}+\cdots\right)
=\frac{4}{\pi}\sum_{j=1}^{\infty}\frac{\sin\bigl((2j-1)x\bigr)}{2j-1}.
$$

## 4. Partial sums

Let $$S_m$$ be the partial sum with the first $$m$$ nonzero terms:

$$
S_m(x)=\frac{4}{\pi}\sum_{j=1}^{m}\frac{\sin\bigl((2j-1)x\bigr)}{2j-1}.
$$

At every point where $$f$$ is continuous, $$S_m(x)\to f(x)$$ as $$m\to\infty$$. The question is what $$S_m$$ looks like near the jump. Try it yourself in the interactive figure below. Drag the slider, turn on "show first harmonics", and then compare the zoomed plot near $$x=0$$.

{% raw %}
<div class="gibbs-demo" id="gibbs-demo">
<style>
.gibbs-demo{--gbg:#ffffff;--gink:#14213d;--gmute:#5b6783;--gline:#d5dbe7;--gtarget:#14213d;--gsum:#0b7a75;--gmark:#c27a00;background:var(--gbg);color:var(--gink);border:1px solid var(--gline);border-radius:6px;padding:1rem;margin:1.5rem 0;font:500 14px/1.4 system-ui,-apple-system,"Segoe UI",sans-serif}
@media (prefers-color-scheme:dark){.gibbs-demo{--gbg:#172036;--gink:#e6ebf5;--gmute:#9aa7c2;--gline:#2b3753;--gtarget:#e6ebf5;--gsum:#4fd1c5;--gmark:#f2b134}}
.gibbs-demo *{box-sizing:border-box}
.gibbs-demo .gd-controls{display:flex;flex-wrap:wrap;gap:.7rem 1.4rem;align-items:center;margin-bottom:.7rem}
.gibbs-demo label{display:flex;align-items:center;gap:.5rem;margin:0}
.gibbs-demo input[type=range]{width:min(15rem,55vw)}
.gibbs-demo select{font:inherit;padding:.2rem .4rem;background:var(--gbg);color:var(--gink);border:1px solid var(--gline);border-radius:4px}
.gibbs-demo canvas{display:block;width:100%;height:auto;aspect-ratio:2/1;margin:0}
.gibbs-demo .gd-key,.gibbs-demo .gd-read{display:flex;flex-wrap:wrap;gap:.3rem 1.4rem;color:var(--gmute);margin-top:.5rem}
.gibbs-demo .gd-key i{display:inline-block;width:1.4rem;border-top:3px solid;vertical-align:middle;margin-right:.4rem}
.gibbs-demo b{color:var(--gink)}
.gibbs-demo h4{margin:1.1rem 0 .3rem;font-size:1rem;color:var(--gink)}
.gibbs-demo table{width:100%;border-collapse:collapse;margin:.4rem 0 0;display:table;font-size:14px}
.gibbs-demo th,.gibbs-demo td{text-align:right;padding:.3rem .5rem;border-bottom:1px solid var(--gline);color:var(--gink);background:none}
.gibbs-demo th:first-child,.gibbs-demo td:first-child{text-align:left}
</style>
<div class="gd-controls">
<label>Terms m <input id="gd-m" type="range" min="1" max="60" value="3" aria-label="Number of terms"> <span id="gd-mv">3</span></label>
<label>Method <select id="gd-meth"><option value="f">Fourier partial sum</option><option value="l">Lanczos sigma factors</option><option value="j">Fejér (Cesàro) mean</option></select></label>
<label><input id="gd-harm" type="checkbox"> show first harmonics</label>
</div>
<canvas id="gd-c1" width="920" height="460" role="img" aria-label="Square wave and its Fourier partial sum"></canvas>
<div class="gd-key"><span><i style="color:var(--gtarget)"></i>square wave</span><span><i style="color:var(--gsum)"></i>approximation</span></div>
<h4>Zoom on the jump at x = 0</h4>
<canvas id="gd-c2" width="920" height="460" role="img" aria-label="Zoomed view of the overshoot near the jump at zero"></canvas>
<div class="gd-key"><span><i style="color:var(--gsum)"></i>approximation</span><span><i style="color:var(--gmark);border-top-style:dashed"></i>limit height 1.1790</span><span><i style="color:var(--gtarget)"></i>true value 1</span></div>
<div class="gd-read"><span>Highest harmonic: <b id="gd-hh"></b></span><span>Peak height: <b id="gd-pk"></b></span><span>Overshoot / jump: <b id="gd-os"></b></span><span>Peak at x = <b id="gd-px"></b></span></div>
<h4>Overshoot of the Fourier partial sums</h4>
<table id="gd-tb"><thead><tr><th>Terms m</th><th>Peak of S_m</th><th>Overshoot / jump</th></tr></thead><tbody></tbody></table>
<script>
(function(){
var PI=Math.PI, root=document.getElementById('gibbs-demo');
function $(id){return document.getElementById(id)}
function css(n){return getComputedStyle(root).getPropertyValue(n).trim();}
function coef(k,M,meth){ if(meth==='l'){var t=PI*k/(M+1);return Math.sin(t)/t;} if(meth==='j'){return 1-k/(M+1);} return 1; }
function S(x,m,meth){ var M=2*m-1,s=0; for(var j=1;j<=m;j++){var k=2*j-1; s+=coef(k,M,meth)*Math.sin(k*x)/k;} return 4/PI*s; }
function setup(c){var r=window.devicePixelRatio||1,w=c.clientWidth||600;c.width=w*r;c.height=w*r/2;var g=c.getContext('2d');g.setTransform(r,0,0,r,0,0);return {g:g,w:w,h:w/2};}
function frame(o,x0,x1,y0,y1,xt,yt,fmt){
  var g=o.g,pad={l:44,r:12,t:12,b:26};
  var X=function(x){return pad.l+(x-x0)/(x1-x0)*(o.w-pad.l-pad.r)};
  var Y=function(y){return o.h-pad.b-(y-y0)/(y1-y0)*(o.h-pad.t-pad.b)};
  g.clearRect(0,0,o.w,o.h);g.font='12px system-ui,sans-serif';g.fillStyle=css('--gmute');g.strokeStyle=css('--gline');g.lineWidth=1;
  g.textAlign='right';g.textBaseline='middle';
  yt.forEach(function(v){g.beginPath();g.moveTo(pad.l,Y(v));g.lineTo(o.w-pad.r,Y(v));g.stroke();g.fillText(String(+v.toFixed(3)),pad.l-6,Y(v));});
  g.textAlign='center';g.textBaseline='top';
  xt.forEach(function(v){g.beginPath();g.moveTo(X(v),pad.t);g.lineTo(X(v),o.h-pad.b);g.stroke();g.fillText(fmt(v),X(v),o.h-pad.b+6);});
  g.save();g.beginPath();g.rect(pad.l,pad.t,o.w-pad.l-pad.r,o.h-pad.t-pad.b);g.clip();
  return {X:X,Y:Y,end:function(){g.restore();}};
}
function line(g,A,f,x0,x1,col,w,n,dash){g.strokeStyle=col;g.lineWidth=w;g.setLineDash(dash||[]);g.beginPath();for(var i=0;i<=n;i++){var x=x0+(x1-x0)*i/n,y=f(x);if(i){g.lineTo(A.X(x),A.Y(y));}else{g.moveTo(A.X(x),A.Y(y));}}g.stroke();g.setLineDash([]);}
function peak(m,meth){var best=-9,bx=0,hi=PI/m;for(var i=1;i<=3000;i++){var x=hi*i/3000,v=S(x,m,meth);if(v>best){best=v;bx=x;}}return {v:best,x:bx};}
function draw(){
  var m=+$('gd-m').value,meth=$('gd-meth').value;$('gd-mv').textContent=m;
  var o=setup($('gd-c1')),g=o.g;
  var A=frame(o,-PI,PI,-1.4,1.4,[-PI,-PI/2,0,PI/2,PI],[-1,0,1],function(v){var r=Math.round(v/PI*2);return r===0?'0':({'-2':'-π','-1':'-π/2','1':'π/2','2':'π'})[r];});
  g.strokeStyle=css('--gtarget');g.lineWidth=2.5;
  [[-PI,0,-1],[0,PI,1]].forEach(function(s){g.beginPath();g.moveTo(A.X(s[0]),A.Y(s[2]));g.lineTo(A.X(s[1]),A.Y(s[2]));g.stroke();});
  g.beginPath();g.moveTo(A.X(0),A.Y(-1));g.lineTo(A.X(0),A.Y(1));g.setLineDash([4,4]);g.globalAlpha=0.4;g.stroke();g.setLineDash([]);g.globalAlpha=1;
  if($('gd-harm').checked){for(var j=1;j<=Math.min(m,6);j++){(function(k){g.globalAlpha=0.35;line(g,A,function(x){return 4/PI*Math.sin(k*x)/k},-PI,PI,css('--gmute'),1.2,400);g.globalAlpha=1;})(2*j-1);}}
  line(g,A,function(x){return S(x,m,meth)},-PI,PI,css('--gsum'),2.2,900);A.end();
  var w=Math.max(0.12,Math.min(0.9,4/m+0.25)),o2=setup($('gd-c2')),g2=o2.g,lim=1.178979744;
  var A2=frame(o2,-w,w,-1.3,1.3,[-w,-w/2,0,w/2,w],[-1,-0.5,0,0.5,1,1.179],function(v){return v.toFixed(2)});
  g2.strokeStyle=css('--gtarget');g2.lineWidth=2;g2.beginPath();g2.moveTo(A2.X(-w),A2.Y(-1));g2.lineTo(A2.X(0),A2.Y(-1));g2.moveTo(A2.X(0),A2.Y(1));g2.lineTo(A2.X(w),A2.Y(1));g2.stroke();
  line(g2,A2,function(){return lim},-w,w,css('--gmark'),1.5,2,[6,5]);
  line(g2,A2,function(x){return S(x,m,meth)},-w,w,css('--gsum'),2.2,900);
  var p=peak(m,meth);g2.fillStyle=css('--gmark');g2.beginPath();g2.arc(A2.X(p.x),A2.Y(p.v),4,0,2*PI);g2.fill();A2.end();
  $('gd-hh').textContent=2*m-1;$('gd-pk').textContent=p.v.toFixed(4);$('gd-os').textContent=(Math.max(0,(p.v-1)/2)*100).toFixed(2)+'%';$('gd-px').textContent=p.x.toFixed(4);
}
var tb=document.querySelector('#gd-tb tbody');
[1,2,3,5,10,25,50,100,500].forEach(function(m){var p=peak(m,'f');var r=document.createElement('tr');r.innerHTML='<td>'+m+'</td><td>'+p.v.toFixed(4)+'</td><td>'+((p.v-1)/2*100).toFixed(2)+'%</td>';tb.appendChild(r);});
['gd-m','gd-meth','gd-harm'].forEach(function(i){$(i).addEventListener('input',draw);});
window.addEventListener('resize',draw);
if(window.matchMedia){window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change',draw);}
draw();
})();
</script>
</div>
{% endraw %}


What you should notice:

- The approximation gets steeper at the jump as $$m$$ grows.
- A bump of fixed height remains next to the jump. It moves closer to $$x=0$$ and gets narrower, but it does not shrink.

## 5. Where the overshoot comes from

To find the height of the bump, locate the maximum of $$S_m$$ near $$0$$. Differentiating and using the identity $$\sum_{j=1}^{m}\cos\bigl((2j-1)x\bigr)=\dfrac{\sin 2mx}{2\sin x}$$ gives

$$
S_m'(x)=\frac{4}{\pi}\sum_{j=1}^{m}\cos\bigl((2j-1)x\bigr)=\frac{2}{\pi}\,\frac{\sin 2mx}{\sin x}.
$$

The first positive zero is at $$x_m=\dfrac{\pi}{2m}$$, and $$S_m$$ increases on $$(0,x_m)$$, so this is the first peak. Its height is

$$
S_m(x_m)=\frac{2}{\pi}\int_0^{\pi/2m}\frac{\sin 2mt}{\sin t}\,dt .
$$

Substitute $$u=2mt$$. For large $$m$$ the variable $$t=u/2m$$ is small, so $$\sin t\approx t$$ and the integral becomes

$$
S_m(x_m)\;\longrightarrow\;\frac{2}{\pi}\int_0^{\pi}\frac{\sin u}{u}\,du=\frac{2}{\pi}\,\mathrm{Si}(\pi)\approx 1.17898 .
$$

The true value just to the right of the jump is $$1$$, so the partial sums overshoot by about $$0.17898$$. The jump has size $$2$$, so the overshoot is

$$
\frac{\tfrac{2}{\pi}\mathrm{Si}(\pi)-1}{2}\approx 0.0895,
$$

about **9% of the jump**, no matter how many terms we take. This is the **Gibbs phenomenon**. The sums converge to $$f$$ at each fixed point away from the jump, but the convergence is not uniform near the jump.

A quick numerical check, which you can run yourself:

```python
import numpy as np

def S(x, m):
    k = 2 * np.arange(1, m + 1) - 1
    return 4 / np.pi * np.sum(np.sin(np.outer(x, k)) / k, axis=1)

x = np.linspace(1e-6, np.pi / 2, 200_000)
for m in [1, 5, 25, 100, 500]:
    peak = S(x, m).max()
    print(m, round(peak, 4), round((peak - 1) / 2, 4))
```

The peak climbs toward $$1.1790$$ and the overshoot relative to the jump toward $$0.0895$$.

## 6. Can the overshoot be removed?

Yes, by changing how we add up the terms. Both of the following multiply the $$k$$-th term by a damping factor $$\sigma_k$$, where $$M=2m-1$$ is the highest harmonic used:

$$
\text{Lanczos: }\ \sigma_k=\frac{\sin\bigl(\pi k/(M+1)\bigr)}{\pi k/(M+1)},
\qquad
\text{Fejér: }\ \sigma_k=1-\frac{k}{M+1}.
$$

Use the "Method" menu in the figure above to compare them with the plain partial sum. The Fejér means are averages of partial sums and have no overshoot at all, because the Fejér kernel is positive. The price is a blurrier jump. This tension between a sharp edge and ringing is the starting point for more refined tools, such as concentration factors for edge detection and prolate spheroidal wave functions, which I will come back to in later posts.

## Exercises

1. Compute the Fourier series of the sawtooth $$g(x)=x$$ on $$(-\pi,\pi)$$. Does the Gibbs phenomenon occur at $$x=\pm\pi$$? How large is the overshoot relative to the jump?
2. Plug $$x=\pi/2$$ into the Fourier series of the square wave and derive the Leibniz formula $$1-\tfrac13+\tfrac15-\cdots=\tfrac{\pi}{4}$$.
3. Show that $$\dfrac{2}{\pi}\mathrm{Si}(\pi)=\dfrac{2}{\pi}\displaystyle\int_0^{\pi}\dfrac{\sin u}{u}\,du$$ can be computed from the Taylor series of $$\sin u/u$$, and use it to confirm $$1.17898$$.

## References

- H. S. Carslaw, *Introduction to the Theory of Fourier's Series and Integrals*, 3rd ed., Dover, 1952. Includes a classical treatment of the Gibbs phenomenon.
- E. M. Stein and R. Shakarchi, *Fourier Analysis: An Introduction*, Princeton University Press, 2003.
- G. B. Folland, *Fourier Analysis and Its Applications*, AMS, 2009.
- A. Zygmund, *Trigonometric Series*, Cambridge University Press, 2002.
- E. Hewitt and R. E. Hewitt, "The Gibbs–Wilbraham phenomenon: an episode in Fourier analysis," *Archive for History of Exact Sciences* 21 (1979), 129–160.
