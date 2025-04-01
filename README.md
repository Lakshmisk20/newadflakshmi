{
    "name": "GitToAzureBlobPipeline",
    "properties": {
        "activities": [
            {
                "name": "CopyFromGitToBlob",
                "type": "Copy",
                "dependsOn": [],
                "policy": {
                    "timeout": "7.00:00:00",
                    "retry": 0
                },
                "userProperties": [],
                "typeProperties": {
                    "source": {
                        "type": "HttpSource",
                        "httpRequestTimeout": "00:10:00"
                    },
                    "sink": {
                        "type": "AzureBlobStorageSink",
                        "blobWriteSettings": {
                            "copyBehavior": "PreserveHierarchy"
                        }
                    }
                },
                "inputs": [
                    {
                        "referenceName": "GitHttpDataset",
                        "type": "DatasetReference"
                    }
                ],
                "outputs": [
                    {
                        "referenceName": "AzureBlobDataset",
                        "type": "DatasetReference"
                    }
                ]
            }
        ],
        "description": "Pipeline to copy CSV from Git to Azure Blob Storage"
    }
}
