English| [简体中文](./README_cn.md)

# video codec Usage Instructions

## Program Functions

`sample_vdec_basic` implements basic decoding functionality, reading local H264/H265/MJPEG files, decoding and saving the results in NV12 format.

`sample_venc_basic` implements basic encoding functionality, reading NV12 images, encoding them as H264 (or H265 or MJPEG), and saving them as local files.

`sample_vdec_two_channel` is designed for scenarios that require simultaneous decoding of multiple channels. Based on `sample_vdec_basic`, it adds a decoding channel to achieve dual-channel decoding. It reads local H264/H265/MJPEG files, decodes them in two channels simultaneously, and saves NV12 files separately.

`sample_venc_two_channel` is designed for scenarios that require simultaneous encoding of multiple channels. Based on `sample_venc_basic`, it adds an encoding channel to achieve dual-channel encoding. It reads local NV12 files, encodes them in two channels simultaneously, and saves them as H264 (or H265 or MJPEG) files.

### Program Deployment

#### sample_vdec_basic

After uploading the compiled `sample_vdec_basic` and the files to be decoded to the development board, grant executable permission to the program by `chmod a+x sample_vdec_basic`. Then run the program by `./sample_vdec_basic -w width -h height -t encode_type -f file`.

Where:
- `width` represents the number of pixels included in the width of the image.
- `height` represents the pixel format included in the height of the image.
- `encode_type` can be h264, h265, or mjpeg.
- `file` is the name of the file to be decoded.

#### sample_venc_basic

After uploading the compiled `sample_venc_basic` and the files to be decoded to the development board, grant executable permission to the program by `chmod a+x sample_venc_basic`. Then run the program by `./sample_venc_basic -w width -h height -t encode_type -f file0 -g file1`.

Where:
- `width` represents the number of pixels included in the width of the image.
- `height` represents the pixel format included in the height of the image.
- `encode_type` can be h264, h265, or mjpeg.
- `file0` is the name of the file to be encoded in NV12 format.
- `file1` is the name of the file to be encoded in NV12 format, with the same width and height as `file0`.

#### sample_vdec_two_channel

After uploading the compiled `sample_vdec_two_channel` and the files to be decoded to the development board, grant executable permission to the program by `chmod a+x sample_vdec_two_channel`. Then run the program by `./sample_vdec_two_channel -w width -h height -t encode_type -f file`.

Where:
- `width` represents the number of pixels included in the width of the image.
- `height` represents the pixel format included in the height of the image.
- `encode_type` can be h264, h265, or mjpeg.### sample_venc_two_channel

After uploading the compiled `sample_venc_two_channel` and the file to be decoded to the development board, give the program executable permission by `chmod a+x sample_venc_two_channel`, and then execute the program as `./sample_venc_two_channel -w width -h height -t encode_type -f file0 -g file1`.

Where `width` represents the number of pixels in the image width.

`height` represents the pixel format contained in the image height.

`encode_type` can be h264\h265\mjpeg.

`file0` is the file name to be encoded, which needs to be in NV12 format.

`file1` is the file name to be encoded, also in NV12 format, and its width and height need to be the same as those of `file0`.

### Execution Results Description

#### sample_vdec_basic

The `decode.nv12` file is generated in the current running directory, and its content is updated along with the decoding content.

#### sample_venc_basic

The `sample_venc.h264`, `sample_venc.h265`, and `sample_venc.jpg` files are generated in the current running directory. The H264/H265 files show alternating content from `file1` and `file2`.

#### sample_vdec_two_channel

The `sample_decode_ch0.nv12` and `sample_decode_ch1.nv12` files are generated in the current running directory, and their content is updated along with the decoding content.

#### sample_venc_two_channel

The `sample_venc_ch0.h264` (`sample_venc_ch0.h265`/`sample_venc_ch0.jpg`) and `sample_venc_ch1.h264` (`sample_venc_ch1.h265`/`sample_venc_ch1.jpg`) files are generated in the current running directory. The H264/H265 files show alternating content from `file1` and `file2`.

## Compilation

Execute the `make` command in the SDK to compile.