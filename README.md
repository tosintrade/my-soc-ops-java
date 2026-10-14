🌐 [Português (BR)](README.pt_BR.md) · [Español](README.es.md)

# Soc Ops

### Turn a room full of strangers into a room full of stories.

Soc Ops is social bingo for in-person mixers. Find people who match the prompts on your 5×5 board, mark the squares, and connect your way to five in a row.

**[Run it locally](#get-started)** · **[Explore the workshop](workshop/GUIDE.md)** · **[See how to play](#how-to-play)**

---

## Make introductions feel easy

No accounts, complicated setup, or awkward icebreaker round required. Start a game, scan your board, and let each square give you a reason to start a conversation.

- **A fresh board every game** — 24 shuffled conversation prompts and a centre free space.
- **Play at your own pace** — tap a square when you find a match; your board is saved in the browser.
- **Celebrate the connection** — complete a row, column, or diagonal to get bingo.
- **Built for the room** — a responsive, touch-friendly board for in-person events.

## How to play

1. Start a game and look over the prompts on your board.
2. Find someone who matches a prompt and ask them about it.
3. Mark the square when you make a match.
4. Get five marked squares in a row to win.

## Get started

You’ll need a Java 21 JDK. The project includes a Maven Wrapper, so a separate Maven installation is not required.

```bash
cd socops
./mvnw spring-boot:run
```

Open [http://localhost:8080](http://localhost:8080) to play.

### Build, test, and lint

```bash
cd socops
./mvnw clean package
./mvnw test
./mvnw verify
```

`verify` includes Checkstyle checks for unused imports and Java formatting conventions.

## Inside the project

Soc Ops is a Spring Boot application using Java 21, Thymeleaf, and a small amount of browser-side JavaScript.

| Path | What’s inside |
| --- | --- |
| [`socops/src/main/java`](socops/src/main/java) | Board generation, bingo rules, and the web controller |
| [`socops/src/main/resources/templates`](socops/src/main/resources/templates) | The game and lobby page |
| [`socops/src/main/resources/static`](socops/src/main/resources/static) | Styles and static assets |
| [`workshop/`](workshop/GUIDE.md) | A hands-on guide to building and extending the project |

## Build along with the workshop

This repository also hosts a guided lab on context engineering, frontend design, and multi-agent development. Start with the [workshop guide](workshop/GUIDE.md):

| Part | Topic |
| --- | --- |
| [00](workshop/00-overview.md) | Overview & checklist |
| [01](workshop/01-setup.md) | Setup & context engineering |
| [02](workshop/02-design.md) | Design-first frontend |
| [03](workshop/03-quiz-master.md) | Custom Quiz Master |
| [04](workshop/04-multi-agent.md) | Multi-agent development |

The workshop is also available in the [`workshop/`](workshop/) folder for offline reading.

---

Have fun, be curious, and let the squares do the introducing.
