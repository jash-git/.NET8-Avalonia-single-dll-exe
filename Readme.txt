問01.C# Avalonia 專案編譯後 執行檔和相關的相依DLL 數量很多 可否將他們整併成為單一檔案 [無法使用]
	使用 ILMerge(太老不支援)
	
	.NET Core 自包含發行
		dotnet publish -c Release -r win-x64 [框架相依式：適合於你的應用程式依然依賴於用戶機器上的 .NET Runtime。]
		dotnet publish -c Release -r win-x64 --self-contained [自包含式：自帶所有相關依賴的 .NET Runtime，因此最終會生成一個相當大的單一檔案，但獨立性會更高。]
		
		EX:
		(.csproj 文件中的配置)
			<PropertyGroup>
			  <OutputType>WinExe</OutputType>
			  <TargetFramework>net5.0</TargetFramework>
			  <RuntimeIdentifier>win-x64</RuntimeIdentifier>
			</PropertyGroup>
		專案檔目錄BAT
			dotnet publish -c Release

			
問02.C# Avalonia 專案編譯後 執行檔和相關的相依DLL 數量很多 可否將他們整併成為一個EXE 和一個DLL [確定會動]
	Costura.Fody
		指令:
			dotnet add package Fody 
			dotnet add package Costura.Fody
		UI(NuGet):
			Costura.Fody
		其他教學文件(以備份實體檔案)