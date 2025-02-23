==========================================================
Rainbow Six Siege No Recoil Script


This Lua script is designed to reduce recoil for 17 different weapons in Rainbow Six Siege. It includes a randomizer to add variability to the recoil control, making it more natural and less detectable.

----------------------------------------------------------
Features
----------------------------------------------------------

- Recoil Control: Adjusts both horizontal and vertical recoil for 17 different weapons.
- Randomizer: Adds a randomness factor to the recoil control to simulate natural movement.
- User Configuration: Allows users to customize the activation key and other settings.

----------------------------------------------------------
Weapons Supported
----------------------------------------------------------

1. SMG-11
2. R4-C
3. 9x19VSN
4. 552 Commando
5. AK-12
6. C8-SFW
7. F2
8. 556XI
9. PDW9
10. AK-74M
11. ARX200
12. AR33
13. MP7
14. Vector
15. Vector Holo
16. MPX
17. SMG-12

----------------------------------------------------------
User Configuration
----------------------------------------------------------

Activation Key
--------------

The script can be activated using the `capslock` key by default. This can be changed in the `Activate_Key` variable.

    local Activate_Key = "capslock"

Weapon Recoil Settings
----------------------

Each weapon has its own recoil settings defined in the `weapon_settings` table. These settings include horizontal recoil, vertical recoil, and fire delay.

    local weapon_settings = {
        [1] = { Horizontal_Recoil = 0, Vertical_Recoil = 35, Fire_Delay = 5 },
        [2] = { Horizontal_Recoil = 0, Vertical_Recoil = 25, Fire_Delay = 5 },
        [3] = { Horizontal_Recoil = -1, Vertical_Recoil = 21, Fire_Delay = 5 },
        [4] = { Horizontal_Recoil = -1, Vertical_Recoil = 18, Fire_Delay = 5 },
        [5] = { Horizontal_Recoil = -1, Vertical_Recoil = 56, Fire_Delay = 5 },
        [6] = { Horizontal_Recoil = 1, Vertical_Recoil = 46, Fire_Delay = 5 },
        [7] = { Horizontal_Recoil = -1, Vertical_Recoil = 75, Fire_Delay = 5 },
        [8] = { Horizontal_Recoil = 5, Vertical_Recoil = 36, Fire_Delay = 5 },
        [9] = { Horizontal_Recoil = -0.5, Vertical_Recoil = 46.5, Fire_Delay = 5 },
        [10] = { Horizontal_Recoil = -1, Vertical_Recoil = 34, Fire_Delay = 5 },
        [11] = { Horizontal_Recoil = -1, Vertical_Recoil = 43, Fire_Delay = 5 },
        [12] = { Horizontal_Recoil = -0.25, Vertical_Recoil = 42, Fire_Delay = 5 },
        [13] = { Horizontal_Recoil = 0.75, Vertical_Recoil = 19, Fire_Delay = 5 },
        [14] = { Horizontal_Recoil = 3, Vertical_Recoil = 67, Fire_Delay = 5 },
        [15] = { Horizontal_Recoil = 0.75, Vertical_Recoil = 27.5, Fire_Delay = 5 },
        [16] = { Horizontal_Recoil = -0, Vertical_Recoil = 19.5, Fire_Delay = 5 },
        [17] = { Horizontal_Recoil = 6, Vertical_Recoil = 37, Fire_Delay = 5 }
    }

Randomness Factor Settings
--------------------------

The script includes a randomness factor to make the recoil control more natural. This can be adjusted using the `Random_Factor_Min` and `Random_Factor_Max` variables.

    local Random_Factor_Min = 0.9 -- Minimum randomness factor (e.g., 90%)
    local Random_Factor_Max = 1.0 -- Maximum randomness factor (e.g., 100%)

Control Keys
------------

The script uses the left mouse button (`Fire_key = 1`) for firing and the right mouse button (`ADS_key = 3`) for aiming down sights.

    local Fire_key = 1
    local ADS_key = 3

----------------------------------------------------------
Script Variables
----------------------------------------------------------

