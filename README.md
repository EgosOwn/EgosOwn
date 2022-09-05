#!/bin/bash

# Kevin Froman 🧑‍💻
# ![Commit stats](https://github-readme-stats.vercel.app/api?username=egosown&hide=stars,prs,issues,contribs&show_icons=true&hide_rank=true&hide_title=true)


    # Extract the source scripts
    srcweave --tangle . README.md
    chmod +x ./xmr-node-status.sh
    ./xmr-node-status.sh
    exit 0


I am a freelance software engineer and open source full-stack developer most proficient in Python, Go, C#, and ES6. I have particular interest in [PETs](https://en.wikipedia.org/wiki/Privacy-enhancing_technologies).

My profile readme is self-updating using the [literate programming](https://en.wikipedia.org/wiki/Literate_programming) tool [srcweave](https://github.com/justinmeiners/srcweave) and is a bash-markdown polyglot.

Information and statistics, fetched by the code snippets below:

* Monero Node Online

I run a [Monero](https://getmonero.org/) node with open RPC and TLS for anyone to use. I believe Monero is an imperfect solution for 'electronic cash', but it is the best that is available today.

--- /xmr-node-status.sh

    nodeOnline=$(curl --max-time 5 -I https://xmr.voidnet.tech/json_rpc)
    if [[ $nodeOnline == "HTTP/2 200"* ]]; then
        echo "Node online"
        sed -i "0,/Monero Node Online/{s/Monero Node Offline/Monero Node Online/}" README.md
    else
        echo "Node offline"
        sed -i "0,/Monero Node Online/{s/Monero Node Online/Monero Node Offline/}" README.md
    fi

---
