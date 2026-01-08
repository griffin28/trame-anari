# ANARI Pan3D Demo

A Docker-based trame application showcasing Pan3D with ANARI rendering backends (helide, visgl, visrtx).

## Build Docker Image

Build the Docker image using the following command:

```bash
docker build --progress=plain -t pan3d-anari .
```

> **Note:** The build process compiles ANARI-SDK, VisRTX, and VTK from source, which may take a while.

## Run Trame Application

Run the trame application with GPU support:

```bash
docker run --gpus all -e ANARI_LIBRARY=helide -p 12345:80 -it pan3d-anari
```

### ANARI Library Options

The `ANARI_LIBRARY` environment variable specifies which ANARI backend to use:

| Library  | Description                          |
|----------|--------------------------------------|
| `helide` | CPU-based reference implementation   |
| `visgl`  | OpenGL-based rendering               |
| `visrtx` | NVIDIA RTX ray tracing (requires GPU)|

Example with VisRTX:

```bash
docker run --gpus all -e ANARI_LIBRARY=visrtx -p 12345:80 -it pan3d-anari
```

## Connect from Browser

Once the container is running, open your web browser and navigate to:

```
http://localhost:12345
```

The Pan3D trame application interface will load, allowing you to interact with the 3D visualization.

## Debug Commands

To start the container with an interactive shell for debugging:

```bash
docker run --gpus all --entrypoint /bin/bash -it pan3d-anari
```
