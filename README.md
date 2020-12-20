# SkyrimSE_Research

```cpp

struct PlayerInstance
{
	char pad_0000[224]; //0x0000
	char *entityName; //0x00E0
	char pad_00E8[800]; //0x00E8
}; //Size: 0x0408


struct BoneArray
{
	vec3 Location; //0x0000
	char pad_000C[20]; //0x000C
	char *boneName; //0x0020
	char pad_0028[88]; //0x0028
}; //Size: 0x0080


struct XModelBone_t
{
	char pad_0000[120]; //0x0000
	char *humanValid; //0x0078
	char pad_0080[88]; //0x0080
	struct BoneArray bone[200];
//	char pad_0100[131916]; //0x0100
}; //Size: 0x20440

struct XModelCache_t
{
	char pad_0000[16]; //0x0000
	char *rootTree; //0x0010
	char pad_0018[280]; //0x0018
	struct XModelBone_t *XModelBone; //0x0130
	char pad_0138[208]; //0x0138
}; //Size: 0x0208


struct Itmes_t
{
	char pad_0000[56]; //0x0000
	char *Name; //0x0038
	char pad_0040[4552]; //0x0040
}; //Size: 0x1208

struct Character_t
{
	struct Itmes_t *Helmet; //0x0088
	char pad_0090[112]; //0x0090
	struct Itmes_t *Chest; //0x0100
	char pad_0108[112]; //0x0108
	struct Itmes_t *Gauntlets; //0x0178
	char pad_0180[352]; //0x0180
	struct Itmes_t *Ring; //0x02E0
	char pad_02E8[112]; //0x02E8
	struct Itmes_t *Boots; //0x0358
	char pad_0360[232]; //0x0360
	struct Itmes_t *Shield; //0x0448
	char pad_0450[2872]; //0x0450
	struct Itmes_t *PrimaryWeapon; //0x0F88
	char pad_0F90[952]; //0x0F90
	class Itmes_t *Arrows; //0x1348
};

struct XModel_t
{
	int32_t Check; //0x0000
	char pad_0004[4]; //0x0004
	struct XModelCache_t *XModelCache; //0x0008
	char pad_0010[120]; //0x0010
	class Character_t Character;
}; //Size: 0x0148

struct CharacterInfo_t
{
	char pad_0000[80]; //0x0000
	class CharacterNode *Node; //0x0050
}; //Size: 0x0058

struct CharacterNode
{
	char pad_0000[48]; //0x0000
	class CharacterStats_t *Stats; //0x0030
	char pad_0038[16]; //0x0038
	class CharacterStatsMax_t *MaxStats; //0x0048
}; //Size: 0x0050

struct CharacterStats_t
{
	char pad_0000[24]; //0x0000
	float health; //0x0018
	char pad_001C[4]; //0x001C
	float magic; //0x0020
	char pad_0024[4]; //0x0024
	float stamina; //0x0028
	char pad_002C[12]; //0x002C
}; //Size: 0x0038

struct CharacterStatsMax_t
{
	float maxHealth; //0x0000
	char pad_0004[4]; //0x0004
	float maxMagic; //0x0008
	char pad_000C[4]; //0x000C
	float maxStaminup; //0x0010
	char pad_0014[52]; //0x0014
}; //Size: 0x0048

struct entity
{
	char pad_0000[64]; //0x0000
	struct PlayerInstance *namePtr; //0x0040
	vec3 Angles; //0x0048
	vec3 Location; //0x0054
	void *Validation[4]; //0x0060 - 0x0078
	char pad_0080[112]; //0x0080
	class CharacterInfo_t *Character; //0x00F0
	char pad_00F8[360]; //0x00F8
	class XModel_t *XModel; //0x0260
}; //Size: 0x00DC
```

## How I fill the Struct

```cpp
//Hook 
sub_299B40_t sub_299B40 = sub_299B40_t(Utils.Module.ResolveImport(L"SkyrimSE.exe") + 0x299B40);

float __fastcall sub_299B40_Hook(float *a1, entity* a2, __int64 a3, char a4)

```
