## Laboratory work IX

Данная лабораторная работа посвещена изучению процесса создания пакета на примере **Github Release**

```bash
$ open https://help.github.com/articles/creating-releases/
```

## Tasks

- [ ] 1. Создать публичный репозиторий с названием **lab9** на сервисе **GitHub**
- [ ] 2. Ознакомиться со ссылками учебного материала
- [ ] 3. Получить токен для доступа к репозиториям сервиса **GitHub**
- [ ] 4. Выполнить инструкцию учебного материала
- [ ] 5. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```bash
$ export GITHUB_TOKEN=<полученный_токен>
$ export GITHUB_USERNAME=<имя_пользователя>
```

```bash
$ git clone https://github.com/${GITHUB_USERNAME}/lab8 lab9
$ cd lab9
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab9
```

```bash
$ cmake -H. -B_build -DCPACK_GENERATOR="TGZ"
$ cmake --build _build --target package
```

```bash
$ sed -i '' 's/lab8/lab9/g' README.md
```

```bash
$ travis login --auto
$ travis enable
```

```bash
$ git tag v0.1.0.0
$ git push origin master
$ git push --tags
```

```bash
$ github-release --version
$ github-release info -u ${GITHUB_USERNAME} -r lab9
$ github-release release \
    --user ${GITHUB_USERNAME} \
    --repo lab9 \
    --tag v0.1.0.0 \
    --name "libprint" \
    --description "my first release"
```

```bash
$ export PACKAGE_OS=`uname -s` PACKAGE_ARCH=`uname -m` 
$ export PACKAGE_FILENAME=print-${PACKAGE_OS}-${PACKAGE_ARCH}.tar.gz
$ github-release upload \
    --user ${GITHUB_USERNAME} \
    --repo lab9 \
    --tag v0.1.0.0 \
    --name "${PACKAGE_FILENAME}" \
    --file _build/*.tar.gz
```

```bash
$ github-release info -u ${GITHUB_USERNAME} -r lab9
$ wget https://github.com/${GITHUB_USERNAME}/lab9/releases/download/v0.1.0.0/${PACKAGE_FILENAME}
$ tar -ztf ${PACKAGE_FILENAME}
```

## Links

- [Create Release](https://help.github.com/articles/creating-releases/)
- [Get GitHub Token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/)
- [github-release](https://github.com/aktau/github-release)

```
Copyright (c) 2017 Vyacheslav Vershinin
```
