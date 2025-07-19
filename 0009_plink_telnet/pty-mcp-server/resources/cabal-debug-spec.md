# Cabal Debug Command Reference (GHCi-style Help)

This is a reference list of GHCi debugger commands usable within `cabal repl` for interactive debugging.  
All commands must be sent via `pty-message`.

---

## 🛠️ Breakpoint Commands

| Command                    | Description                                      |
|----------------------------|--------------------------------------------------|
| `:break M line`            | Set breakpoint at line in module `M`            |
| `:break M function`        | Set breakpoint at function in module `M`        |
| `:delete n`                | Delete breakpoint number `n`                    |
| `:delete *`                | Delete all breakpoints                          |
| `:show breaks`             | List current breakpoints                        |

---

## ▶️ Execution Commands

| Command           | Description                                  |
|-------------------|----------------------------------------------|
| `:main`           | Run the program entry point (`main`)         |
| `:continue`       | Resume after hitting a breakpoint            |
| `:step`           | Step into next expression                    |
| `:step-over`      | Step over current expression (GHCi 9+)       |
| `:step-out`       | Step out of current function (GHCi 9+)       |
| `:trace`          | Trace execution (legacy)                     |

---

## 🔍 Inspection Commands

| Command               | Description                              |
|------------------------|------------------------------------------|
| `:print var`           | Lazily print the value of `var`         |
| `:force var`           | Fully evaluate and print `var`          |
| `:show bindings`       | Show local variables in scope           |
| `:info name`           | Show type/class info of `name`          |

---

## 🧮 Evaluation Commands

| Command               | Description                              |
|------------------------|------------------------------------------|
| `:<expr>`              | Evaluate expression at prompt            |
| `:type <expr>`         | Show the type of an expression           |
| `:kind <type>`         | Show the kind of a type                  |

---

## 🔄 Session Management

| Command          | Description                              |
|------------------|------------------------------------------|
| `:reload`        | Reload source files                      |
| `:load file.hs`  | Load specific file                       |
| `:quit`          | Exit the REPL                            |
| `:show modules`  | Show loaded modules                      |

---

## 📝 Notes

- Always wait for REPL to return a prompt (`*Main>`) before sending the next command.
- Output may include debugger state, breakpoint hits, or variable values.
- Do not use standard input/output — use `pty-message`.

