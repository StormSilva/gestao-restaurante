# Gestão de Restaurante (v0.1)

Next.js + Tailwind + Supabase (Postgres, Auth, Realtime).

## Como rodar
1. Crie um projeto grátis em supabase.com.
2. No SQL Editor, rode `supabase/schema.sql`.
3. Em Authentication > Users, crie o usuário do dono (e-mail e senha).
4. Vincule o dono a um restaurante (SQL Editor):
   ```sql
   with r as (insert into restaurantes (nome, slug) values ('Meu Restaurante', 'meu-restaurante') returning id)
   insert into usuarios (id, restaurante_id) select 'UUID-DO-USUARIO', id from r;
   ```
5. `cp .env.example .env.local` e preencha URL e chave anon (Project Settings > API).
6. `npm install && npm run dev` e abra http://localhost:3000

## Próximos passos
- Cardápio público `/r/[slug]` com carrinho que grava em `pedidos` e `pedido_itens`
- Upload de fotos (Supabase Storage)
- Dashboard de análises (itens mais vendidos, faturamento por dia/hora)
