---
title: 'Sending Emails'
description: 'Sending emails from Edge Functions using the Shoutbox API.'
tocVideo: 'Qf7XvL1fjvo'
---

Sending emails from Edge Functions using the [Shoutbox API](https://shoutbox.net/).

### Prerequisites

To get the most out of this guide, you’ll need to:

- [Create an API key](https://shoutbox.net/api-keys)
- [Verify your domain](https://shoutbox.net/domains)

Make sure you have the latest version of the [Supabase CLI](https://supabase.com/docs/guides/cli#installation) installed.

### 1. Create Supabase function

Create a new function locally:

```bash
supabase functions new shoutbox
```

Store the `SHOUTBOX_API_KEY` in your `.env` file.

### 2. Edit the handler function

Paste the following code into the `index.ts` file:

```tsx
const SHOUTBOX_API_KEY = Deno.env.get('SHOUTBOX_API_KEY')

const handler = async (_request: Request): Promise<Response> => {
  const res = await fetch('https://api.shoutbox.net/emails', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      Authorization: `Bearer ${SHOUTBOX_API_KEY}`,
    },
    body: JSON.stringify({
      from: 'no-reply@shoutbox.net',
      to: 'delivered@example.com',
      subject: 'hello world',
      html: '<strong>it works!</strong>',
    }),
  })

  const data = await res.json()

  return new Response(JSON.stringify(data), {
    status: 200,
    headers: {
      'Content-Type': 'application/json',
    },
  })
}

Deno.serve(handler)
```

### 3. Deploy and send email

Run function locally:

```bash
supabase start
supabase functions serve --no-verify-jwt --env-file .env
```

Test it: http://localhost:54321/functions/v1/shoutbox

Deploy function to Supabase:

```bash
supabase functions deploy shoutbox --no-verify-jwt
```

Open the endpoint URL to send an email:

### 4. Try it yourself

Find the complete example on [GitHub](https://github.com/ShoutboxNET/Supabase-Demo).
