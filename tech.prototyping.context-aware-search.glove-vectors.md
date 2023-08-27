---
id: 6s1yhbp39gc6fzym7l5gtqd
title: Glove Vectors
desc: ''
updated: 1679790499699
created: 1679790499699
---

Wasn't digging into the code much was just trying to see if I can get #chatgpt4 to write some prototype python, for it. To try it out further would need to try using glove vectors in java or kotlin.

<details>
<summary>Example of code being able to use glove vectors to give similar words</summary>

To reproduce: './install.sh && python ./hello.py' (from commit:fc486bd) in ${GT_SANDBOX_REPO}/glove-vectors-python

## Command to reproduce:
```bash
gt.sandbox.checkout.commit fc486bd \
&& cd "${GT_SANDBOX_REPO}/glove-vectors-python" \
&& cmd.run.announce "./install.sh && python ./hello.py"
```

## Recorded output of command:
```
Requirement already satisfied: numpy in /usr/local/lib/python3.11/site-packages (1.24.2)
Requirement already satisfied: scipy in /usr/local/lib/python3.11/site-packages (1.10.1)
Requirement already satisfied: numpy<1.27.0,>=1.19.5 in /usr/local/lib/python3.11/site-packages (from scipy) (1.24.2)
Requirement already satisfied: matplotlib in /usr/local/lib/python3.11/site-packages (3.7.1)
Requirement already satisfied: contourpy>=1.0.1 in /usr/local/lib/python3.11/site-packages (from matplotlib) (1.0.7)
Requirement already satisfied: cycler>=0.10 in /usr/local/lib/python3.11/site-packages (from matplotlib) (0.11.0)
Requirement already satisfied: fonttools>=4.22.0 in /usr/local/lib/python3.11/site-packages (from matplotlib) (4.39.2)
Requirement already satisfied: kiwisolver>=1.0.1 in /usr/local/lib/python3.11/site-packages (from matplotlib) (1.4.4)
Requirement already satisfied: numpy>=1.20 in /usr/local/lib/python3.11/site-packages (from matplotlib) (1.24.2)
Requirement already satisfied: packaging>=20.0 in /usr/local/lib/python3.11/site-packages (from matplotlib) (23.0)
Requirement already satisfied: pillow>=6.2.0 in /usr/local/lib/python3.11/site-packages (from matplotlib) (9.4.0)
Requirement already satisfied: pyparsing>=2.3.1 in /usr/local/lib/python3.11/site-packages (from matplotlib) (3.0.9)
Requirement already satisfied: python-dateutil>=2.7 in /usr/local/lib/python3.11/site-packages (from matplotlib) (2.8.2)
Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.11/site-packages (from python-dateutil>=2.7->matplotlib) (1.16.0)
Requirement already satisfied: scikit-learn in /usr/local/lib/python2.7/site-packages (0.20.4)
Requirement already satisfied: scipy>=0.13.3 in /usr/local/lib/python2.7/site-packages (from scikit-learn) (1.2.3)
Requirement already satisfied: numpy>=1.8.2 in /usr/local/lib/python2.7/site-packages (from scikit-learn) (1.16.6)
Requirement already satisfied: sklearn in /usr/local/lib/python3.11/site-packages (0.0.post1)
done with installation
['prince', 'queen', 'uncle', 'ii', 'grandson']
['fingernails', 'toenails', 'stringy', 'peeling', 'shove']
```


</details>


<details>
<summary>Code that wasn't matching the expected file, but was able to get some context aware match.</summary>

To reproduce: './install.sh && python ./use-glove-vector-to-try-to-find-context-based-match.py' (from commit:25305f8) in ${GT_SANDBOX_REPO}/glove-vectors-python

## Command to reproduce:
```bash
gt.sandbox.checkout.commit 25305f8 \
&& cd "${GT_SANDBOX_REPO}/glove-vectors-python" \
&& cmd.run.announce "./install.sh && python ./use-glove-vector-to-try-to-find-context-based-match.py"
```

## Recorded output of command:
```
Requirement already satisfied: numpy in /usr/local/lib/python3.11/site-packages (1.24.2)
Requirement already satisfied: scipy in /usr/local/lib/python3.11/site-packages (1.10.1)
Requirement already satisfied: numpy<1.27.0,>=1.19.5 in /usr/local/lib/python3.11/site-packages (from scipy) (1.24.2)
Requirement already satisfied: matplotlib in /usr/local/lib/python3.11/site-packages (3.7.1)
Requirement already satisfied: contourpy>=1.0.1 in /usr/local/lib/python3.11/site-packages (from matplotlib) (1.0.7)
Requirement already satisfied: cycler>=0.10 in /usr/local/lib/python3.11/site-packages (from matplotlib) (0.11.0)
Requirement already satisfied: fonttools>=4.22.0 in /usr/local/lib/python3.11/site-packages (from matplotlib) (4.39.2)
Requirement already satisfied: kiwisolver>=1.0.1 in /usr/local/lib/python3.11/site-packages (from matplotlib) (1.4.4)
Requirement already satisfied: numpy>=1.20 in /usr/local/lib/python3.11/site-packages (from matplotlib) (1.24.2)
Requirement already satisfied: packaging>=20.0 in /usr/local/lib/python3.11/site-packages (from matplotlib) (23.0)
Requirement already satisfied: pillow>=6.2.0 in /usr/local/lib/python3.11/site-packages (from matplotlib) (9.4.0)
Requirement already satisfied: pyparsing>=2.3.1 in /usr/local/lib/python3.11/site-packages (from matplotlib) (3.0.9)
Requirement already satisfied: python-dateutil>=2.7 in /usr/local/lib/python3.11/site-packages (from matplotlib) (2.8.2)
Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.11/site-packages (from python-dateutil>=2.7->matplotlib) (1.16.0)
Requirement already satisfied: scikit-learn in /usr/local/lib/python2.7/site-packages (0.20.4)
Requirement already satisfied: scipy>=0.13.3 in /usr/local/lib/python2.7/site-packages (from scikit-learn) (1.2.3)
Requirement already satisfied: numpy>=1.8.2 in /usr/local/lib/python2.7/site-packages (from scikit-learn) (1.16.6)
Requirement already satisfied: sklearn in /usr/local/lib/python3.11/site-packages (0.0.post1)
done with installation
sc.work.principles.eat-your-own-dog-food.md
```

</details>
