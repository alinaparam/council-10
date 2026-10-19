# Council of 10 / Совет десяти

A Claude Code skill. Ask a hard question and 10 advisors argue about it: optimist, pessimist, realist, devil's advocate, practitioner, strategist, skeptic, innovator, financier and human. They answer separately, review each other anonymously, and a chairman gives you one decision with a first step.

Скилл для Claude Code. Задаёшь трудный вопрос, и 10 советников спорят: оптимист, пессимист, реалист, адвокат дьявола, практик, стратег, скептик, новатор, финансист и «человек». Они отвечают отдельно, анонимно оценивают друг друга, а председатель выдаёт одно решение и первый шаг.

## Install / Установка

Windows (PowerShell):

```powershell
git clone https://github.com/alinaparam/council-10 "$env:TEMP\council-10"
Copy-Item -Recurse "$env:TEMP\council-10\council-10" "$env:USERPROFILE\.claude\skills\council-10"
```

macOS / Linux:

```bash
git clone https://github.com/alinaparam/council-10 /tmp/council-10
cp -r /tmp/council-10/council-10 ~/.claude/skills/council-10
```

Restart Claude Code. / Перезапусти Claude Code.

## Use / Как пользоваться

Say one of these in Claude Code:

- `созови совет: переходить ли мне на другую работу?`
- `council this: should I launch a course or a workshop?`
- `pressure-test this plan`

You get: decision, why, where the council agreed and split, main risk, first step, what would change the verdict.

## Notes

- It spawns 10 sub-agents plus reviewers, so it uses noticeably more tokens than a normal answer. Save it for decisions that matter.
- Change the advisors by editing `council-10/SKILL.md`.
