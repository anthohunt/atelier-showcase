**English** · [Français](README.fr.md)

> Showcase repository: the code and data of this project are private; this README describes it.

# Atelier

A web portal that opens, for each team project, a coding-agent session shared by all its members, with a built-in meeting assistant.

## The problem

In a research and teaching team, not everyone has a coding agent installed, configured and connected to the right files. Atelier puts that agent in a browser. Each project member logs in and finds the same session, the same working folder and the same conversation. Colleagues use it to design course applications or to write change requests for an existing application.

## How it works

- One project equals one session. The server starts it in a `tmux` session placed in the project's working folder.
- `ttyd` displays that terminal in the browser; a "Message to the session" bar lets users write to the agent without handling the terminal.
- A single access rule: project member or administrator.
- Each project has a shared folder that the agent keeps up to date as work goes on.
- Conversations are kept on disk: after an interruption, the session resumes where it stopped.
- Updates are deployed by reloading the server, without cutting the running sessions.

## What is built

In service. Functions in place:

- Automatic closing every day at 20:00 (Paris time): banner at 19:45, instruction at 19:50 to active sessions to update their folder, sessions stopped at 20:00, conversations kept. Reopening on request only, 24 hours at most. Time calculation checked on 13 cases out of 13 (summer, winter, clock-change days, midnight).
- Meeting assistant: transcription, live summary, tree-shaped minutes, a panel to ask the meeting agent questions or give it instructions, an editable canvas of nodes and links, one active meeting at a time.
- Administration console: accounts, members, projects arranged by drag and drop in a folder tree.
- 15 skills from the web application design pipeline, synchronised every hour to the sessions.

In August 2026, the server was simplified: the idea of a personal agent per member was dropped in favour of one session per project (734 lines reduced to 549).

## What is public

This page is public. The tool, its code and the team's projects remain private.

## Technical stack

- Node.js (server and WebSocket)
- `tmux` and `ttyd`
- Docker
- Traefik
- HTML and JavaScript interface
