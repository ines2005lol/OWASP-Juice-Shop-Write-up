# Setup

How to get OWASP Juice Shop running on my machine.

## Option 1: Docker (recommended)

Docker is the easiest way: no need to install Node.js or build anything.

### 1. Make sure Docker is running

Open Docker Desktop, then check in a terminal:

```powershell
docker --version
```

### 2. Download the Juice Shop image

```powershell
docker pull bkimminich/juice-shop
```

### 3. Start Juice Shop

```powershell
docker run --rm -p 127.0.0.1:3000:3000 bkimminich/juice-shop
```

What the flags mean:

| Flag | Meaning |
|------|---------|
| `--rm` | Delete the container when it stops (keeps things clean) |
| `-p 127.0.0.1:3000:3000` | Make the app reachable on port 3000, **only from my own machine** |

### 4. Open it in the browser

Go to **http://localhost:3000**

### 5. Stop it

Press `Ctrl + C` in the terminal where it's running.

> ⚠️ Because of `--rm`, stopping the container **resets all progress** on the
> Score Board. That's fine since my solutions are written down in this repo,
> but keep it in mind. (Juice Shop can also save/restore progress from the
> Score Board page.)

## Option 2: Node.js (from source)

Only needed if Docker doesn't work. Requires Node.js (an LTS version).

```powershell
git clone https://github.com/juice-shop/juice-shop.git --depth 1
```

```powershell
cd juice-shop
```

```powershell
npm install
```

```powershell
npm start
```

Then open **http://localhost:3000**.

## Useful tools

Start with just the browser, add the others when a challenge needs them.

- **Browser DevTools** (`F12`): inspect the page, read JavaScript, watch
  network requests. This is enough for most early challenges.
- **[Burp Suite Community](https://portswigger.net/burp/communitydownload)**:
  intercept and modify requests between the browser and the server.
- **[CyberChef](https://gchq.github.io/CyberChef/)**: decode/encode Base64,
  hashes, JWTs, etc.

## First steps once it's running

1. Explore the shop like a normal user: register, browse, add to basket.
2. Find the hidden **Score Board** (finding it is the first challenge!).
3. Pick a ⭐ challenge, copy `writeups/_TEMPLATE.md`, and start taking notes.
