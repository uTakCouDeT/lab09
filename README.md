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

## Tutorial

```bash
$ export GITHUB_TOKEN=<полученный_токен>
$ export GITHUB_USERNAME=<имя_пользователя>
```

```bash
$ git clone https://github.com/${GITHUB_USERNAME}/lab8 lab9
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab9
$ cd lab9
```

```bash
$ cmake -H. -B_build -DCPACK_GENERATOR="TGZ"
$ cmake --build --target package
```

```bash
$ git tag v0.1.0.0
$ git push --tags
```

```bash
$ github-release info -u ${GITHUB_USERNAME} -r lab9
$ github-release release \
    --user ${GITHUB_USERNAME} \
    --repo lab9 \
    --tag v0.1.0.0 \
    --name "libprint" \
    --description "my first release" \
```

```bash
$ OS=`uname -s` AR=`uname -a` github-release upload \
    --user ${GITHUB_USERNAME} \
    --repo lab9 \
    --tag v0.1.0.0 \
    --name "${OS}-${AR}" \
    --file _build/*.tgz
```

```bash
$ github-release info -u ${GITHUB_USERNAME} -r lab8
```

## Links

- [Create Release](https://help.github.com/articles/creating-releases/)
- [Get GitHub Token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/)
- [github-release](https://github.com/aktau/github-release)
