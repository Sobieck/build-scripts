# Build scripts

Ritter Insurance Marketing project specific build scripts.

- `build-webapi-netfx.cake` ASP.NET WebApi2 with full .NET framework

## Usage

Perform the following steps in a target project:

### Create build.cmd

```batch
@echo off

powershell -ExecutionPolicy RemoteSigned -File ./build.ps1
```

### Create build.ps1

```powershell
Remove-Item "build" -Recurse -ErrorAction Ignore
New-Item -ItemType directory -Path "build" | Out-Null

Invoke-WebRequest https://raw.githubusercontent.com/ritterim/build-scripts/master/bootstrap-cake.ps1 -OutFile build\bootstrap-cake.ps1
Invoke-WebRequest https://raw.githubusercontent.com/ritterim/build-scripts/master/build-webapi-netfx.cake -OutFile build.cake

.\build\bootstrap-cake.ps1
```

### Create version.txt

Example:

```
1.0.0
```

### Use AssemblyInfo.Generated.cs

If the generated file won't be included in another manner, replace `<Compile Include="Properties\AssemblyInfo.cs" />` with `<Compile Include="Properties\AssemblyInfo*.cs" />`.

### Create or update `.gitignore`

Include:

```
build/
tools/
build.cake
AssemblyInfo.Generated.cs
```

## License

MIT
