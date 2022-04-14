## The framework of DFuzzer

The quality of seed queue may highly influence the fuzzing result. Intuitively, a high diversity in seed queues can help fuzzers detect different kinds of faults; in other words, a seed queue without a high diversity may cause the omission of some critical faults and thus affect the fault-detection effectiveness of fuzzing.

Motivated by the impact of the diverse seed queues on fuzzing for DL systems, we propose a diversity-driven seed queue construction approach, namely _DFuzzer_. DFuzzer attempts to distribute the seeds as “far away” from one another as possible. Based on the idea of “even spreading”, DFuzzer constructs seed queue by incrementally updating the “best” seeds chosen from the test pool. In addition, we propose two difference measurement metrics _IBDM_ and _FBDM_ based on the information theory and deep features, respectively, to quantify the difference between the seeds in the ongoing seed queue and those in the test pool. Accordingly, two algorithms, namely _DFuzzer-IB_ and _DFuzzer-FB_, are developed to implement DFuzzer based on IBDM and FBDM, respectively.

The framework of the proposed diversity-driven seed queue construction approach (DFuzzer) is illustrated below.
![image](src)

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/DFuzzer/DFuzzer/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
