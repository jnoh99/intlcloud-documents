An event notification informs you of a file transcoding result, so you can move on to the next logical step.

## Event Notification Definition
An event in MPS refers to a task status change of a file during transcoding. An event notification refers to a message notification that you will receive at the end of an event, which includes the file transcoding result.

## Event Notification Types
Below are types of event notifications currently provided:

| Event Type     | Event Name | Description |
|:---------:|:---:|:---:|
| WorkflowTask | WorkflowTaskEvent | Status change. The `Status` field of the event shows the specific status. <br>Generally, the status is `FINISH`, indicating that the task has ended. The task could have been completed successfully or failed. |

## Event Notification Mode

MPS uses CMQ to send event notifications. When you use MPS, you need to activate CMQ and authorize MPS before you can receive transcoding event notifications. If you do not activate CMQ or do not configure the CMQ queue address for event notification in a workflow template, you will not receive task event notifications from MPS.

>
>- If you use a TencentCloud API to receive CMQ event messages, you need to acknowledge each individual message for the message to be removed from the queue; otherwise, the API will keep pulling the same event messages.
>- For more information on receiving CMQ messages, please see [Consuming Messages](https://intl.cloud.tencent.com/document/product/406/5839). For more information on acknowledging CMQ messages, please see [Deleting a Message](https://intl.cloud.tencent.com/document/product/406/5840).

## Event Notification Sample

```
{
    "EventType":"WorkflowTask",
    "WorkflowTaskEvent":{
        "TaskId":"245****654-WorkflowTask-f46dac7fe2436c47******d71946986t0",
        "Status":"FINISH",
        "ErrCode":0,
        "Message":"",
        "InputInfo":{
            "Type":"COS",
            "CosInputInfo":{
                "Bucket":"macgzptest-125****654",
                "Region":"ap-guangzhou",
                "Object":"/dianping2.mp4"
            }
        },
        "MetaData":{
            "AudioDuration":11.261677742004395,
            "AudioStreamSet":[
                {
                    "Bitrate":127771,
                    "Codec":"aac",
                    "SamplingRate":44100
                }
            ],
            "Bitrate":2681468,
            "Container":"mov,mp4,m4a,3gp,3g2,mj2",
            "Duration":11.261677742004395,
            "Height":720,
            "Rotate":90,
            "Size":3539987,
            "VideoDuration":10.510889053344727,
            "VideoStreamSet":[
                {
                    "Bitrate":2553697,
                    "Codec":"h264",
                    "Fps":29,
                    "Height":720,
                    "Width":1280
                }
            ],
            "Width":1280
        },
        "MediaProcessResultSet":[
            {
                "Type":"Transcode",
                "TranscodeTask":{
                    "Status":"SUCCESS",
                    "ErrCode":0,
                    "Message":"SUCCESS",
                    "Input":{
                        "Definition":10,
                        "WatermarkSet":[
                            {
                                "Definition":515247,
                                "TextContent":"",
                                "SvgContent":""
                            }
                        ],
                        "OutputStorage":{
                            "Type":"COS",
                            "CosOutputStorage":{
                                "Bucket":"gztest-125****654",
                                "Region":"ap-guangzhou"
                            }
                        },
                        "OutputObjectPath":"/dasda/dianping2_transcode_10",
                        "SegmentObjectName":"/dasda/dianping2_transcode_10_{number}",
                        "ObjectNumberFormat":{
                            "InitialValue":0,
                            "Increment":1,
                            "MinLength":1,
                            "PlaceHolder":"0"
                        }
                    },
                    "Output":{
                        "OutputStorage":{
                            "Type":"COS",
                            "CosOutputStorage":{
                                "Bucket":"gztest-125****654",
                                "Region":"ap-guangzhou"
                            }
                        },
                        "Path":"/dasda/dianping2_transcode_10.mp4",
                        "Definition":10,
                        "Bitrate":293022,
                        "Height":320,
                        "Width":180,
                        "Size":401637,
                        "Duration":11.26200008392334,
                        "Container":"mov,mp4,m4a,3gp,3g2,mj2",
                        "Md5":"31dcf904c03d0cd78346a12c25c0acc9",
                        "VideoStreamSet":[
                            {
                                "Bitrate":244608,
                                "Codec":"h264",
                                "Fps":24,
                                "Height":320,
                                "Width":180
                            }
                        ],
                        "AudioStreamSet":[
                            {
                                "Bitrate":48414,
                                "Codec":"aac",
                                "SamplingRate":44100
                            }
                        ]
                    }
                },
                "AnimatedGraphicTask":null,
                "SnapshotByTimeOffsetTask":null,
                "SampleSnapshotTask":null,
                "ImageSpriteTask":null
            },
            {
                "Type":"AnimatedGraphics",
                "TranscodeTask":null,
                "AnimatedGraphicTask":{
                    "Status":"FAIL",
                    "ErrCode":30010,
                    "Message":"TencentVodPlatErr Or Unkown",
                    "Input":{
                        "Definition":20000,
                        "StartTimeOffset":0,
                        "EndTimeOffset":600,
                        "OutputStorage":{
                            "Type":"COS",
                            "CosOutputStorage":{
                                "Bucket":"gztest-125****654",
                                "Region":"ap-guangzhou"
                            }
                        },
                        "OutputObjectPath":"/dasda/dianping2_animatedGraphic_20000"
                    },
                    "Output":null
                },
                "SnapshotByTimeOffsetTask":null,
                "SampleSnapshotTask":null,
                "ImageSpriteTask":null
            },
            {
                "Type":"SnapshotByTimeOffset",
                "TranscodeTask":null,
                "AnimatedGraphicTask":null,
                "SnapshotByTimeOffsetTask":{
                    "Status":"SUCCESS",
                    "ErrCode":0,
                    "Message":"SUCCESS",
                    "Input":{
                        "Definition":10,
                        "TimeOffsetSet":[

                        ],
                        "WatermarkSet":[
                            {
                                "Definition":515247,
                                "TextContent":"",
                                "SvgContent":""
                            }
                        ],
                        "OutputStorage":{
                            "Type":"COS",
                            "CosOutputStorage":{
                                "Bucket":"gztest-125****654",
                                "Region":"ap-guangzhou"
                            }
                        },
                        "OutputObjectPath":"/dasda/dianping2_snapshotByOffset_10_{number}",
                        "ObjectNumberFormat":{
                            "InitialValue":0,
                            "Increment":1,
                            "MinLength":1,
                            "PlaceHolder":"0"
                        }
                    },
                    "Output":{
                        "Storage":{
                            "Type":"COS",
                            "CosOutputStorage":{
                                "Bucket":"gztest-125****654",
                                "Region":"ap-guangzhou"
                            }
                        },
                        "Definition":0,
                        "PicInfoSet":[
                            {
                                "TimeOffset":0,
                                "Path":"/dasda/dianping2_snapshotByOffset_10_0.jpg",
                                "WaterMarkDefinition":[
                                    515247
                                ]
                            }
                        ]
                    }
                },
                "SampleSnapshotTask":null,
                "ImageSpriteTask":null
            },
            {
                "Type":"ImageSprites",
                "TranscodeTask":null,
                "AnimatedGraphicTask":null,
                "SnapshotByTimeOffsetTask":null,
                "SampleSnapshotTask":null,
                "ImageSpriteTask":{
                    "Status":"SUCCESS",
                    "ErrCode":0,
                    "Message":"SUCCESS",
                    "Input":{
                        "Definition":10,
                        "OutputStorage":{
                            "Type":"COS",
                            "CosOutputStorage":{
                                "Bucket":"gztest-125****654",
                                "Region":"ap-guangzhou"
                            }
                        },
                        "OutputObjectPath":"/dasda/dianping2_imageSprite_10_{number}",
                        "WebVttObjectName":"/dasda/dianping2_imageSprite_10",
                        "ObjectNumberFormat":{
                            "InitialValue":0,
                            "Increment":1,
                            "MinLength":1,
                            "PlaceHolder":"0"
                        }
                    },
                    "Output":{
                        "Storage":{
                            "Type":"COS",
                            "CosOutputStorage":{
                                "Bucket":"gztest-125****654",
                                "Region":"ap-guangzhou"
                            }
                        },
                        "Definition":10,
                        "Height":80,
                        "Width":142,
                        "TotalCount":2,
                        "ImagePathSet":[
                            "/dasda/imageSprite/dianping2_imageSprite_10_0.jpg"
                        ],
                        "WebVttPath":"/dasda/imageSprite/dianping2_imageSprite_10.vtt"
                    }
                }
            }
        ]
    }
}
```

<!--For more information on structures and fields in event notification messages, please see [API Documentation - Data Structure]().-->
