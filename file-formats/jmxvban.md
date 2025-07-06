---
hidden: true
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# JMXVBAN

{% tabs %}
{% tab title="File Structure" %}
```csharp
12  string  Signature           //JMXVBAN 0102
4   int     unkInt0             // Introduced in 0102, 0 in all files
4   int     unkInt1             // Introduced in 0102, 0 in all files
4   int     Name.Length
*   string  Name
4   int     Duration            // in ms
4   int     FPS                 // Frames per second
4   int     IsCyclic

// Keyframe timings, so you can interpolate between two poses
4   uint    KeyframeTimesCount
foreach(KeyframeTime)
{
    4   uint    KeyframeTime    // in ms
}

// Bones with transformations
4   uint    AnimatedBoneCount
foreach(AnimatedBone)
{
    4   uint    AnimatedBoneName.Length
    *   string  AnimatedBoneName
    4   uint    AnimatedKeyframeCount
    foreach(AnimatedKeyframe)
    {
        // These two together give you the transformation matrix relative to it's parent bone/joint
        16  Quaternion  AnimatedKeyframe.Rotation
        12  Vector3     AnimatedKeyframe.Translation
    }
}
```
{% endtab %}

{% tab title="ImHex" %}
```c
#pragma array_limit 4294967296
#pragma pattern_limit 4294967296

struct Quaternion
{
    float X;
    float Y;
    float Z;
    float W;
};

struct Vector3
{
    float X;
    float Y;
    float Z;
};

struct Keyframe
{
    Quaternion Rotation;
    Vector3 Translation;
};

struct AnimatedBone
{
    u32 BoneNameLength;
    char BoneName[BoneNameLength];
    u32 KeyframesCount;
    Keyframe Keyframes[KeyframesCount];
};

struct JMXVBAN
{
    char Signature[12];
    u32 unkInt0;
    u32 unkInt1;
    u32 NameLength;
    char Name[NameLength];
    u32 Duration;
    u32 FPS;
    u32 IsCyclic;
    u32 KeyframeTimesCount;
    u32 KeyframeTimes[KeyframeTimesCount];
    u32 AnimatedBonesCount;
    AnimatedBone AnimatedBones[AnimatedBonesCount];
};

JMXVBAN file @ 0;
```
{% endtab %}
{% endtabs %}
