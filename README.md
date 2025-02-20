# CyberChef Container

This repository contains an automated workflow to build [CyberChef](https://github.com/gchq/CyberChef) from source and package it as a Docker container.

## Features

- Automated weekly builds (Monday, 02:00 UTC)
- Built from latest CyberChef source
- Published to GitHub Container Registry
- Multiple version tags available

## Usage

### Pull the Container

```bash
# Latest version
docker pull ghcr.io/bifr0est/cyberchef_container/cyberchef:latest

# Specific date version
docker pull ghcr.io/bifr0est/cyberchef_container/cyberchef:YYYYMMDD
```

### Run the Container

```bash
# Run on port 8080
docker run -p 8080:80 ghcr.io/bifr0est/cyberchef_container/cyberchef:latest
```

Access CyberChef at http://localhost:8080

## Manual Build

To trigger a manual build:

1. Go to Actions tab
2. Select "Build CyberChef Container from Source"
3. Click "Run workflow"
4. Select 'main' branch
5. Click "Run workflow"

## Technical Details

- Base image: `nginx:1.25-alpine3.18`
- Exposed port: 80
- Content location: `/usr/share/nginx/html/`

## Tags

- `latest`: Most recent build
- `YYYYMMDD`: Date-based version
- `sha-...`: Git SHA version

## Troubleshooting

Common issues and solutions:

1. Image pull failed:
   ```bash
   echo $GITHUB_TOKEN | docker login ghcr.io -u USERNAME --password-stdin
   ```

2. Check container status:
   ```bash
   docker ps
   ```

3. View logs:
   ```bash
   docker logs [container-id]
   ```

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

MIT License

## Acknowledgments

- GCHQ for CyberChef
- GitHub Actions
- GitHub Container Registry