---
title: gnu cflow 教學 (gnu cflow tutorial)
date: 2022-05-20
cover:
thumbnail:
toc: true
categories: Learning-Note-學習筆記
tags:
    - Linux
    - cflow
---

gnu cflow 教學與筆記。

<!-- more -->

## Get started
[Official manual webpage](https://www.gnu.org/software/cflow/manual/html_node/index.html#Top)

## Download source code
[Official download webpage](https://ftp.gnu.org/gnu/cflow/)

```bash
wget https://ftp.gnu.org/gnu/cflow/cflow-latest.tar.gz
tar -xvf cflow-latest.tar.gz
```

## Build source code
解壓縮後裡面有 INSTALL 文字檔案說明如何 build

```bash
cd <cflow folder>
./configure
make
sudo make install
```

## 使用方式
如果需要畫圖功能，還需要安裝 `graphviz`
```bash
sudo apt install graphviz
```

* [官網範例](https://www.gnu.org/software/cflow/manual/html_node/Quick-Start.html#Quick-Start)

```c
/* whoami.c - a simple implementation of whoami utility */
#include <pwd.h>
#include <sys/types.h>
#include <stdio.h>
#include <stdlib.h>

int who_am_i(void) {
	struct passwd *pw;
	char *user = NULL;

	pw = getpwuid(geteuid());
	if(pw)
		user = pw->pw_name;
	else if((user = getenv("USER")) == NULL) {
		fprintf(stderr, "I don't know!\n");
		return 1;
	}
	printf("%s\n", user);
	return 0;
}

int main(int argc, char **argv) {
	if (argc > 1) {
		fprintf(stderr, "usage: whoami\n");
		return 1;
	}
	return who_am_i();
}
```

* 產生 pdf 檔
```bash
cflow -f dot whoami.c | dot -Tpdf -o ~/Desktop/cflow_example.pdf
```

* 結果圖
![cflow example](/images/gnu-cflow/gnu_cflow_example.jpg)