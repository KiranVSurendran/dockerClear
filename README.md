# Docker Cleanup Tools

This repository provides two tools for cleaning up Docker components:
1. **HTML Web Interface** – A simple web page with buttons to trigger Docker cleanup commands.
2. **Jupyter Notebook** – An interactive notebook with buttons for executing cleanup commands.

## HTML Web Interface
The `docker_cleanup.html` file includes buttons for:
- Stopping all containers
- Removing all containers
- Removing all images
- Removing all volumes
- Removing all networks
- Performing a full system cleanup

### Usage
1. Serve the HTML file using a simple Python server:
   ```sh
   python3 -m http.server 8080
   ```
2. Open `http://localhost:8080/docker_cleanup.html` in your browser.
3. Click the buttons to execute cleanup commands (requires a backend to handle API requests).

## Jupyter Notebook
The `docker_cleanup.ipynb` file provides an interactive way to clean up Docker using Python.

### Usage
1. Install Jupyter if not installed:
   ```sh
   pip install notebook
   ```
2. Open the notebook:
   ```sh
   jupyter notebook docker_cleanup.ipynb
   ```
3. Click the buttons to run cleanup commands directly from the notebook.

## Warning
These commands will **permanently delete all Docker containers, images, volumes, and networks**. Use with caution!

## License
MIT License

