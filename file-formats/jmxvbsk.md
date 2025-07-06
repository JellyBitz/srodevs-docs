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

# JMXVBSK

Contains the bone hierarchy to form a skeleton used for rigging process of the model.

{% tabs %}
{% tab title="File Structure" %}
```csharp
//CPrimBranch : CPrim, IPrim
12  string  Signature               //JMXVBSK 0101
4   uint    SubPrimCount            // Number of bones
foreach(SubPrimCount)
{
    //CPrimBone : CPrimNode, CSubPrim
    // BoneData
    1   byte    Type            // 0 = CPrimBone, 1 = CPrimDummy
    4   uint    Name.Length 
    *   string  Name
    4   uint    ParentName.Length
    *   string  ParentName

    // Transformation relative to parent bone
    16  Quaternion  RotationToParent
    12  Vector3     TranslationToParent
    
    // Transformation relative to world origin
    16  Quaternion  RotationToOrigin
    12  Vector3     TranslationToOrigin
    
    // Transformation relative to local armature
    16  Quaternion  RotationToLocal
    12  Vector3     TranslationToLocal
    
    4   uint    ChildBoneCount
    foreach(ChildBoneCount)
    {
        // ChildBone
        4   uint    Name.Length
        *   string  Name
    }    
}
4   uint    unkUInt0    //ASSERT(nCount == 0)?
4   uint    unkUInt1    //ASSERT(nCount == 0)?
```
{% endtab %}

{% tab title="ImHex" %}
```c
#pragma array_limit 4294967296
#pragma pattern_limit 4294967296

enum BoneType : u8
{
    CPrimBone = 0,
    CPrimDummy = 1
};

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

struct ChildBone
{
    u32 NameLength;
    char Name[NameLength];
};

struct Bone
{
    BoneType Type;
    u32 NameLength;
    char Name[NameLength];
    u32 ParentNameLength;
    char ParentName[ParentNameLength];
    Quaternion RotationFromParent;
    Vector3 TranslationFromParent;
    Quaternion RotationFromOrigin;
    Vector3 TranslationFromOrigin;
    Quaternion RotationFromLocalArmature;
    Vector3 TranslationFromLocalArmature;
    u32 ChildBoneCount;
    ChildBone Children[ChildBoneCount];
};

struct JMXVBSK
{
    char Signature[12];
    u32 BoneCount;
    Bone Bones[BoneCount];
    u32 unkInt0;
    u32 unkInt1;
};

JMXVBSK file @ 0;
```
{% endtab %}
{% endtabs %}
