    #!/bin/bash

# ![Kevin Froman](kevin.svg)
### Readme build time:


    # Perform literate tangling then run all the scripts
    srcweave --tangle . README.md
    for f in *.sh; do
        chmod +x "$f"
        bash "$f"
    done
    rm *.sh
    git add README.md
    git commit -m "Automatic update"
    git push origin master
    # Past the exit we can have invalid bash code
    exit 0


I am a freelance software engineer and open source full-stack developer most proficient in Python, Go, C#, and ES6. I have particular interest in [PETs](https://en.wikipedia.org/wiki/Privacy-enhancing_technologies).

My profile readme is a self-updating bash-markdown polyglot using the [literate programming](https://en.wikipedia.org/wiki/Literate_programming) tool [srcweave](https://github.com/justinmeiners/srcweave).

---
# Information and statistics

* Monero Node: Online
# ![Commit stats](https://github-readme-stats.vercel.app/api?username=egosown&hide=stars,prs,issues,contribs&show_icons=true&hide_rank=true&hide_title=true)
---

I run a [Monero](https://getmonero.org/) node with open RPC and TLS for anyone to use. I believe Monero is an imperfect solution for 'electronic cash', but it is the best that is available today.

Below we check if my node is online, and we update the entry in the statistics section.




--- /updatereadme.sh


---

--- /setbuildtime.sh

    # Set the build time
    buildTime=$(date)
    sed -i "0,/### Readme build time:/{s/### Readme build time:.*/### Readme build time: $buildTime/}" README.md
---
