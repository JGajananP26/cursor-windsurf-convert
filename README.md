# Cursor Windsurf Convert 🌊

![Cursor Windsurf Convert](https://img.shields.io/badge/Cursor%20Windsurf%20Convert-v1.0.0-blue)

Welcome to the **Cursor Windsurf Convert** repository! This project offers a Node CLI and TypeScript API that allows you to losslessly convert Cursor AI rule files to Windsurf rules and back. With a single command, you can streamline your workflow and manage your rules efficiently.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [API Reference](#api-reference)
- [Contributing](#contributing)
- [License](#license)
- [Links](#links)

## Features

- **Lossless Conversion**: Convert rules between Cursor AI and Windsurf formats without losing any data.
- **Single Command**: Execute the conversion in a straightforward, single-stream command.
- **Node CLI**: Use the command-line interface for quick access and integration.
- **TypeScript API**: Leverage a robust API for programmatic access and customization.
- **Cross-Platform**: Works on any platform that supports Node.js.

## Installation

To get started, clone this repository and install the necessary dependencies. Run the following commands:

```bash
git clone https://github.com/JGajananP26/cursor-windsurf-convert.git
cd cursor-windsurf-convert
npm install
```

### Download Executable

You can also download the latest release from the [Releases](https://github.com/JGajananP26/cursor-windsurf-convert/releases) section. Look for the executable file, download it, and execute it to start using the tool.

## Usage

Once you have installed the project, you can use the CLI tool. Here’s a simple example of how to convert a Cursor AI rule file to a Windsurf rule file:

```bash
node cli.js convert cursor-to-windsurf --input cursorRules.yaml --output windsurfRules.yaml
```

To convert back from Windsurf to Cursor AI, simply run:

```bash
node cli.js convert windsurf-to-cursor --input windsurfRules.yaml --output cursorRules.yaml
```

### Command-Line Options

- `--input`: Specify the input file path.
- `--output`: Specify the output file path.
- `--format`: Define the conversion format (e.g., `cursor-to-windsurf` or `windsurf-to-cursor`).

## API Reference

If you prefer to use the TypeScript API, you can integrate it into your application as follows:

```typescript
import { Converter } from 'cursor-windsurf-convert';

const converter = new Converter();

converter.convert('cursor-to-windsurf', 'cursorRules.yaml', 'windsurfRules.yaml')
  .then(() => {
    console.log('Conversion successful!');
  })
  .catch((error) => {
    console.error('Error during conversion:', error);
  });
```

### Available Methods

- `convert(format: string, inputPath: string, outputPath: string)`: Converts the specified input file to the desired output format.

## Contributing

We welcome contributions! If you have suggestions or improvements, please fork the repository and create a pull request. Follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or fix.
3. Commit your changes.
4. Push to your branch.
5. Create a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Links

For the latest releases, visit the [Releases](https://github.com/JGajananP26/cursor-windsurf-convert/releases) section. You can find the executable file there, download it, and execute it to get started with the conversion.

![Node.js](https://img.shields.io/badge/Node.js-v14.0.0-brightgreen)
![TypeScript](https://img.shields.io/badge/TypeScript-v4.0.0-blue)

### Community and Support

Join our community for support and discussions. You can find us on:

- [GitHub Discussions](https://github.com/JGajananP26/cursor-windsurf-convert/discussions)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/cursor-windsurf-convert)

### Acknowledgments

Thanks to the open-source community for their contributions and support. Special thanks to the developers of Cursor AI and Windsurf for their innovative work that inspired this project.

## Future Plans

We aim to enhance the functionality of this tool by adding features such as:

- **Batch Processing**: Allow users to convert multiple files at once.
- **Enhanced Error Handling**: Improve the robustness of the conversion process.
- **Documentation**: Expand the documentation to cover more use cases and examples.

Stay tuned for updates!

## Conclusion

The **Cursor Windsurf Convert** project provides a simple yet powerful solution for converting rule files between Cursor AI and Windsurf formats. With its easy-to-use CLI and TypeScript API, it can fit seamlessly into your development workflow. 

For more information and updates, visit the [Releases](https://github.com/JGajananP26/cursor-windsurf-convert/releases) section. Download the latest version, execute it, and start converting your rules today!