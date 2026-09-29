# Putting Test2u on Netlify

This zip contains the complete Test2u source code. Test2u is not a plain static
site — it needs a server to run the exam engine (starting attempts, the timer,
auto-save and marking). Netlify can run it, but it has to build the project; you
cannot drag a folder of ready-made HTML into Netlify for this app.

## Steps

1. Unzip this folder.
2. Go to netlify.com, choose "Add new site" and upload/connect this project.
   (Easiest reliable path: push the unzipped folder to a GitHub repository and
   pick "Import from Git" in Netlify.)
3. Netlify reads `netlify.toml`, so the build command and publish folder are
   already set for you.
4. Before the first deploy, add these environment variables in
   Netlify → Site settings → Environment variables:

   - `VITE_SUPABASE_URL`
   - `VITE_SUPABASE_PUBLISHABLE_KEY`
   - `VITE_SUPABASE_PROJECT_ID`
   - `SUPABASE_URL`
   - `SUPABASE_PUBLISHABLE_KEY`
   - `SUPABASE_PROJECT_ID`
   - `SUPABASE_SERVICE_ROLE_KEY`

   The first six are in the `.env.example` file included here — copy the values
   from your own database settings.

5. Deploy.

## Important

The student exam engine keeps answer keys on the server, so it needs the
**service role key** of your database. That key is not available from inside
Lovable, so you will only be able to fill it in if you move the database to your
own account. Without it, the teacher pages and sign-in still work, but starting
and marking an exam will fail.

If you would rather not manage any of this, publishing straight from Lovable
handles the server, the keys and the database for you in one click.
