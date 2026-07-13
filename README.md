# GitHub Repositories Node

A custom **MachinaOS/OpenCompany workflow node** that retrieves all repositories associated with an authenticated GitHub account using the GitHub REST API.

This node integrates seamlessly with the existing GitHub credential system and returns repository information in a structured JSON format, making it easy to use in automation workflows.

---

## Features

- Authenticate using a GitHub Personal Access Token
- Fetch all repositories for the authenticated user
- Returns structured JSON output
- Uses the existing GitHub credential provider
- Automatically registers as a workflow node
- Fully compatible with MachinaOS plugin architecture

---

## Repository Structure

```
server/
└── nodes/
    └── github/
        ├── __init__.py
        ├── credentials.py
        └── github_repositories/
            ├── __init__.py
            ├── meta.json
            └── icon.svg
```

---

## Output

The node returns repository details including:

- Repository Name
- Full Repository Name
- Description
- Visibility (Public / Private)
- Default Branch
- Programming Language
- Repository URL

Example:

```json
{
  "count": 13,
  "repositories": [
    {
      "name": "MachinaOS",
      "full_name": "username/MachinaOS",
      "visibility": "public",
      "language": "Python",
      "default_branch": "main",
      "html_url": "https://github.com/username/MachinaOS"
    }
  ]
}
```

---

## Requirements

- Python 3.11+
- MachinaOS / OpenCompany
- GitHub Personal Access Token
- Internet connection

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/<repository>.git
```

### 2. Copy the node

Place the folder inside

```
server/nodes/github/
```

so the directory becomes

```
server/nodes/github/github_repositories/
```

---

## Configure Credentials

Create a GitHub Personal Access Token.

Store it inside your environment variables.

Example:

```env
GITHUB_TOKEN=ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

The node reuses the existing GitHub credential implementation already available in MachinaOS.

---

## Running

Start MachinaOS normally.

```bash
pnpm install

pnpm run build

pnpm run dev
```

or

```bash
python server.py
```

(depending on your installation)

After startup, the new **GitHub Repositories** node will automatically appear inside the **GitHub** category.

---

## How It Works

1. Reads the GitHub Personal Access Token.
2. Authenticates with GitHub REST API.
3. Fetches repositories of the authenticated user.
4. Parses the API response.
5. Returns structured JSON output.
6. Makes the output available to downstream workflow nodes.

---

## Plugin Architecture

The implementation follows the MachinaOS plugin system.

The node consists of:

- **ActionNode**
- **Pydantic Input Model**
- **Pydantic Output Model**
- **Operation Method**

Since MachinaOS performs automatic plugin discovery, no manual registration is required.

---

## Files

| File | Description |
|------|-------------|
| `__init__.py` | Main node implementation |
| `meta.json` | Node metadata |
| `icon.svg` | Workflow editor icon |

---

## Future Improvements

Possible enhancements include:

- Repository Search
- Pagination Support
- Branch Listing
- Commit History
- Pull Requests
- Issues
- Contributors
- GitHub Organizations
- Repository Statistics
- Starred Repositories
- Fork Information

---

## Screenshots

### Workflow Node

_Add screenshot here_

---

### Execution Result

_Add screenshot here_

---

## Technologies Used

- Python
- Pydantic
- GitHub REST API
- MachinaOS Plugin Framework

---

## References

- MachinaOS Plugin System Documentation
- GitHub REST API Documentation

---

## Author

**Soumik Roy**

Automation & Workflow Development

---

## License

This project is intended for educational and development purposes.
