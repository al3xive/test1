---
title: Starting Transcoding Process with Custom Params
position: 7
request: /v1/start_encode2
main_message: This method runs transcoding of an uploaded file applying custom settings to it. Use this method in case you need a refined control over the transcoding process.<br> Check Description of query object properties
attributes:
  - attribute: task_token
    required: required
    message: Task token returned with <b style="color:#41c186;">create_task</b> method.
  - attribute: query
    required: required
    message: JSON object containing the details of transcoding procedure. See examples and description of query's properties below.
  - attribute: profiles
    required: optional
    message: Any string with length of 1000 characters (max).<br> It might become handy if you need to pass your website's ID or any JSON object.<br><h2>Query's properties description:</h2><br> 
  - attribute: source | stitch
    required: required
    message: Either <span class="q6-blue-text">source</span> or <span class="q6-blue-text">stitch</span> param should be specified.<br> The <span class="q6-blue-text">source</span> is responsible for defining a single video's URI, whether it's an http(s) URL or tus URI returned with <b style="color:#41c186;">upload_file</b> method.<br> Use the <span class="q6-blue-text">stitch</span> param in order to combine several input videos into a single one. Stitch should be a json-list of URLs or video-objects. Specify <span class="q6-blue-text">start_time</span> and <span class="q6-blue-text">duration</span> while using an object form. Check the examples below.<br><code>["https://youserver.com/video1.mp4"<br>"https://youserver.com/video1.mp4",<br>"https://youserver.com/video2.mkv",<br>{"url":"https://yourserver.com/video3.mp4", "start_time":"100.0", "duration":"60.0"}]</code><br> The same video URL can be specified several times in a stitch array (e.g. to stitch different clips from the same video). In this case the original video will be downloaded only at once.
  - attribute: format
    required: required
    message: A list of objects, each describing params for a single output video stream (MP4, WEBM, HLS or MPEG-DASH).
  - attribute: output
    required: optional
    message: Output video format. Currently supported values are <b>mp4</b>, <b>webm</b>, <b>advanced_hls</b>, <b>advanced_dash</b>.<br> The <b>thumbnail</b> & <b>thumbnails</b> values are used for creation of thumbnail images. See the Create thumbnails section for more details.
  - attribute: destination
    required: required
    message: URI to store output video in. In case this value is not specified, video will be temporarily stored on the Qencode's servers.<br> For Amazon S3 use the following URL format:<br><code>s3://access_id:access_secret@s3.amazonaws.com<br>[:port]/bucket_name/path</code><br> For custom S3 server just specify your hostname:<br><code>s3://access_id:access_secret@example.com<br>[:port]/bucket_name/path</code><br> For Aspera:<br><code>fasp://access_id:access_secret@example.com[:tcp_port][:udp_port]/path</code><br> For FTP:<br><code>ftp://access_id:access_secret@example.com[:port]/path</code><br><br> It is highly recommended to you specify destination as a JSON object with the following structure:<br><br>S3<br><code>{<br>"url":“s3://example.com/bucket/video.mp4”,<br>"key":"your_access_key",<br>"secret":"your_access_secret",<br>"permissions":"public-read", //optional field [*]<br>"storage_class":"REDUCED_REDUNDANCY"//optional field [**]<br>}</code><br><br>FTP<br><code>{<br>"url":“ftp://example.com:[port]/folder/video.mp4”,<br>"key":"user",<br>"secret":"password",<br>"is_passive":"true/false",<br>"use_tls":"true/false"<br>}</code><br><br>Aspera<br><code>{<br>"url":“fasp://example.com/folder/video.mp4”,<br>"key":"user",<br>"secret":"password",<br>"tcp_port":"port",<br>"udp_port":"port"<br>}</code><br><br>Please make sure a video file name (for MP4/WEBM) or a folder (for HLS/MPEG-DASH) is included in path. Check the <a href="https://docs.aws.amazon.com/AmazonS3/latest/user-guide/set-permissions.html" target="_blank">Bucket/Object Permissions</a> & <a href="https://aws.amazon.com/s3/reduced-redundancy/" target="_blank">Reduced Redundancy Storage</a> for more information.
  - attribute: file_extension
    required: required
    message: Output video file extension (only for MP4 format, defaults to '.mp4').
  - attribute: size
    required: required
    message: Output video frame size in pixels ("width"x"height"). Defaults to original frame size.
  - attribute: rotate
    required: required
    message: Rotate video through specified degrees value. Possible values are 90, 180, 270.
  - attribute: framerate
    required: required
    message: Output video frame rate. Defaults to original frame rate.
  - attribute: bitrate
    required: required
    message: Output video stream bitrate in kylobytes. Defaults is up to 512. Please note, don't specify bitrate unless you want constant bitrate for the video. To create variable bitrate use quality param.
  - attribute: quality
    required: required
    message: Output video stream quality (aka Constant rate factor). Use this param to produce optimized videos with variable bitrate. For H.264 the range is 0-51, where 0 is lossless and 51 is worst possible. A lower value is a higher quality and a subjectively sane range is 18-28. Consider 18 to be visually lossless. It should look the same or nearly the same as the input but it isn't technically lossless.
  - attribute: pix_format
    required: required
    message: Output video pixel format. Possible values are yuv420p, yuv422p, yuvj420p, yuvj422p. Defaults to yuv420p.
  - attribute: profile
    required: required
    message: x264 video codec settings profile. Possible values are high, main, baseline. Defaults to main.
  - attribute: video_codec
    required: required
    message: Output stream video codec. Defaults to libx264. Possible values are libx264, libx265, libvpx, libvpx-vp9.
  - attribute: video_codec_parameters
    required: required
    message: Output stream video codec <a href="https://www.ffmpeg.org/ffmpeg-all.html" target="_blank">parameters</a>.<br><br><h4>Video_Codec_Parameters Description:</h4> 
  - attribute: vprofile
    required: required
    message: x264 video codec settings profile. Possible values are high, main, baseline. Main is default.
  - attribute: level
    required: required
    message: Set of constraints that indicate a degree of required decoder performance for a profile.
  - attribute: coder
    required: required
    message: Context-Adaptive Binary Arithmetic Coding (CABAC) is the default entropy encoder used by x264. Possible values are 1 and 0. Default is 1.
  - attribute: flags2
    required: required
    message: Allows B-frames to be kept as references. Possible values are +bpyramid, +wpred, +mixed_refs, +dct8×8, -fastpskip/+fastpskip, +aud Default is None.
  - attribute: partitions
    required: required
    message: One of x264's most useful features is the ability to choose among many combinations of inter and intra partitions. Possible values are +partp8x8, +partp4x4, +partb8x8, +parti8x8, +parti4x4. Default is None.
  - attribute: directpred
    required: required
    message: Defines motion detection type, 0 -- none, 1 -- spatial, 2 -- temporal, 3 -- auto. Default is 1.
  - attribute: me_method
    required: required
    message: Motion Estimation method used in encoding. Possible values are epzs, hex, umh, full. Default is None.
  - attribute: subq
    required: required
    message: Set sub pel motion estimation quality
  - attribute: trellis
    required: required
    message: Set rate-distortion optimal quantization
  - attribute: refs
    required: required
    message: Number of reference frames each P-frame can use. The range is from 0-16
  - attribute: cmp
    required: required
    message: Set full pel me compare function.
  - attribute: me_range
    required: required
    message: Set limit motion vectors range (1023 for DivX player)
  - attribute: sc_threshold
    required: required
    message: Set scene change threshold.
  - attribute: i_qfactor
    required: required
    message: Set QP factor between P and I frames
  - attribute: b_strategy
    required: required
    message: Set strategy to choose between I/P/B-frames.
  - attribute: qcomp
    required: required
    message: Set video quantizer scale compression (VBR). It is used as a constant in the ratecontrol equation. Recommended default range rc_eq is 0.0-1.0.
  - attribute: qmin
    required: required
    message: Set min video quantizer scale (VBR). Must be included between -1 and 69, default value is 2.
  - attribute: qmax
    required: required
    message: Set max video quantizer scale (VBR). Must be included between -1 and 1024, default value is 31.
  - attribute: qdiff
    required: required
    message: Set max difference between the quantizer scale (VBR).
  - attribute: max_rate
    required: required
    message: Set max bitrate tolerance (in bits/s). Requires bufsize to be set.
  - attribute: min_rate
    required: required
    message: Set min bitrate tolerance (in bits/s). CBR encode is recommended.
  - attribute: sws_flags
    required: required
    message: Set the scaler flags. This is also used to set the scaling algorithm. Only a single algorithm should be selected. Default value is ‘bicubic’.
  - attribute: preset
    required: required
    message: Specify the preset for matching stream(s).
  - attribute: flags
    required: required
    message: Set generic flags. (Possible values ‘mv4’, ‘qpel’, ‘loop’, ‘qscale’, ‘pass1’, ‘pass2’, ‘gray’, ‘emu_edge’, ‘psnr’, ‘truncated’, ‘ildct’, ‘low_delay’, ‘global_header’, ‘bitexact’, ‘aic’, ‘cbp’, ‘qprd’, ‘ilme’, ‘cgop’)
  - attribute: rc_lookahead
    required: required
    message: Set number of frames to look ahead for frametype and ratecontrol.
  - attribute: audio_codec
    required: required
    message: Output file audio codec name. Possible values are aac, vorbis. Defaults to aac.
  - attribute: audio_bitrate
    required: required
    message: Output file audio bitrate value in kylobytes. Defaults to 64.
  - attribute: audio_sample_rate
    required: required
    message: Output file audio sample rate. Defaults to 44100.
  - attribute: audio_channels_number
    required: required
    message: Output file audio channels number. Default value is 2.
  - attribute: segment_duration
    required: required
    message: Segment duration to split media (in seconds). Defaults to 8.
  - attribute: stream
    required: required
    message: Contains a list of elements each describing a single view stream for HLS or MPEG-DASH format.
  - attribute: keyframe
    required: required
    message: Keyframe period (in frames). Defaults to 90.
  - attribute: start_time
    required: required
    message: Specifies the start time (in seconds) in input video to begin transcoding from.
  - attribute: duration
    required: required
    message: Specifies duration of the video fragment (in seconds) to be transcoded.
  - attribute: two_pass
    required: required
    message: Use two-pass encoding to achieve the exact bitrate value for an output. Please note, that two-pass encoding is two times slower than the one-pass coding. The price to be twice higher.

