---
title: 命名空間 (Namespace)
date: 2019-05-17
cover: /images/C++-Tutorial/C++-Tutorial-banner.jpg
thumbnail: /images/C++-Tutorial/C++-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C++
---

命名空間 教學與筆記。

<!-- more -->

# 說明

當程式越龐大，可能會發生同名類別的問題。這時可使用命名空間來解決。

## 命名空間 範例

```cpp
#include <iostream>
#include <string>
using namespace std;

namespace ASUS {
    class notebook {
    };
}

namespace Acer {
    class notebook {
    };
}

int main() {
    ASUS::notebook A;
    Acer::notebook B;

    return 0;
}
```

其中`::`為範圍運算子。

## 子命名空間 範例

另外還可再延伸至 子命名空間。

```cpp
#include <iostream>
#include <string>
using namespace std;

namespace ASUS {
    namespace Taiwan {
        class notebook {
        };
    }
    
    namespace Japan {
        class notebook {
        };
    }
}

int main() {
    ASUS::Taiwan::notebook A;
    ASUS::Japan::notebook B;

    return 0;
}
```