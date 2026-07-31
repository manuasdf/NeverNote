# NeverNote

A self-destructing note-sharing web application built with Express and TypeScript. Create notes, share them via unique hash links, and have them automatically deleted upon first access.

## Features

- **Create Notes**: Write notes via a simple web interface
- **Unique Links**: Each note gets a unique SHA-256 hash as its identifier
- **One-Time Access**: Notes are automatically deleted after being read once
- **Security**: Input sanitization to prevent XSS attacks
- **No Database**: Notes are stored as files in the `notes/` directory

## Tech Stack

- **Backend**: Express.js (v5.x)
- **Language**: TypeScript
- **Templating**: Nunjucks
- **Security**: sanitize-html
- **Runtime**: Node.js

## Getting Started

### Prerequisites

- Node.js (v20 or higher recommended)
- npm or yarn

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/manu/NeverNote.git
   cd NeverNote
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Build the TypeScript code:
   ```bash
   npm run build
   ```

4. Start the development server:
   ```bash
   npm run dev
   ```

   Or for production:
   ```bash
   npm start
   ```

5. Open your browser to [http://localhost:3000](http://localhost:3000)

## Usage

1. **Creating a Note**
   - Visit the homepage
   - Enter your note in the text area
   - Click "Create Note"
   - A unique shareable link will be generated

2. **Reading a Note**
   - Open the shareable link in any browser
   - The note content will be displayed
   - The note is immediately deleted from the server after being read

3. **Sharing Notes**
   - Copy the generated link and share it with anyone
   - The recipient can view the note once, then it's gone forever

## Project Structure

```
NeverNote/
├── src/
│   ├── index.ts              # Main Express application
│   ├── model/
│   │   ├── noteCreate.ts     # Note creation logic
│   │   ├── noteRead.ts       # Note reading logic
│   │   └── noteDelete.ts     # Note deletion logic
│   └── views/
│       ├── index.njk         # Base layout
│       ├── input.njk         # Note creation form
│       └── output.njk        # Note display page
├── public/
│   └── client.js             # Frontend JavaScript
├── dist/                    # Compiled TypeScript output
├── notes/                   # Stored notes (auto-created)
├── package.json
├── tsconfig.json
└── README.md
```

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET    | `/`      | Renders the note creation form |
| POST   | `/`      | Creates a new note, returns shareable link |
| GET    | `/:hash` | Reads and deletes the note with the given hash |

## Configuration

The server runs on port 3000 by default. To change the port, modify `src/index.ts`:

```typescript
const port = 3000; // Change this value
```

## Security Features

- **Input Sanitization**: All note content is sanitized using `sanitize-html` to prevent XSS attacks
- **Unique Hashes**: Each note gets a SHA-256 hash as its filename
- **One-Time Read**: Notes are deleted immediately after being accessed

## Development

- **Development mode** (with auto-reload):
  ```bash
  npm run dev
  ```
## License

This project is open source and available under the MIT License.

## Contributing

Contributions are welcome! Feel free to submit pull requests or open issues for bugs and feature requests.

