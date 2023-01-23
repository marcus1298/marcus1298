<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=6495ED&height=180&section=header&text=Marcus+Oliveira&fontSize=30&fontColor=F0FFFF&animation=twinkling&fontAlignY=35"/>

[![Typing SVG](https://readme-typing-svg.herokuapp.com/?color=6495ED&size=45&center=true&vCenter=true&width=1000&lines=Engenheiro+de+Computação;Apaixonado+por+tecnologia!;Welcome+to+my+profile,+enjoy+your+stay!)](https://git.io/typing-svg)

## ✨ Sobre mim
🎓 Computer Engineering - UFU
|| 👾 Computer Graphics - IFTM
|| ☁️ Experience with cloud projects (AWS)

💻 Data engineering, data lake
|| 💰 Banking

![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=marcus1298&show_icons=true&theme=transparent)


<div align="center>

<img width="49%" height="195px" src="https://github-readme-stats.vercel.app/api?username=marcus1298&show_icons=true&count_private=true&hide_border=true&title_color=00bfbf&icon_color=C0C0C0&text_color=C0C0C0&bg_color=0d1117" alt="Marcus Oliveira gitHub stats"/>
            
<img width="41%" height="195px" src="https://github-readme-stats.vercel.app/api/top-langs/?username=marcus1298&layout=compact&hide_border=true&title_color=C0C0C0&text_color=C0C0C0&bg_color=0d1117"/>


</div>

## 🚀 Skills 
<div style="display: inline_block"><br>
  <img align="center" alt="Python" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg">
  <img align="center" alt="Csharp" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/csharp/csharp-original.svg">

  <img align="center" alt="RCsharp" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original.svg">
  
  <img align="center" alt="Csharp" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/amazonwebservices/amazonwebservices-original-wordmark.svg">
  
</div>
  
## 📬 Redes Sociais   
  
<div> 



  <a href="https://www.youtube.com/channel/UC1CwDDyRTdpjyz43ShRgcnw" target="_blank"><img src="https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white" target="_blank"></a>
  <a href="https://www.instagram.com/marcus_oliveir.a/" target="_blank"><img src="https://img.shields.io/badge/-Instagram-%23E4405F?style=for-the-badge&logo=instagram&logoColor=white" target="_blank"></a>
  <a href = "mailto:marcusviniciusiftm@gmail.com"><img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>
  <a href="https://www.linkedin.com/in/marcus-oliveira-34bb74172/" target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a> 
  
</div>


name: generate animation

on:
  # run automatically every 12 hours
  schedule:
    - cron: "0 */12 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master
    
  

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v2
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
