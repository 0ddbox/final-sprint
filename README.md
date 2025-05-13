# final-sprint
# Sound Integration – Game Project (OOP Class)

## Overview
This file documents how the sound effects were added to the project using Java and LibGDX. These sounds were created in FL Studio and cover key interactions like menu navigation, collisions, and save confirmation. The code for playing these sounds has been written and tested locally but has **not yet been pushed to the main project repository**.

## Sound Files Implemented

| File Name                      | Usage                               |
|-------------------------------|-------------------------------------|
| `menu selection 2.wav`        | Menu hover/select sound             |
| `selection 3.wav`             | Alternate select sound              |
| `menu closing noise.wav`      | When closing any in-game menu       |
| `save game.wav`               | Played after a successful save      |
| `collision or wrong choice.wav` | Invalid input or collision event  |
| `collision 2.wav`             | Alternative collision sound         |

## How Sounds Were Integrated

- **File Placement:**  
  All sound files were placed in the `assets/sounds/` directory of the project.

- **Code Implementation:**  
  I created a `SoundManager` class to handle loading and playing sounds using LibGDX’s `Gdx.audio.newSound()` method. Each sound is stored in a `HashMap<String, Sound>` for easy reuse.

  ```java
  public class SoundManager {
      private static final Map<String, Sound> sounds = new HashMap<>();

      public static void load() {
          sounds.put("menu_select", Gdx.audio.newSound(Gdx.files.internal("sounds/menu selection 2.wav")));
          sounds.put("menu_close", Gdx.audio.newSound(Gdx.files.internal("sounds/menu closing noise.wav")));
          sounds.put("save_game", Gdx.audio.newSound(Gdx.files.internal("sounds/save game.wav")));
          sounds.put("collision_1", Gdx.audio.newSound(Gdx.files.internal("sounds/collision or wrong choice.wav")));
          sounds.put("collision_2", Gdx.audio.newSound(Gdx.files.internal("sounds/collision 2.wav")));
      }

      public static void play(String soundName) {
          if (sounds.containsKey(soundName)) {
              sounds.get(soundName).play();
          }
      }
  }
