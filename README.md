<h2 align="center">⚠️ THIS IS A MIRROR ⚠️</h2>

> [!WARNING]  
> Hi there! This is a **read-only mirror**, automatically synced from our Forgejo instance.  
>   
> - 🛠️ All development happens on the primary Forgejo repository  
> - 💬 You’re welcome to open Issues, Discussions, or even PRs here if it’s convenient — just know they may not be acted on directly, since the sync is one-way  
>   
> For the best chance of your contributions being merged, or for quicker responses, please head over to the main Forgejo repo.  
>   
> - Original repo: https://git.prisma.moe/Thadah/Hibernateforge
>   
> — *Self-hosting 4 the win!*

---

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]

<!-- PROJECT LOGO 
<br />
<div align="center">
  <a href="https://github.com/Thadah/hibernateforge">
    <img src="src/assets/hfLogo.png" alt="Logo" width="160" height="160">
  </a>
-->
  <h1 align="center">Hibernateforge</h1>

  <p align="center">
    Let your Minecraft Forge server snooze when idle, slashing CPU usage without missing a block!
    <br />
    <br />
    <a href="https://github.com/Thadah/hibernateforge">View Demo</a>
    ·
    <a href="https://github.com/Thadah/hibernateforge/issues">Report Bug or </a>
    ·
    <a href="https://github.com/Thadah/hibernateforge/issues">Request Feature</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#build">Build</a></li>
      </ul>
    </li>
    <li><a href="#run">Run</a></li>
    <li><a href="#configuration">Configuration</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>


<!-- ABOUT THE PROJECT -->
## About The Project

**Hibernateforge** is a lightweight tool that automatically puts your Minecraft Forge server to sleep when no players are online. By reducing CPU usage during idle times, it helps save server resources, lowers your electricity bill, and makes your server more eco-friendly. It's a simple way to keep your Minecraft world running smoothly without wasting power when it's not needed.


<p align="right">(<a href="#readme-top">back to top</a>)</p>


### Built With

This project is built with the following technologies:

* ![Gradle](https://img.shields.io/badge/gradle-02303A.svg?style=for-the-badge&logo=gradle&logoColor=white)
* ![Fabric/Neoforge](https://img.shields.io/badge/CurseForge-F16436?style=for-the-badge&logo=CurseForge&logoColor=white)
* ![Visual Studio Code](https://img.shields.io/badge/Visual_Studio_Code-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- GETTING STARTED -->
## Getting Started

To get a local copy up and running, follow these simple steps.

### Prerequisites

Ensure you have the following installed on your machine:

- **Java Development Kit (JDK)**: Version 21 or higher.
  - [Download JDK](https://adoptium.net/)
- **Gradle**: Version 8.9 or higher.
  - [Install Gradle](https://gradle.org/install/)
- **Minecraft**: Version 1.21.6 or higher

### Build

1. **Clone the repository**
    ```sh
    git clone https://github.com/Thadah/hibernateforge.git
    ```

2. Navigate to the project directory
    ```sh
    cd hibernateforge
    ```

3. Build the project with Gradle
    ```sh
    ./gradlew clean :fabric:build :neoforge:build
    ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Run

You will need a Minecraft Forge server. 
Copy the `<mod>/build/libs/hibernateforge-<mod>-x.x.x.jar` file to the `mods` folder of your Minecraft Forge server.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Configuration

The mod automatically creates a configuration file at `config/hibernateforge.json` on first run. Here are the available settings:

### Basic Settings

```json
{
  "startEnabled": true,
  "ticksToSkip": 400,
  "permissionLevel": 2,
  "sleepTimeMs": 75
}
```

| Setting | Default | Description |
|---------|---------|-------------|
| `startEnabled` | `true` | Whether hibernation activates automatically when server starts with no players |
| `ticksToSkip` | `400` | Number of ticks to process before applying sleep during hibernation |
| `permissionLevel` | `2` | Required permission level to use hibernation commands (0=all, 4=owner) |
| `sleepTimeMs` | `75` | Milliseconds to sleep between tick processing cycles |

### Memory Optimization

```json
{
  "enableMemoryOptimization": true,
  "memoryCleanupIntervalSeconds": 30,
  "memoryThresholdPercent": 80.0,
  "maxChunksToUnloadPerTick": 10,
  "forceGarbageCollection": true,
  "gcIntervalSeconds": 30,
  "saveBeforeHibernation": true,
  "removeOldDroppedItems": true,
  "droppedItemMaxAgeSeconds": 300,
  "removeProjectiles": true,
  "removeExperienceOrbs": true,
  "compactDataStructures": true,
  "logMemoryUsage": true
}
```

| Setting | Default | Description |
|---------|---------|-------------|
| `enableMemoryOptimization` | `true` | Enable memory cleanup during hibernation |
| `memoryCleanupIntervalSeconds` | `30` | How often to run memory cleanup routines |
| `memoryThresholdPercent` | `80.0` | Memory usage percentage that triggers cleanup |
| `maxChunksToUnloadPerTick` | `10` | Maximum chunks to unload per server tick |
| `forceGarbageCollection` | `true` | Force Java garbage collection during hibernation |
| `gcIntervalSeconds` | `30` | Minimum time between garbage collection runs |
| `saveBeforeHibernation` | `true` | Save world data before entering hibernation |
| `removeOldDroppedItems` | `true` | Remove old dropped items during hibernation |
| `droppedItemMaxAgeSeconds` | `300` | Age in seconds after which items are removed (5 minutes) |
| `removeProjectiles` | `true` | Remove arrows and other projectiles |
| `removeExperienceOrbs` | `true` | Remove floating experience orbs |
| `compactDataStructures` | `true` | Attempt to compact server data structures |
| `logMemoryUsage` | `true` | Log memory usage information to console |

### CPU Optimization

```json
{
  "aggressiveCpuSaving": true,
  "minSleepInterval": 1500,
  "highLoadSleepMultiplier": 1.5,
  "yieldInterval": 8
}
```

| Setting | Default | Description |
|---------|---------|-------------|
| `aggressiveCpuSaving` | `true` | Enable more aggressive CPU saving measures |
| `minSleepInterval` | `1500` | Minimum time in milliseconds between sleep cycles |
| `highLoadSleepMultiplier` | `1.5` | Multiplier for sleep time when system load is high |
| `yieldInterval` | `8` | How often to yield CPU to other threads (every N ticks) |

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.
If you don't have any coding experience, testing other platforms and configurations is also very welcome!

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- LICENSE -->
## License

Distributed under the European Union Public License v1.2. See `LICENSE` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- CONTACT -->
## Contact

Thadah D. Denyse - thadahdenyse@protonmail.com

Project Link: [https://github.com/Thadah/hibernateforge](https://github.com/Thadah/hibernateforge)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

Thanks to these nice projects!

* [Img Shields](https://shields.io)
* [markdown-badges](https://github.com/Ileriayo/markdown-badges#table-of-contents)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/Thadah/hibernateforge.svg?style=for-the-badge
[contributors-url]: https://github.com/Thadah/hibernateforge/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Thadah/hibernateforge.svg?style=for-the-badge
[forks-url]: https://github.com/Thadah/hibernateforge/network/members
[stars-shield]: https://img.shields.io/github/stars/Thadah/hibernateforge.svg?style=for-the-badge
[stars-url]: https://github.com/Thadah/hibernateforge/stargazers
[issues-shield]: https://img.shields.io/github/issues/Thadah/hibernateforge.svg?style=for-the-badge
[issues-url]: https://github.com/Thadah/hibernateforge/issues
[license-shield]: https://img.shields.io/github/license/Thadah/hibernateforge.svg?style=for-the-badge
[license-url]: https://github.com/Thadah/hibernateforge/blob/master/LICENSE

---

> [!WARNING]
> **🔗 This repository is automatically mirrored from a private Forgejo instance.**