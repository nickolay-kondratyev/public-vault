---
id: g60xux1hbmapf42dfoxj07u
title: Python Extract Text Example
desc: ''
updated: 1688159589026
created: 1688159577236
---


```py
import sys
import boto3

def detect_text(file_path):
    with open(file_path, 'rb') as document:
        image_bytes = bytearray(document.read())

    textract = boto3.client('textract')

    response = textract.detect_document_text(Document={'Bytes': image_bytes})

    for item in response["Blocks"]:
        if item["BlockType"] == "LINE":
            print(item["Text"])

# The script now expects the file path as a command-line argument
if len(sys.argv) > 1:
    detect_text(sys.argv[1])
else:
    print("Please provide the path to an image file.")


```