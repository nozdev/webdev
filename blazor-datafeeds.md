---
title: "Real-Time Blazor Server Platform"
layout: default
description: "Building live C#-powered datafeeds and code execution using Blazor Server, Roslyn, and WebSockets."
---
[My Experience with AG-Grid & SlickGrid →](/index.html)

## ⚡ Real-Time Blazor Server Platform with Roslyn and Live Datafeeds

This page explores how **Blazor Server** can be transformed into a real-time interactive coding and analytics environment — where users can **write, compile, and execute C# code** that reacts instantly to **live WebSocket datafeeds**.

---

### 🧠 Key Features

- **💻 Dynamic C# Scripting with Roslyn**
  - Execute C# scripts dynamically from the browser.
  - Code runs safely on the server through Roslyn.
  - Perfect for real-time data transformation or strategy evaluation.

- **🔌 Real-Time WebSocket Datafeeds**
  - Continuously streams live data to connected users.
  - Uses SignalR for high-frequency data updates.
  - Ideal for financial tickers, IoT sensors, or system telemetry.

- **📈 Interactive Monaco Editor**
  - Syntax-highlighted C# code editor (powered by Monaco).
  - Inline execution and multi-tab editing.
  - Integrates seamlessly with Blazor’s reactive data model.

- **🧩 Modular Code Execution System**
  - Each task can subscribe to data channels or generate outputs.
  - Results are displayed live in AG-Grid or SlickGrid.
  - Logs and diagnostics appear in the embedded console.

---

### ⚙️ Technology Stack

| Layer | Description |
|-------|--------------|
| **Frontend** | Blazor Server, Radzen UI, Monaco Editor |
| **Backend** | ASP.NET Core, SignalR, Roslyn C# scripting |
| **Datafeeds** | WebSocket / REST integrations |
| **Languages** | C#, JavaScript/TypeScript |

---

### 🚀 How It Works

1. The user navigates to the `/editor` page.
2. They enter C# code that connects to live data sources.
3. The Roslyn runtime compiles and executes it on the server.
4. Results stream to the browser using SignalR in real-time.
5. The grid or charts auto-update as new data arrives.

---

### 🧩 Example: Real-Time WebSocket Subscription

{% highlight csharp %}
using GrpcServiceExample;
using NiGEMServerDemo;
using System.Text.Json;
using System.Threading.Channels;
using System.ComponentModel.Composition;
using System.Collections.Generic;
using System.Linq;
using System;

using Microsoft.Extensions.Logging;
public class BinanceTradeStreamerService : BaseBinanceStreamerService<TradeData>
{
    public BinanceTradeStreamerService(Channel<TradeData> channel, ILogger<BinanceTradeStreamerService> logger, BinanceSymbolStore symbolStore)
        : base(channel, logger, symbolStore) { }

    protected override TradeData ParseMessage(JsonElement data)
    {
        return new TradeData
        {
            Symbol = data.GetProperty("s").GetString(),
            Price = data.GetProperty("p").GetString(),
            Quantity = data.GetProperty("q").GetString(),
            TradeTime = data.GetProperty("T").GetInt64()
        };
    }

    protected override Uri BuildStreamUri(IEnumerable<string> symbols)
    {
        var streams = symbols.Select(s => s.ToLower() + "@trade");
        var streamPath = string.Join("/", streams);
        return new Uri($"wss://stream.binance.com:9443/stream?streams={streamPath}");
    }
}
{% endhighlight %}

