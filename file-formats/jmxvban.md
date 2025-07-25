---
hidden: true
---

# JMXVBAN

Contains the keyframes transformations (translation, rotation) to animate a skeleton.

{% tabs %}
{% tab title="File Structure" %}
<pre class="language-csharp"><code class="lang-csharp"><strong>12  string  Signature           //JMXVBAN 0102
</strong>4   int     unkInt0             // Introduced in 0102, 0 in all files
4   int     unkInt1             // Introduced in 0102, 0 in all files
4   int     Name.Length
*   string  Name
4   int     Duration            // in ms
4   int     FPS                 // Frames per second
4   int     IsCyclic

// Keyframe timings, so you can interpolate between two poses
4   uint    KeyframeCount
foreach (KeyframeCount)
{
    4   uint    Time            // in ms
}

4   uint    AnimatedBoneCount
foreach(AnimatedBoneCount)
{
    // AnimatedBone
    4   uint    Name.Length
    *   string  Name
    4   uint    TransformationCount // Linked to the KeyframeCount
    foreach(TransformationCount)
    {
        // Transformation matrix relative to the parent bone/joint
        16  Quaternion  Rotation
        12  Vector3     Translation
    }
}
</code></pre>
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

struct Transformation
{
    Quaternion Rotation;
    Vector3 Translation;
};

struct AnimatedBone
{
    u32 NameLength;
    char Name[NameLength];
    u32 TransformationCount;
    Transformation Transformations[TransformationCount];
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
    u32 KeyframeCount;
    u32 Keyframes[KeyframeCount];
    u32 AnimatedBoneCount;
    AnimatedBone AnimatedBones[AnimatedBoneCount];
};

JMXVBAN file @ 0;
```
{% endtab %}
{% endtabs %}
