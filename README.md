# Gleam Docker Image

This repository contains a Dockerfile for creating a Docker image with Gleam programming language.

## What is Gleam?

Gleam is a friendly language for building type-safe, scalable systems! It compiles to Erlang and has a Go-like syntax with a powerful type system.

## Docker Image

This Docker image provides a ready-to-use environment for Gleam development. It's based on the official Erlang image and includes the latest stable version of Gleam.

## Usage

### Pull the Image

To pull the pre-built image from Docker Hub:

```bash
docker pull michalhodur/gleam:latest
```

### Build the Image

If you want to build the image yourself:

1. Clone this repository:
   ```bash
   git clone https://github.com/mjwhodur/gleam-docker.git
   cd gleam-docker
   ```

2. Build the Docker image:
   ```bash
   docker build .
   ```

### Run a Gleam Project

To run a Gleam project using this Docker image:

```bash
docker run -it --rm -v $(pwd):/app michalhodur/gleam:latest gleam run
```

This command mounts your current directory to `/app` in the container and runs the Gleam project.

## Dockerfile

The Dockerfile uses a multi-stage build to keep the final image size small:

1. It starts with the official Erlang image.
2. Downloads and installs the latest version of Gleam.
3. Sets up the working directory and default command.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is open source and available under the [MIT License](LICENSE).

## Contact

If you have any questions or feedback, please open an issue on this GitHub repository.
