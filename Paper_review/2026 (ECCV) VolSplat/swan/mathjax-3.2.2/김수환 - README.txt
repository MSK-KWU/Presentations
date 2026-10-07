참고자료: 
https://docs.mathjax.org/en/latest/web/hosting.html
https://community.rstudio.com/t/what-is-the-canonical-way-of-adding-javascript-to-a-xaringan-presentation/40348/2

1. node.js (npm) 설치
https://nodejs.org/en

2. mathjax 설치
$ npm install mathjax

3. mathjax가 어디에 설치됐는지 찾기
$ npm list mathjax

4. 필요한 곳에 mathjax 폴더 복사
C:\Users\user  -> ???

5. local mathjax와 연결
<script src="path-to-MathJax/tex-chtml.js" id="MathJax-script" async></script>

6. xaringan에서 불러오기
output:  
  xaringan::moon_reader:
    includes:
      in_header:
        - 'mathjax_linked.html'