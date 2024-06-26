# Оглавление
- [Git Fetch vs Git Pull](#git-fetch-vs-git-pull)
  - [Когда использовать каждую команду](#когда-использовать-каждую-команду)
- [Изменение последнего коммита](#изменение-последнего-коммита)
  - [Локальный репозиторий](#локальный-репозиторий)
  - [Удаленный репозиторий](#удаленный-репозиторий)
- [Полезные материалы](#полезные-материалы)

## Git Fetch vs Git Pull

![Git Fetch vs Git Pull](https://pbs.twimg.com/media/FLG-tC-UcAEPRNk.jpg "Git Fetch vs Git Pull Illustration")

Изображение предоставлено [Allison Horst](https://x.com/allison_horst/status/1491183918883966976?s=20).

- **`git fetch`** загружает изменения из удаленного репозитория, но не объединяет их с вашей текущей рабочей веткой. Это позволяет вам проверить изменения перед их интеграцией.

- **`git pull`**, в свою очередь, делает оба действия: загружает изменения и сразу же пытается объединить их с вашей текущей веткой. Это удобно для быстрой синхронизации, но может привести к необходимости разрешения конфликтов слияния, если изменения касаются одних и тех же частей кода.

### Когда использовать каждую команду

Используйте `git fetch`, чтобы увидеть изменения в удаленных ветках, без влияния на вашу текущую рабочую ветку. После просмотра изменений вы можете выполнить `git merge` или `git rebase`, чтобы интегрировать эти изменения.

Используйте `git pull`, когда вы готовы сразу принять и интегрировать изменения из удаленного репозитория в вашу текущую ветку.

## Изменение последнего коммита
### Локальный репозиторий
Если вы хотите включить новые изменения в последний коммит:
```bash
git add <файлы_для_коммита>
git commit --amend
```
Откроется редактор для изменения сообщения коммита. Если вы не хотите менять сообщение коммита, сохраните и закройте редактор.

Если вы хотите сохранить предыдущее сообщение коммита, используйте флаг `--no-edit`:
```bash
git commit --amend --no-edit
```

### Удаленный репозиторий
Если последний коммит уже был отправлен в удалённый репозиторий, после его изменения:
```bash
git push <удаленный_репо> <ветка> --force
```
Или, если вы используете Git версии 2.5 и выше, можно использовать более безопасный вариант:
```bash
git push <удаленный_репо> <ветка> --force-with-lease
```
При использовании `git push --force` вы перезаписываете ветку в удалённом репозитории без предупреждений, что может привести к потере чужих коммитов. В отличие от этого, `git push --force-with-lease` предотвращает перезапись, если кто-то уже обновил ветку после вашего последнего `fetch` или `pull`.
Команда `--force-with-lease` сначала проверит, что состояние удалённой ветки совпадает с вашими ожиданиями (то есть не было новых коммитов), прежде чем принудительно обновить её. Если были обнаружены новые коммиты, команда не будет выполнена, что позволяет избежать случайной потери работы, выполненной другими коллегами.

![image](https://github.com/shinkai-tester/first_steps_js/assets/57576102/dfd30526-d774-4b2a-86d5-ae0500f2415e)


## Полезные материалы

- [GIT PURR! Git Commands Explained with Cats!](https://girliemac.com/blog/2017/12/26/git-purr/)
- [GitHub Training Kit](https://training.github.com/)
- [Interactive resources for learning Git](https://www.makeuseof.com/git-learn-interactive-resources/)
- [Baeldung's Git Guide](https://www.baeldung.com/ops/git-guide)
- [Git Amend w3schools](https://www.w3schools.com/git/git_amend.asp?remote=github)
- [Git Cheatsheet](https://ndpsoftware.com/git-cheatsheet.html#loc=index;)
