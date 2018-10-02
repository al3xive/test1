---
title: Getting Transcoding Task Status
position: 16
request: /v1/create_token
main_message: This route is for inquiring a transcoding task status.

request_examples:
  - code_block: |2-
      "format": curl https://api.qencode.com/v1/status -d task_tokens=63adfb01d408081b10440682f3a64114

    language: curl

  - code_block: |2-
      curl https://master-79109168ae0711e8b00baa831f35b3f7.qencode.com/v1/status -d task_tokens=d4936f71a242d4b61d790efa217ff9d5

    language: curl

response_examples:
  - code_block: |2-
      {"error":0,"statuses":{"d4936f71a242d4b61d790efa217ff9d5":{"status":"downloading","percent":0,"error":0,"error_description":null,"images":[],"videos":[],"status_url":"https:\/\/master-79109168ae0711e8b00baa831f35b3f7.qencode.com\/v1\/status"}}}

    language: json
  - code_block: |2-
      {"statuses": {"d4936f71a242d4b61d790efa217ff9d5": {"images": [], "status": "encoding", "percent": 8.3743842364532011, "videos": [], "error": 0}}, "error": 0}

      {"statuses": {"d4936f71a242d4b61d790efa217ff9d5": {"images": [], "status": "encoding", "percent": 68.965517241379317, "videos": [{"profile": "5a2a846a26e88", "url": "https://nyc3.digitaloceanspaces.com/qencode3/videos/240/498afa68af0711e8b9c60a443ab347fd.mp4", "tag": "video-0-0", "storage": {"format": "mp4", "bucket": "qencode3", "host": "nyc3.digitaloceanspaces.com", "key": "videos/240/498afa68af0711e8b9c60a443ab347fd.mp4", "scheme": "https", "type": "custom_s3", "port": null}, "user_tag": "240p"}], "error": 0}}, "error": 0}

      {"images": [], "status": "completed", "percent": 100.0, "videos": [{"profile": "5a2a846a26e88", "url": "https://nyc3.digitaloceanspaces.com/qencode3/videos/240/498afa68af0711e8b9c60a443ab347fd.mp4", "tag": "video-0-0", "storage": {"format": "mp4", "bucket": "qencode3", "host": "nyc3.digitaloceanspaces.com", "key": "videos/240/498afa68af0711e8b9c60a443ab347fd.mp4", "scheme": "https", "type": "custom_s3", "port": null}, "user_tag": "240p"}, {"profile": "5a2a846a26e88", "url": "https://nyc3.digitaloceanspaces.com/qencode3/videos/720/498afa68af0711e8b9c60a443ab347fd.mp4", "tag": "video-2-0", "storage": {"format": "mp4", "bucket": "qencode3", "host": "nyc3.digitaloceanspaces.com", "key": "videos/720/498afa68af0711e8b9c60a443ab347fd.mp4", "scheme": "https", "type": "custom_s3", "port": null}, "user_tag": "720p"}, {"profile": "5a2a846a26e88", "url": "https://nyc3.digitaloceanspaces.com/qencode3/output/360/498afa68af0711e8b9c60a443ab347fd.mp4", "tag": "video-4-0", "storage": {"format": "mp4", "bucket": "qencode3", "host": "nyc3.digitaloceanspaces.com", "key": "output/360/498afa68af0711e8b9c60a443ab347fd.mp4", "scheme": "https", "type": "custom_s3", "port": null}, "user_tag": "360p"}, {"profile": "5a2a846a28604", "url": "https://nyc3.digitaloceanspaces.com/qencode3/hls/498afa68af0711e8b9c60a443ab347fd/playlist.m3u8", "tag": "video-5-1", "storage": {"format": "hls", "bucket": "qencode3", "host": "nyc3.digitaloceanspaces.com", "key": "/hls/498afa68af0711e8b9c60a443ab347fd", "scheme": "https", "type": "custom_s3", "port": null}, "user_tag": "360p"}, {"profile": "5a2a846a28604", "url": "https://nyc3.digitaloceanspaces.com/qencode3/hls/498afa68af0711e8b9c60a443ab347fd/playlist.m3u8", "tag": "video-5-0", "storage": {"format": "hls", "bucket": "qencode3", "host": "nyc3.digitaloceanspaces.com", "key": "/hls/498afa68af0711e8b9c60a443ab347fd", "scheme": "https", "type": "custom_s3", "port": null}, "user_tag": "240p"}, {"profile": "5a2a846a26e88", "url": "https://nyc3.digitaloceanspaces.com/qencode3/output/480/498afa68af0711e8b9c60a443ab347fd.mp4", "tag": "video-3-0", "storage": {"format": "mp4", "bucket": "qencode3", "host": "nyc3.digitaloceanspaces.com", "key": "output/480/498afa68af0711e8b9c60a443ab347fd.mp4", "scheme": "https", "type": "custom_s3", "port": null}, "user_tag": "480p"}, {"profile": "5a2a846a26e88", "url": "https://nyc3.digitaloceanspaces.com/qencode3/videos/1080/498afa68af0711e8b9c60a443ab347fd.mp4", "tag": "video-1-0", "storage": {"format": "mp4", "bucket": "qencode3", "host": "nyc3.digitaloceanspaces.com", "key": "videos/1080/498afa68af0711e8b9c60a443ab347fd.mp4", "scheme": "https", "type": "custom_s3", "port": null}, "user_tag": "1080p"}], "error": 0}}, "error": 0}

    language: json
---