# Audio Transcription and Word Error Rate Calculation

This project involves extracting audio files from a directory, generating transcripts for those audio files using speech recognition, and calculating the Word Error Rate (WER) between the generated transcripts and the corresponding ground truth transcripts. The Word Error Rate is a metric used to evaluate the performance of speech recognition systems by measuring the edit distance between the generated transcript and the ground truth transcript.

## Code Overview

The project is implemented in a single Python script or Jupyter Notebook file, which consists of the following components:

### 1. Extract Audio Files

The `extract_audios` function is responsible for extracting all audio files from a given folder path and copying them to an output folder. It recursively traverses the directory structure and copies files with the following extensions: `.mp3`, `.wav`, `.flac`, `.ogg`, and `.aac`. You can add or remove extensions as per your requirements.

### 2. Generate Transcripts

The `generate_transcript` function generates transcripts for the extracted audio files using the Google Speech Recognition API. It reads the audio data from the file, recognizes the speech using the API, and returns the transcript as a string. The function handles exceptions related to speech recognition errors, such as when the audio is not understood or when there is a request error from the API.

### 3. Create DataFrame

The code creates a pandas DataFrame with two columns: `'audio_file'` and `'transcript'`. It iterates over the extracted audio files, generates transcripts using the `generate_transcript` function, and stores the file names and transcripts in the DataFrame. This DataFrame will serve as the basis for further processing and analysis.

### 4. Get Ground Truth

The `get_ground_truth` function is used to retrieve the ground truth transcripts from a separate dataset or file. It checks if the audio file name is present in the 'file_path' column of the ground truth data, and if a match is found, it returns the corresponding ground truth transcript. The ground truth transcripts are typically manually created and serve as the reference for evaluating the performance of the speech recognition system.

### 5. Calculate Word Error Rate

The `calculate_wer` function calculates the Word Error Rate (WER) between the generated transcript and the corresponding ground truth transcript for each row in the DataFrame. It uses the `wer` function from the `jiwer` library to compute the WER. The Word Error Rate is a measure of the edit distance between the generated transcript and the ground truth transcript, taking into account insertions, deletions, and substitutions of words.

If the ground truth transcript is missing (NaN), the function returns NaN as the WER for that row.

The code applies the `calculate_wer` function to the DataFrame and creates a new column `'wer'` to store the calculated WER values for each audio file.

## Dependencies

The project requires the following Python libraries:

- `pandas`: A powerful data analysis and manipulation library for Python.
- `speech_recognition`: A library for performing speech recognition with support for several APIs and engines.
- `jiwer`: A library for computing Word Error Rate and other evaluation metrics for speech recognition systems.

You can install these libraries using pip:
