# SceneSeeker

SceneSeeker is a powerful video scene search tool that extracts scenes from a video, indexes them, and allows for searching using both text and image queries. It leverages advanced AI models to understand the content of video scenes and find relevant matches based on natural language descriptions or similar images.

## Features

- Video scene extraction using OpenCV
- Scene embedding generation with Facebook's ImageBind model
- Efficient indexing and searching with DocArray and HNSW
- Multimodal search capabilities (text and image)
- Support for both CPU and GPU processing

## Prerequisites

- Python 3.7+
- PyTorch
- OpenCV
- ImageBind
- DocArray
- Other dependencies (see `requirements.txt`)

## Installation

1. Clone this repository:
   ```
   git clone https://github.com/Balogunolalere/scene-seeker.git
   cd scene-seeker
   ```

2. Install the required packages:
   ```
   pip install -r requirements.txt
   ```

3. Install ImageBind:
   ```
   pip install git+https://github.com/facebookresearch/ImageBind.git
   ```

## Usage

1. Set the `VIDEO_PATH` variable to the path of your input video.

2. Run the main script:
   ```
   python sceneseeker.py
   ```

3. The script will extract scenes, generate embeddings, and index them.

4. Use the `search` method to find scenes:
   ```python
   # Text search
   text_query = 'child on a green slide'
   text_results = searcher.search(text_query)
   searcher.display_results(text_results)

   # Image search
   image_query = ImageDoc(url='/path/to/query/image.jpg')
   image_results = searcher.search(image_query)
   searcher.display_results(image_results)
   ```

## How It Works

1. **Scene Extraction**: The video is processed to extract key frames representing distinct scenes.
2. **Embedding Generation**: Each scene is embedded using the ImageBind model, which creates a unified representation for both images and text.
3. **Indexing**: The scene embeddings are indexed using HNSW for efficient similarity search.
4. **Searching**: Users can search for scenes using either text descriptions or example images. The system finds the most similar scenes based on the embedded representations.

## Customization

- Adjust the `BATCH_SIZE` variable to optimize memory usage and processing speed.
- Modify the `ContentDetector` parameters in the `extract_scenes` method to fine-tune scene detection sensitivity.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Acknowledgments

- [ImageBind](https://github.com/facebookresearch/ImageBind) by Facebook Research
- [DocArray](https://github.com/docarray/docarray) for efficient indexing and searching
- [OpenCV](https://opencv.org/) for video processing