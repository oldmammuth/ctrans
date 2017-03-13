# ctrans -- Coordinates Tranformation Tool
Little python script that transforms a geographical coordinate to a web slippy map's tile reference.

## Usage
```crans -h``` gets you a nice but maybe confusing help.

Here's the short and long of it.

### Get Geographic Coordinates Given a Web Map Tile
Web map tiles come in the form of a path /{Z}/{X}/{Y}.{ext}, where:

- Z = zoom level,
- X and Y = tile coordinates for that particular zoom
- (ext is a image file extension that we don't need to know to transform coordinates)

Thus, if we want to obtain the geographic longlat coordinates of that tile, we'll run *ctrans* this way:

``` bash
$ ./ctrans t2l <X> <Y>
```
**Important**: The coordinate given are those corresponding to the NW point of the tile


#### Some Options:

- ```-c, --centertile```: This nice option gets you the longitude and latitude at the tile's center point. The default behavior is in fact to give you the NW point (which is useful to get also the surrounding tiles)
- ```-z, --zoom```: Sets the Zoom level; **if not present the zoom level considered is 12**
- ```-v, --verbose```: Gets you the answer in a more discoursive way than just pure numbers... If you are into that chitchat (and chatbots) stuff...

#### Example:
``` bash
./ctrans t2l -cv -z 13 4376 2932
```
### Get a Web Map Tile Given the Geographic Coordinates 
So I have a long lat reference of a point on earth, and I want to know the path for a Web Map

``` bash
$ ./ctrans l2t <longitude> <latitude>
```

#### Some Options:

- ```-z, --zoom```: Sets the Zoom level; **if not present the zoom level considered is 12**
- ```-v, --verbose```: Here too you can Getthe answer in a more discoursive way, but it gets more useful, since you obtain a web map path to copy-paste...

#### Example:
``` bash
./ctrans l2t -v -z 13 12.326660 45.444717
```

## Author and License Notice
Assembled by Davide 'oldmammuth' Del Papa

Based on functions found at:
https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames#Python

Hope you enjoy it.