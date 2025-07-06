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

{% tabs %}
{% tab title="File Structure" %}
```csharp
//CPrimBranch : CPrim, IPrim
12  string  Signature               //JMXVBSK 0101
4   uint    SubPrimCount            // Number of bones
for (int i = 0; i < SubPrimCount; i++)
{
    //CPrimBone : CPrimNode, CSubPrim
    // BoneData
    1   byte    BoneType            // 0 = CPrimBone, 1 = CPrimDummy
    4   uint    BoneName.Length 
    *   string  BoneName
    4   uint    ParentBoneName.Length
    *   string  ParentBoneName

    // Transform relative to parent bone
    16  Quaternion  RotationToParent
    12  Vector3     TranslationToParent
    
    // Transform relative to world origin
    16  Quaternion  RotationToOrigin
    12  Vector3     TranslationToOrigin
    
    // Transform relative to local armature
    16  Quaternion  RotationToLocal
    12  Vector3     TranslationToLocal
    
    4   uint    ChildBoneCount
    for (int j = 0; j < ChildBoneCount; j++)
    {
        4   uint    ChildBoneName.Length
        *   string  ChildBoneName
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
    u32 ChildBonesCount;
    ChildBone Children[ChildBonesCount];
};

struct JMXVBSK
{
    char Signature[12];
    u32 BoneCount;
    Bone Bones[BoneCount];
};

JMXVBSK file @ 0;
```
{% endtab %}
{% endtabs %}
