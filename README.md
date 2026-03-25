# YouTube Transcript Extractor

This project provides a tool to extract transcripts from YouTube videos and save them as structured JSON data. It is particularly useful for creating datasets for RAG (Retrieval-Augmented Generation) applications or other NLP tasks.

## 📋 Table of Contents
- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Usage](#usage)
- [Output Format](#output-format)
- [Workflow](#workflow)

## 🔍 Overview
The `dataset_extraction.ipynb` notebook contains a Python script that utilizes the `youtube-transcript-api` to fetch subtitles/transcripts from specified YouTube videos. The script processes the raw transcript data and saves it into a JSON format suitable for further processing.

## 🛠 Prerequisites

- Python 3.x
- Jupyter Notebook
- `youtube-transcript-api` library

You can install the required library using pip:
```bash
pip install youtube-transcript-api
```

## 🚀 Usage

1. Open the `dataset_extraction.ipynb` notebook.
2. The script defines a helper function `fetch_and_save_transcript(url, filename, languages=["hi"])`.
3. Call this function with the YouTube URL and the desired output filename.

Example:
```python
fetch_and_save_transcript(
    "https://www.youtube.com/watch?v=C6YtPJxNULA",
    "ml_hindi.json"
)
```

## 📄 Output Format

The script generates JSON files containing an array of transcript segments. Each segment has the following structure:

```json
[
  {
    "id": 0,
    "video_id": "C6YtPJxNULA",
    "text": "The actual transcript text...",
    "start": 0.0,
    "end": 5.0
  },
  ...
]
```

- **id**: Sequential identifier for the segment.
- **video_id**: The YouTube video ID.
- **text**: The content of the transcript segment.
- **start**: Start time of the segment in seconds.
- **end**: End time of the segment in seconds.

## 🔄 Workflow

The following diagram illustrates the pipeline implemented in the script:

```mermaid
graph TD
    A([Start]) --> B[/Input YouTube URL/]
    B --> C[Extract Video ID]
    C --> D{Fetch Transcript}
    D -->|Success| E[Process Data Structure]
    D -->|Failure| H([Error Handling])
    E --> F[Format Content (ID, Text, Start, End)]
    F --> G[/Save to JSON File/]
    G --> I([End])

    subgraph "Data Processing"
    C
    D
    E
    F
    end
```