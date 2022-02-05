# arc-spec README #

ARCs are stored in the WOS in an object file format, where each ARC is a complete object defined by a collection of files.

An ARC can be many things:  
 
Spatial audio clip
Collection of audio clips in relative position to each other
Image
Video
Image dragged by a dinosaur
Collection of audio clips that play when near them with visible directional hints
A birthday cake with spatial audio coming from it

The object format begins with the index.json file, which is a declarative JSON file that references the other files in the ARC and includes metadata:

Name, description
Owner
Permissions and privacy
3D Transform

Files can be media, html divs, Javascript, and ARC files.  The top level index.json file is structured to be indexed, includes pinning information for the overall ARC, and 3D transform to orient the object.  Supported file formats include:

Jpeg, png, gif
Mpeg, mp4
HTML div files
ARC files 

ARC files can define complex objects, including multiple objects, moving objects, multiple objects pinned to many locations, and interactivity.

The index.json file can refer directly to media or can refer to a separate render format file. For example the index.json file could reference an image, audio file, or could reference a Questori Quest file to render a Quest.  It could refer to an HTML file to render HTML into space.

## Example ##
Spatial audio ARC
https://ipfs.io/ipfs/QmXN8whBDCKTDcPUBb5VJ1QjbcfJv7uGenQ7jFFoM6qxSv

```Console
/index.json
/media
/media/hello.mp3
/media/example-cover-image.jpg
```

Index.json - entrypoint to the object
```json
{
  "apiVersion": "v1",
  "metadata": {
    "name": "example-mp4",
    "createdAt": "2021-12-15T01:01:01Z",
    "description": "example simple audio mp4",
    "privacy" : "public",
    "visibility": "visible",
    "fidelity": [
      "phone",
      "earbuds"
    ]
  },
  "kind": "arc",
  "spec": {
    "coverImageUri": "/media/example-cover-image.jpg",
    "representation": [{
      "profile": "audio",
      "mimeType": "audio/mp4",
      "uri": "/media/hello.mp3"
    }]
  }
}
```