json_example:
    title: Example of JSON object for query param
    json: |2-
      {
        "query": {
            "source": "https://example.com/myvideo.mp4",
            "format": [
            {
                "output": "mp4",
                "destination": "",
                "file_extension": "mp4",
                "size": "320x240",
                "rotate": "90",
                "framerate": "25",
                "bitrate": "300",
                "pix_format": "yuv420p",
                "profile": "main",
                "video_codec_parameters": {
                "vprofile": "baseline",
                "level": "31",
                "coder": "0",
                "flags2": "-bpyramid+fastpskip-dct8x8",
                "partitions": "+parti8x8+parti4x4+partp8x8+partb8x8",
                "directpred": "2",
                "me_method": "hex"
                },
                "audio_bitrate": "64",
                "audio_sample_rate": "44100",
                "audio_channels_number": "2"
            },
            {
                "output": "advanced_hls",
                "destination": "",
                "segment_duration": "4",
                "stream": [
                {
                    "size": "320x240",
                    "rotate": "180",
                    "framerate": "30",
                    "bitrate": "300",
                    "pix_format": "yuv420p",
                    "profile": "main",
                    "video_codec_parameters": {
                    "vprofile": "baseline",
                    "level": "31",
                    "coder": "0",
                    "flags2": "-bpyramid+fastpskip-dct8x8",
                    "partitions": "+parti8x8+parti4x4+partp8x8+partb8x8",
                    "directpred": "2",
                    "me_method": "hex"
                    },
                    "audio_bitrate": "64",
                    "audio_sample_rate": "44100",
                    "audio_channels_number": "2"
                },
                {
                    "size": "160x120",
                    "bitrate": "150",
                    "keyframe": "60",
                    "profile": "main"
                }
                ]
            }
            ]
        }
      }    

