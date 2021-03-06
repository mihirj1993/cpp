# ([C++](Cpp.md)) [AddColoredNoise](CppAddColoredNoise.md)

[AddColoredNoise](CppAddColoredNoise.md) is a [VCL
graphics](CppVclGraphics.md) [code snippet](CppVclCodeSnippets.md) to
add colored noise to a [Extctrls::TImage](CppTImage.md).

![AddColoredNoise example (png)](CppAddColoredNoise.png)

```c++
#include <cassert>
#include <cstdlib>
#include <Extctrls.hpp>

//Adds colored noise in range [0,max_rand>
// * max_rand =   0 denotes no noise added (image untouched)
// * max_rand = 255 denotes max noise added (image unrecognizable)
//From http://www.richelbilderbeek.nl/CppAddColoredNoise.htm
void AddColoredNoise(
  const Extctrls::TImage * const source,
  const int max_rand,
  Extctrls::TImage * const target)
{
  assert(max_rand >=   0);
  assert(max_rand  < 256);
  assert(source!=0 && "Image is NULL");
  assert(source->Picture->Bitmap!=0 && "Image bitmap is NULL");
  assert(source->Picture->Bitmap->PixelFormat == pf24bit && "Image bitmap must be 24 bit");
  assert(target!=0 && "Image is NULL");
  assert(target->Picture->Bitmap!=0 && "Image bitmap is NULL");
  assert(target->Picture->Bitmap->PixelFormat == pf24bit && "Image bitmap must be 24 bit");
  //Get the width and height from the source
  const int width  = source->Picture->Bitmap->Width;
  const int height = source->Picture->Bitmap->Height;
  //Set the target's width and height
  target->Picture->Bitmap->Width  = width;
  target->Picture->Bitmap->Height = height;

  for (int y=0; y!=height; ++y)
  {
    const unsigned char * lineSource
      = static_cast<const unsigned char *>(
        source->Picture->Bitmap->ScanLine[y]);
    unsigned char * lineTarget
      = static_cast<unsigned char *>(
        target->Picture->Bitmap->ScanLine[y]);
    for (int x=0; x!=width; ++x)
    {
      const int rand = std::rand() % max_rand;
      const int blue  = (static_cast<int>(lineSource[x*3+0]) + rand) % 256;
      const int green = (static_cast<int>(lineSource[x*3+1]) + rand) % 256;
      const int red   = (static_cast<int>(lineSource[x*3+2]) + rand) % 256;
      assert(red   >=   0);
      assert(red    < 256);
      assert(green >=   0);
      assert(green  < 256);
      assert(blue  >=   0);
      assert(blue   < 256);
      lineTarget[x*3+0]=blue; //Blue
      lineTarget[x*3+1]=green; //Green
      lineTarget[x*3+2]=red; //Red
    }
  }
}
```