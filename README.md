# OCR Invoice Processing with LangGraph

This project is a Python-based pipeline for processing invoice images using Optical Character Recognition (OCR). It extracts key information (vendor, invoice number, date, total, currency), cleans and validates the data, stores it in a SQLite database, and logs the results. The workflow is orchestrated using LangGraph, a framework for building robust, stateful applications.

- Features: 

OCR Extraction: Reads text from invoice images using an OCR library (e.g., easyocr).

Text Cleaning: Normalizes noisy OCR output to improve accuracy.

Data Validation: Ensures extracted data meets basic schema and numeric requirements.

Data Storage: Saves processed data to a SQLite database.

Notification: Logs processing outcomes with validation status and key details.

Fallback Extraction: Uses regex-based heuristic extraction when AI-based processing is unavailable.

- Project Structure:

The pipeline consists of the following key components:

NODE_OCR: Extracts raw text from an image file using OCR.

NODE_CLEAN: Cleans noisy OCR text using a LangGraph-based cleaning node, with fallback to pass-through on errors.

_heuristic_extract: A fallback regex-based function to extract structured data (vendor, number, date, total, currency) from cleaned text.

NODE_VALIDATION: Checks the extracted data for required fields and numeric validity.

NODE_PERSIST: Stores the validated data in a SQLite database.

NODE_NOTIFY: Prints a summary of the processing outcome, including validation status.

- Requirements:

Python 3.8+

Libraries: pytesseract, langgraph, sqlite3, json, re, and other dependencies (see requirements.txt for details).

Tesseract OCR installed on your system.