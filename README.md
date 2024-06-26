## Laboratory work I

Данная лабораторная работа посвещена изучению утилит для разработки проектов

## Tasks

- [ ] 1. Ознакомиться со ссылками учебного материала
- [ ] 2. Выполнить инструкцию учебного материала
- [ ] 3. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```bash
$ export GITHUB_USERNAME=<имя_пользователя>
$ export GIST_TOKEN=<сохраненный_токен>
$ alias edit=<nano|vi|vim|subl>
```

```sh
$ mkdir -p ${GITHUB_USERNAME}/workspace
$ cd ${GITHUB_USERNAME}/workspace
$ pwd
$ cd ..
$ pwd
```

```sh
$ mkdir -p workspace/tasks/
$ mkdir -p workspace/projects/
$ mkdir -p workspace/reports/
$ cd workspace
```

```sh
# Debian
$ wget https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
$ tar -xf node-v6.11.5-linux-x64.tar.xz
$ rm -rf node-v6.11.5-linux-x64.tar.xz
$ mv node-v6.11.5-linux-x64 node
```

```sh
$ ls node/bin
$ echo ${PATH}
$ export PATH=${PATH}:`pwd`/node/bin
$ echo ${PATH}
$ mkdir scripts
$ cat > scripts/activate<<EOF
export PATH=\${PATH}:`pwd`/node/bin
EOF
$ source scripts/activate
```

```sh
$ gem install gist
```

```sh
$ (umask 0077 && echo ${GIST_TOKEN} > ~/.gist)
```

## Report

```sh
$ export LAB_NUMBER=01
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gist REPORT.md
```

## Links

### Unix commands

- [ar](https://en.wikipedia.org/wiki/Ar_(Unix))
- [cat](https://en.wikipedia.org/wiki/Cat_(Unix))
- [cd](https://en.wikipedia.org/wiki/Cd_(command))
- [cp](https://en.wikipedia.org/wiki/Cp_(Unix))
- [cut](https://en.wikipedia.org/wiki/Cut_(Unix))
- [echo](https://en.wikipedia.org/wiki/Echo_(command))
- [env](https://en.wikipedia.org/wiki/Env_(shell))
- [ex](https://en.wikipedia.org/wiki/Ex_(editor))
- [file](https://en.wikipedia.org/wiki/File_(command))
- [find](https://en.wikipedia.org/wiki/Find)
- [ls](https://en.wikipedia.org/wiki/Ls)
- [man](https://en.wikipedia.org/wiki/Man_page)
- [mkdir](https://en.wikipedia.org/wiki/Mkdir)
- [mv](https://en.wikipedia.org/wiki/Mv)
- [nm](https://en.wikipedia.org/wiki/Nm_(Unix))
- [ps](https://en.wikipedia.org/wiki/Ps_(Unix))
- [pwd](https://en.wikipedia.org/wiki/Pwd)
- [rm](https://en.wikipedia.org/wiki/Rm_(Unix))
- [sed](https://en.wikipedia.org/wiki/Sed)
- [touch](https://en.wikipedia.org/wiki/Touch_(Unix))

### Package Managers

- [apt](http://help.ubuntu.ru/wiki/apt) | [dnf](https://en.wikipedia.org/wiki/DNF_(software)) | [yum](https://fedoraproject.org/wiki/Yum/ru)
- [brew](https://brew.sh) | [linuxbrew](http://linuxbrew.sh)
- [npm](https://docs.npmjs.com)

### Software

- [curl](https://www.gitbook.com/book/bagder/everything-curl/details)
- [wget](https://www.gnu.org/software/wget/manual/wget.pdf)
- [clang](https://clang.llvm.org)
- [g++](https://gcc.gnu.org/onlinedocs/gcc-4.0.2/gcc/G_002b_002b-and-GCC.html)
- [make](https://en.wikipedia.org/wiki/Make_(software))
- [open](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/open.1.html)
- [openssl](https://www.openssl.org)
- [nano](https://www.nano-editor.org)
- [tree](https://linux.die.net/man/1/tree)
- [vim](http://www.vim.org)

## Homework

1. Скачайте библиотеку *boost* с помощью утилиты **wget**. Адрес для скачивания `https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz`.
```
$ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
```
[result](https://gist.github.com/ValyaLivsh/5d74351d75812fb696340406bbb02c03#file-lab1-1-txt)

2. Разархивируйте скаченный файл в директорию `~/boost_1_69_0`
```
$ mkdir ~/boost_1_69_0
$ tar -xvzf boost_1_69_0.tar.gz -C boost_1_69_0
```

3. Подсчитайте количество файлов в директории `~/boost_1_69_0` **не включая** вложенные директории.
```
$ cd boost_1_69_0/boost_1_69_0
$ find -maxdepth 1 -type f | wc -l
12
```

4. Подсчитайте количество файлов в директории `~/boost_1_69_0` **включая** вложенные директории.
```
$ find -type f | wc -l
61191
```

5. Подсчитайте количество заголовочных файлов, файлов с расширением `.cpp`, сколько остальных файлов (не заголовочных и не `.cpp`).
```
$ find -type f -name "*.h" | wc -l
296

$ find -type f -name "*.hpp" | wc -l
14912

$ find -type f -name "*.cpp" | wc -l
13774

$ find -type f ! -name "*.hpp" ! -name "*.cpp" ! -name "*.h" | wc -l
32209
```

6. Найдите полный пусть до файла `any.hpp` внутри библиотеки *boost*.
```
$ find -type f -iname "any.hpp"
./boost/hana/any.hpp
./boost/hana/fwd/any.hpp
./boost/proto/detail/any.hpp
./boost/type_erasure/any.hpp
./boost/xpressive/detail/utility/any.hpp
./boost/spirit/home/support/algorithm/any.hpp
./boost/any.hpp
./boost/fusion/algorithm/query/any.hpp
./boost/fusion/algorithm/query/detail/any.hpp
./boost/fusion/include/any.hpp
```
7. Выведите в консоль все файлы, где упоминается последовательность `boost::asio`.
```
$ grep -r "boost::asio"
```
[result](https://gist.github.com/ValyaLivsh/fb16f822117c42e6379acc76673ec09a#file-lab1-7-txt)

8. Скомпилирутйе *boost*.
```
$ ./bootstrap.sh --prefix=boost_output
```
[result](https://gist.github.com/ValyaLivsh/db63e57fa6dfa460bd74daf052b575f3#file-lab1-8-txt)

```
$ ./b2 install -j 12
```
[result](https://gist.github.com/ValyaLivsh/0c1470d397c0c7a2e19fb2804818e213#file-lab1-8-2-txt)

9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию `~/boost-libs`.
```
$ mv boost_output/lib/ ~/boost-libs/
```

10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
```
$ find . -type f -exec du -h {} +
```
[result](https://gist.github.com/ValyaLivsh/054cd485838e60570c873e092b5f49fa#file-lab1-10-txt)

11. Найдите *топ10* самых "тяжёлых".
```
$ find . -type f -exec du -h {} +|sort -rh | head -n 10
154M    ./bin.v2/libs/math/build/gcc-13.2.1/release/threading-multi/src/tr1/pch.hpp.gch
154M    ./bin.v2/libs/math/build/gcc-13.2.1/release/link-static/threading-multi/src/tr1/pch.hpp.gch
12M     ./libs/math/doc/math.pdf
4,5M    ./bin.v2/libs/wave/build/gcc-13.2.1/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/libboost_wave.a
3,7M    ./status/expected_results.xml
3,2M    ./bin.v2/libs/regex/build/gcc-13.2.1/release/link-static/threading-multi/visibility-hidden/libboost_regex.a
3,0M    ./libs/gil/io/test_images/raw/RAW_CANON_D30_SRGB.CRW
2,7M    ./libs/asio/doc/reference.qbk
2,7M    ./libs/algorithm/test/search_test_data/0001.corpus
2,7M    ./bin.v2/libs/math/build/gcc-13.2.1/release/link-static/threading-multi/visibility-hidden/libboost_math_tr1l.a
```

```
Copyright (c) 2015-2021 The ISC Authors
```