The script uses a `weapon_table` to store the recoil settings for each weapon. This table is used to apply the recoil control during gameplay.

    local weapon_table = {
        [1] = { Horizontal = weapon_settings[1].Horizontal_Recoil, Vertical = weapon_settings[1].Vertical_Recoil, FireDelay = weapon_settings[1].Fire_Delay },
        [2] = { Horizontal = weapon_settings[2].Horizontal_Recoil, Vertical = weapon_settings[2].Vertical_Recoil, FireDelay = weapon_settings[2].Fire_Delay },
        [3] = { Horizontal = weapon_settings[3].Horizontal_Recoil, Vertical = weapon_settings[3].Vertical_Recoil, FireDelay = weapon_settings[3].Fire_Delay },
        [4] = { Horizontal = weapon_settings[4].Horizontal_Recoil, Vertical = weapon_settings[4].Vertical_Recoil, FireDelay = weapon_settings[4].Fire_Delay },
        [5] = { Horizontal = weapon_settings[5].Horizontal_Recoil, Vertical = weapon_settings[5].Vertical_Recoil, FireDelay = weapon_settings[5].Fire_Delay },
        [6] = { Horizontal = weapon_settings[6].Horizontal_Recoil, Vertical = weapon_settings[6].Vertical_Recoil, FireDelay = weapon_settings[6].Fire_Delay },
        [7] = { Horizontal = weapon_settings[7].Horizontal_Recoil, Vertical = weapon_settings[7].Vertical_Recoil, FireDelay = weapon_settings[7].Fire_Delay },
        [8] = { Horizontal = weapon_settings[8].Horizontal_Recoil, Vertical = weapon_settings[8].Vertical_Recoil, FireDelay = weapon_settings[8].Fire_Delay },
        [9] = { Horizontal = weapon_settings[9].Horizontal_Recoil, Vertical = weapon_settings[9].Vertical_Recoil, FireDelay = weapon_settings[9].Fire_Delay },
        [10] = { Horizontal = weapon_settings[10].Horizontal_Recoil, Vertical = weapon_settings[10].Vertical_Recoil, FireDelay = weapon_settings[10].Fire_Delay },
        [11] = { Horizontal = weapon_settings[11].Horizontal_Recoil, Vertical = weapon_settings[11].Vertical_Recoil, FireDelay = weapon_settings[11].Fire_Delay },
        [12] = { Horizontal = weapon_settings[12].Horizontal_Recoil, Vertical = weapon_settings[12].Vertical_Recoil, FireDelay = weapon_settings[12].Fire_Delay },
        [13] = { Horizontal = weapon_settings[13].Horizontal_Recoil, Vertical = weapon_settings[13].Vertical_Recoil, FireDelay = weapon_settings[13].Fire_Delay },
        [14] = { Horizontal = weapon_settings[14].Horizontal_Recoil, Vertical = weapon_settings[14].Vertical_Recoil, FireDelay = weapon_settings[14].Fire_Delay },
        [15] = { Horizontal = weapon_settings[15].Horizontal_Recoil, Vertical = weapon_settings[15].Vertical_Recoil, FireDelay = weapon_settings[15].Fire_Delay },
        [16] = { Horizontal = weapon_settings[16].Horizontal_Recoil, Vertical = weapon_settings[16].Vertical_Recoil, FireDelay = weapon_settings[16].Fire_Delay },
        [17] = { Horizontal = weapon_settings[17].Horizontal_Recoil, Vertical = weapon_settings[17].Vertical_Recoil, FireDelay = weapon_settings[17].Fire_Delay }
    }

----------------------------------------------------------
Functions
----------------------------------------------------------

Volatility
----------

Calculates the delay between shots with added variability.

    function Volatility(base_delay, variability)
        return base_delay + (variability * (math.random() - 0.5))
    end

Move_x
------

Moves the mouse horizontally based on the recoil settings and randomness factor.

    function Move_x(horizontal_recoil)
        local random_factor = math.random() * (Random_Factor_Max - Random_Factor_Min) + Random_Factor_Min
        MoveMouseRelative(math.floor(random_factor * horizontal_recoil), 0)
    end

Move_y
------

Moves the mouse vertically based on the recoil settings and randomness factor.

    function Move_y(vertical_recoil)
        local random_factor = math.random() * (Random_Factor_Max - Random_Factor_Min) + Random_Factor_Min
        MoveMouseRelative(0, math.floor(random_factor * vertical_recoil))
    end

Direct_Fire
-----------

Controls the firing mechanism, applying the recoil settings and delays.

    function Direct_Fire()
        local horizontal_recoil = weapon_table[current_weapon].Horizontal
        local vertical_recoil = weapon_table[current_weapon].Vertical

        -- Add initial delay before first pull
        Sleep(1) -- 1ms delay for weapons with charge-up time

        repeat
            if not IsMouseButtonPressed(ADS_key) then
                break
            end
            Move_x(horizontal_recoil)
            Move_y(vertical_recoil)
            Sleep(math.floor(Volatility(0.8, 0.5) * weapon_table[current_weapon].FireDelay))
        until not IsMouseButtonPressed(Fire_key)
    end

OnEvent
-------

Handles events such as profile activation, deactivation, and mouse button presses.

    function OnEvent(event, arg)
        if event == "PROFILE_ACTIVATED" then
            script_active = true
            EnablePrimaryMouseButtonEvents(true)
        elseif event == "PROFILE_DEACTIVATED" then
            script_active = false
            ReleaseMouseButton(Fire_key)
            ReleaseMouseButton(ADS_key)
        end

        if event == "MOUSE_BUTTON_PRESSED" and arg == Activate_Key then
            script_active = not script_active
        end

        if script_active and event == "MOUSE_BUTTON_PRESSED" and arg == Fire_key and IsKeyLockOn(Activate_Key) and IsMouseButtonPressed(ADS_key) then
            Direct_Fire()
        end
    end

----------------------------------------------------------
Usage
----------------------------------------------------------

1. Configure the script by setting the desired `Activate_Key`, `Random_Factor_Min`, `Random_Factor_Max`, `Fire_key`, and `ADS_key`.
2. Load the script in your Lua script executor.
3. Activate the script using the `Activate_Key`.
4. Select the desired weapon by setting the `current_weapon` variable.
5. Enjoy reduced recoil with natural variability while playing Rainbow Six Siege.

**Note**: Use this script responsibly and be aware of the terms of service of the game you are playing.