request_examples:
  - code_block: |2-
      curl https://api.qencode.com/v1/start_encode2 \
         -d task_token=b49e034d198262f1d5d15ed9f3cb8ee1 \
         -d payload="12345" \
         -d query='{"query": {
         "source": "https://qa.qencode.com/static/test_mini.mp4",
         "format": [
           {
             "output": "mp4",
             "destination": {
               "url":"s3://nyc3.digitaloceanspaces.com/qencode3/test/test_mini.mp4",
               "key":"abcde12345",
               "secret":"abcde12345",
               "permissions": "public-read"
             },
                   "framerate": "29.97",
                   "keyframe": "25",
                   "file_extension": "mp4",
                   "size": "360x240",
                   "video_codec_parameters": {
                     "vprofile": "baseline",
                     "level": "31",
                     "coder": "0",
                     "flags2": "-bpyramid+fastpskip-dct8x8",
                     "partitions": "+parti8x8+parti4x4+partp8x8+partb8x8",
                     "directpred": "2",
                     "me_method": "hex"
                   },
                   "start_time": "10",
                   "duration": "20",
                   "audio_bitrate": "64",
                   "audio_sample_rate": "44100",
                   "audio_channels_number": "2"
                 }
               ]
             }
            }

    language: curl

response_examples:
  - code_block: |-
      {"error":0,"status_url":"https:\/\/api.qencode.com\/v1\/status"}

    language: json
---