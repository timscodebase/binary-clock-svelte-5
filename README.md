# Svelte 5 Binary Clock

A fun coding project to learn Svelte 5 and to create a binary clock. I a have chosen to use a JS map structure to store a lookup table for the binary values of each digit. This is then used to set the class of each digit to either 'active' or '' to display the time.

## Get started

Fork my repo and clone it to your local machine. Then install the dependencies...

```bash
  gh repo clone timscodebase/binary-clock-svelte-5
  cd binary-clock-svelte-5
  pnpm install
```

### Run

```bash
  pnpm run dev
```

### Deploy

I have used [Vercel](https://vercel.com/) to deploy my app.

```bash
  pnpm add -g vercel
  vercel login
  vercel deploy
```
