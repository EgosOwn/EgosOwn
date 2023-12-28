    #!/bin/bash

# ![Kevin Froman](kevin.svg)

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

My profile readme is a self-updating bash-markdown polyglot using the [literate programming](https://en.wikipedia.org/wiki/Literate_programming) tool [srcweave](https://github.com/justinmeiners/srcweave). In plain english, that means you can run this document as a bash script.



# Information and statistics

Readme build time Thu Dec 28 02:49:54 AM UTC 2023


git.voidnet.tech status: Online

# ![Commit stats](https://github-readme-stats.vercel.app/api?username=egosown&hide=stars,prs,issues,contribs&show_icons=true&hide_rank=true&hide_title=true)



--- /updatereadme.sh

    @{setbuildtime}
    @{loadGitStatus}

---

It's handy to know when the current build was done. This portion sets the build time in the statistics section.

--- setbuildtime

    # Set the build time
    buildTime=$(date -u)

    sed -i "s/^Readme build time.*/Readme build time $buildTime/" README.md

---


My gitea instance is where I do much of my programming: [git.voidnet.tech](https://git.voidnet.tech)

Below we check if my site is online, and we update the entry in the statistics section.

--- loadGitStatus

    gitOnline=$(curl --max-time 6 -I https://git.voidnet.tech/explore/repos)
    if [[ $gitOnline == "HTTP/2 200"* ]]; then
        echo "Gitea online"
        sed -i "0,/git.voidnet.tech status Offline/{s/^git.voidnet.tech status Offline/git.voidnet.tech status Online/}" README.md
    else
        echo "Node offline"
        sed -i "0,/git.voidnet.tech status Offline/{s/^git.voidnet.tech status Online/git.voidnet.tech status Offline/}" README.md
    fi

---
