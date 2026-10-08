# Building DEVI Decrypt

You need the [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0) (see `global.json`).

```bash
git clone https://github.com/Deviops-app/DEVI-Decrypt.git
cd DEVI-Decrypt
dotnet restore DeviDecrypt.sln
dotnet build DeviDecrypt.sln --configuration Release
```

Official Windows packages remain on <https://deviops.app/tools/devi-decrypt/>.

See [docs/STATUS.md](docs/STATUS.md).
