# Template Overview
## How to Use the Template
- Start by using `Use this template` in this repository to create a Repo on Github.
- Start by Forking or Downloading this repository.

## Layers
There are 5 layers: Features, Services, Core, UserInterface, Shared.

- **Feature**
  - The layer directly interacting with the user, handling user actions or displaying data.
  - Example: AuthFeature, ProfileFeature

- **Domain**
  - The layer where domain logic is processed.
  - Example: AuthDomain, ProfileDomain

- **Core**
  - The layer that contains pure functional modules without the business logic of the app.
  - Example: NetworkingModule, DatabaseModule

- **UserInterface**
  - The layer that contains UI element modules like common views, design systems, and resources.
  - Example: DesignSystem, LocalizableManager

- **Shared**
  - The layer that contains modules reused across all layers, like logging and extensions.
  - Example: UtilityModule, LoggingModule

These layers are separated with the above considerations in mind.

## Micro Feature
Each module is designed based on the Micro Feature structure.
This architecture, inspired by Micro Services, allows for horizontal expansion of large and expanding projects by functionality.

<img src="https://user-images.githubusercontent.com/74440939/210211725-5ac7c9fe-bf25-4707-9775-4f46f1c0c522.png" width="200">

##### https://docs.tuist.io/building-at-scale/microfeatures/#product

## Project Setup
You can perform the basic settings by running `make init` in the project root, entering the project name and organization name.

Running `make signing` in the project root allows for Project Team Signing.

## Creating Modules
Running `make module` in the project root lets you create a new module by selecting the module layer, name, and Micro Feature type.

## Makefile
Commands that can be run in the project root:
- **make init**: Basic project setup by entering the project name and organization.
  - swift Scripts/InitEnvironment.swift

- **make signing**: Project Team Signing.
  - swift Scripts/CodeSigning.swift

- **make generate**: Fetch external dependencies and generate the project.
  - tuist fetch
  - tuist generate

- **make module**: Create a module.
  - swift Scripts/GenerateModule.swift

- **make dependency**: Add a dependency.
  - swift Scripts/NewDependency.swift

- **make ci_generate**: Fetch dependencies and generate a project for CI (without SwiftLint).
  - tuist fetch
  - TUIST_ENV=CI tuist generate

- **make cd_generate**: Fetch dependencies and generate a project for CD (without SwiftLint).
  - tuist fetch
  - TUIST_ENV=CD tuist generate

- **make clean**: Delete all xcodeproj and xcworkspace files.
  - rm -rf **/*.xcodeproj
  - rm -rf *.xcworkspace

- **make reset**: Run tuist clean, then delete all xcodeproj and xcworkspace files.
  - tuist clean
  - rm -rf **/*.xcodeproj
  - rm -rf *.xcworkspace

## Scaffold
```sh
tuist Scaffold(Demo/Interface/Sources/Testing/Tests/UITests) 
  --layer (Features/Services/Core/Shared/UserInterface layer name)
  --name (module name)
```

This allows you to directly create the target module of the Project module.