# Polls

This project was created during the [Rocketseat](https://www.rocketseat.com.br/) Next Level Week event, Expert edition. It allows to create polls and vote on them. These polls are saved on a PostgreSQL database, for that, the application uses the Prisma ORM. Also, the API has an Websocket connection where every time a user votes on the poll, the API sends a message on this connection including the updates on the vote of a single poll. The polls vote ranking are managed with redis.

# Getting Started

## Versions

Node v20.11.0

## Installations

```bash
npm install
```

## Environment Variables

Create a new `.env` file inside the project root, and define your database URL using the content below and replacing the `<user` and `<password` by the database user and password respectively.

`.env`:

```
DATABASE_URL="postgresql://<user>:<password>@localhost:5432/polls?schema=public"
```

## Running Docker images

```bash
docker compose up -d
```

This will start a PostgreSQL instance and a Redis instance on Docker.

## Running migrations

This will run all migrations creating the tables and other configs inside the database.

```bash
npx prisma migrate dev
```

## Running

```bash
npm run dev
```

The API will be running on `http://localhost:3333` and websocket on `ws://localhost:3333`.

## Routes

You can import the HTTP requests collection with the file `request-collection.json`.

| Route                  | Method | Protocol | Description                                    |
| ---------------------- | ------ | -------- | ---------------------------------------------- |
| /polls                 | POST   | HTTP     | Create a new poll.                             |
| /polls/:pollId         | GET    | HTTP     | Get a single poll.                             |
| /polls/:pollId/vote    | POST   | HTTP     | Vote on a poll option.                         |
| /polls/:pollId/results | --     | WS       | Open a WS connection to receive votes results. |
