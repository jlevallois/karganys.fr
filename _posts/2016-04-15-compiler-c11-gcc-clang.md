---
ID: 1195
post_title: Compiler en C++11 avec GCC ou Clang
author: Jérémy Levallois
post_date: 2016-04-15 15:00:27
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/programmation/c-cpp/compiler-c11-gcc-clang/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";s:4:"1197";s:11:"_thumb_type";s:5:"thumb";}'
layout_key:
  - ""
post_slider_check_key:
  - "0"
---
## Problème

Prenons par exemple ce code utilisant des fonctionnalités définis dans la norme C++11 :

```c
// test.cpp
#include <vector>
#include <string>

int main(int argc, char** argv)
{
  std::vector<std::string> v = { "a", "b", "c" };

  return 0;
}
```

Si vous voulez compiler ce code source, la ligne suivante ne fonctionne pas :

```sh
g++ test.cpp -o test
```
ou avec Clang :

```sh
clang++ test.cpp -o test
```

et vous obtiendrez :

```sh
test.cpp: In function ‘int main(int, char**)’:
test.cpp:6:48: error: in C++98 ‘v’ must be initialized by constructor, not by ‘{...}’
   std::vector<std::string> v = { "a", "b", "c" };
                                                ^
test.cpp:6:48: error: could not convert ‘{"a", "b", "c"}’ from ‘<brace-enclosed initializer list>’ to ‘std::vector<std::basic_string<char> >’
```

ou

```sh
test.cpp:6:28: error: non-aggregate type 'std::vector<std::string>' cannot be initialized with an initializer list
  std::vector<std::string> v = { "a", "b", "c" };
                           ^   ~~~~~~~~~~~~~~~~~
1 error generated.
```

## Résolution

Il faut rajouter le flag `-std=c++11` à la compilation pour définir que le code utilise des fonctionnalités de C++11. Ainsi :

```sh
g++ -std=c++11 test.cpp -o test
```
ou

```sh
clang++ -std=c++11 test.cpp -o test
```
compileront votre fichier.