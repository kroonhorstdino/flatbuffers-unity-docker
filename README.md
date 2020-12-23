# flatbuffers-unity

convenient cross platform way to use flatbuffers for unity:

1. creates flatbuffers .net (mono) DLL compatible with unity 
2. dockerized flatc binary for easy integration into CI pipelines

based on [mono docker](https://github.com/mono/docker)

**note:** currently only supports flatbuffers v1.12.0

# Usage

1. create your schema fbs (`schema.fbs`)
2. use flatc to generate your code (flatc bin in container)
3. grab .net DLL for unity from [releases](https://github.com/gameroasters/flatbuffers-unity-docker/releases)
4. done

## example for using flatc

```sh
docker run -it -v $(shell pwd):/fb gameroasters/flatbuffers-unity:latest /bin/bash -c "cd /fb && \
	flatc -n --gen-onefile schema.fbs && \
	flatc -r --gen-onefile schema.fbs"
```

this will generate a `schema.cs` and `schema.rs` with your schema type serialiation in rust and csharp.

# Todo

- [] support flatbuffers master version
- [] use dotnet instead of mono https://github.com/google/flatbuffers/commit/0bdf2fa156f5133b09ddac7beb326b942d524b38