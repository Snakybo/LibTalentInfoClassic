# LibTalentInfoClassic-1.0

A library that can retrieve talent info for any specialization.

## Examples

### Get talent info for the current class

```lua
local LibTalentInfo = LibStub("LibTalentInfoClassic-1.0")

local class = select(2, UnitClass("player"))
local _, name = LibTalentInfo:GetTalentInfo(class, 1, 1)

print(name)
```

### Get talent info for a different class

```lua
local LibTalentInfo = LibStub("LibTalentInfoClassic-1.0")

local class = "WARRIOR" -- non-localized class identifier

for tab = 1, MAX_TALENT_TABS do
	for talentIndex = 1, LibTalentInfo:GetNumTalentsForTab(class, tab) do
		local _, name = LibTalentInfo:GetTalentInfo(class, tab, talentIndex)
		print(name)
	end
end
```

## Updating for a new patch

The update process for talent data has been made as seamless as possible, there are two utilities which can be used to automatically extract talent data from in-game and convert it into a format usable by this library.

To get started, download the [Talent Extractor](https://github.com/snakybo/TalentExtractor/) addon and install it into your WoW. This addon has no interface, and will automatically run in the background as soon as you log in or switch specialization.

You will have to log into each class, and switch to each available specialization in order to fully populate (or update) your local data. The data is saved in your `WTF` folder.

After the data has been fully populated, download the [Talent Parser](https://github.com/snakybo/TalentParser) Python utility. The repository contains installation instructions.

Copy the `TalentExtractor.lua` data file from your `WTF/Account/YOUR ACCOUNT/SavedVariables` folder into the same folder as the Python script.

When you run the script a new `TalentDataWOTLK.lua` file will be generated, this file is fully compatible with LibTalentInfo and can be directly copied into this library.
