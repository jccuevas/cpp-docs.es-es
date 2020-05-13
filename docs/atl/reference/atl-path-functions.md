---
title: Funciones de ruta de acceso ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, path
f1_keywords:
- ATLPATH/ATL::ATLPath::AddBackslash
- ATLPATH/ATL::ATLPath::AddExtension
- ATLPATH/ATL::ATLPath::Append
- ATLPATH/ATL::ATLPath::BuildRoot
- ATLPATH/ATL::ATLPath::Canonicalize
- ATLPATH/ATL::ATLPath::Combine
- ATLPATH/ATL::ATLPath::CommonPrefix
- ATLPATH/ATL::ATLPath::CompactPath
- ATLPATH/ATL::ATLPath::CompactPathEx
- ATLPATH/ATL::ATLPath::FileExists
- ATLPATH/ATL::ATLPath::FindExtension
- ATLPATH/ATL::ATLPath::FindFileName
- ATLPATH/ATL::ATLPath::GetDriveNumber
- ATLPATH/ATL::ATLPath::IsDirectory
- ATLPATH/ATL::ATLPath::IsFileSpec
- ATLPATH/ATL::ATLPath::IsPrefix
- ATLPATH/ATL::ATLPath::IsRelative
- ATLPATH/ATL::ATLPath::IsRoot
- ATLPATH/ATL::ATLPath::IsSameRoot
- ATLPATH/ATL::ATLPath::IsUNC
- ATLPATH/ATL::ATLPath::IsUNCServer
- ATLPATH/ATL::ATLPath::IsUNCServerShare
- ATLPATH/ATL::ATLPath::MakePretty
- ATLPATH/ATL::ATLPath::MatchSpec
- ATLPATH/ATL::ATLPath::QuoteSpaces
- ATLPATH/ATL::ATLPath::RelativePathTo
- ATLPATH/ATL::ATLPath::RemoveArgs
- ATLPATH/ATL::ATLPath::RemoveBackslash
- ATLPATH/ATL::ATLPath::RemoveBlanks
- ATLPATH/ATL::ATLPath::RemoveExtension
- ATLPATH/ATL::ATLPath::RemoveFileSpec
- ATLPATH/ATL::ATLPath::RenameExtension
- ATLPATH/ATL::ATLPath::SkipRoot
- ATLPATH/ATL::ATLPath::StripPath
- ATLPATH/ATL::ATLPath::StripToRoot
- ATLPATH/ATL::ATLPath::UnquoteSpaces
ms.assetid: d1ec2b8d-7ec7-43ea-90dd-0a740d2a742b
ms.openlocfilehash: 2ab8dfc2e9d5789b7ee67f8082f28cf228608663
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168804"
---
# <a name="atl-path-functions"></a>Funciones de ruta de acceso ATL

ATL proporciona la clase ATLPath para manipular las rutas de acceso en forma de [CPathT](cpatht-class.md). Este código se puede encontrar en atlpath. h.

## <a name="related-classes"></a>Clases relacionadas

|||
|-|-|
|[Clase CPathT](cpatht-class.md)|Esta clase representa una ruta de acceso.|

## <a name="related-typedefs"></a>Typedefs relacionadas

|||
|-|-|
|`CPath`|Una especialización de [CPathT](cpatht-class.md) mediante `CString`.|
|`CPathA`|Una especialización de [CPathT](cpatht-class.md) mediante `CStringA`.|
|`CPathW`|Una especialización de [CPathT](cpatht-class.md) mediante `CStringW`.|

## <a name="functions"></a>Functions

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|Esta función es un contenedor sobrecargado de [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).|
|[ATLPath::AddExtension](#addextension)|Esta función es un contenedor sobrecargado de [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).|
|[ATLPath::Append](#append)|Esta función es un contenedor sobrecargado de [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).|
|[ATLPath::BuildRoot](#buildroot)|Esta función es un contenedor sobrecargado de [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).|
|[ATLPath::Canonicalize](#canonicalize)|Esta función es un contenedor sobrecargado de [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).|
|[ATLPath::Combine](#combine)|Esta función es un contenedor sobrecargado de [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).|
|[ATLPath::CommonPrefix](#commonprefix)|Esta función es un contenedor sobrecargado de [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).|
|[ATLPath::CompactPath](#compactpath)|Esta función es un contenedor sobrecargado de [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).|
|[ATLPath::CompactPathEx](#compactpathex)|Esta función es un contenedor sobrecargado de [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).|
|[ATLPath::FileExists](#fileexists)|Esta función es un contenedor sobrecargado de [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).|
|[ATLPath::FindExtension](#findextension)|Esta función es un contenedor sobrecargado de [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).|
|[ATLPath::FindFileName](#findfilename)|Esta función es un contenedor sobrecargado de [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).|
|[ATLPath::GetDriveNumber](#getdrivenumber)|Esta función es un contenedor sobrecargado de [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).|
|[ATLPath::IsDirectory](#isdirectory)|Esta función es un contenedor sobrecargado de [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).|
|[ATLPath::IsFileSpec](#isfilespec)|Esta función es un contenedor sobrecargado de [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).|
|[ATLPath::IsPrefix](#isprefix)|Esta función es un contenedor sobrecargado de [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).|
|[ATLPath::IsRelative](#isrelative)|Esta función es un contenedor sobrecargado de [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).|
|[ATLPath::IsRoot](#isroot)|Esta función es un contenedor sobrecargado de [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).|
|[ATLPath::IsSameRoot](#issameroot)|Esta función es un contenedor sobrecargado de [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).|
|[ATLPath::IsUNC](#isunc)|Esta función es un contenedor sobrecargado de [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).|
|[ATLPath::IsUNCServer](#isuncserver)|Esta función es un contenedor sobrecargado de [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).|
|[ATLPath::IsUNCServerShare](#isuncservershare)|Esta función es un contenedor sobrecargado de [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).|
|[ATLPath::MakePretty](#makepretty)|Esta función es un contenedor sobrecargado de [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).|
|[ATLPath::MatchSpec](#matchspec)|Esta función es un contenedor sobrecargado de [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).|
|[ATLPath::QuoteSpaces](#quotespaces)|Esta función es un contenedor sobrecargado de [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).|
|[ATLPath::RelativePathTo](#relativepathto)|Esta función es un contenedor sobrecargado de [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).|
|[ATLPath::RemoveArgs](#removeargs)|Esta función es un contenedor sobrecargado de [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).|
|[ATLPath::RemoveBackslash](#removebackslash)|Esta función es un contenedor sobrecargado de [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).|
|[ATLPath::RemoveBlanks](#removeblanks)|Esta función es un contenedor sobrecargado de [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).|
|[ATLPath::RemoveExtension](#removeextension)|Esta función es un contenedor sobrecargado de [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).|
|[ATLPath::RemoveFileSpec](#removefilespec)|Esta función es un contenedor sobrecargado de [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).|
|[ATLPath::RenameExtension](#renameextension)|Esta función es un contenedor sobrecargado de [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).|
|[ATLPath::SkipRoot](#skiproot)|Esta función es un contenedor sobrecargado de [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).|
|[ATLPath::StripPath](#strippath)|Esta función es un contenedor sobrecargado de [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).|
|[ATLPath::StripToRoot](#striptoroot)|Esta función es un contenedor sobrecargado de [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).|
|[ATLPath::UnquoteSpaces](#unquotespaces)|Esta función es un contenedor sobrecargado de [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlpath. h

## <a name="atlpathaddbackslash"></a><a name="addbackslash"></a>ATLPath:: AddBackSlash

Esta función es un contenedor sobrecargado de [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

### <a name="syntax"></a>Sintaxis

```cpp
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw) para obtener más información.

## <a name="atlpathaddextension"></a><a name="addextension"></a>ATLPath:: AddExtension

Esta función es un contenedor sobrecargado de [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>Observaciones

Consulte [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw) para obtener más información.

## <a name="atlpathappend"></a><a name="append"></a>ATLPath:: Append

Esta función es un contenedor sobrecargado de [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>Observaciones

Consulte [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw) para obtener más información.

## <a name="atlpathbuildroot"></a><a name="buildroot"></a>ATLPath:: objeto buildroot

Esta función es un contenedor sobrecargado de [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

### <a name="syntax"></a>Sintaxis

```cpp
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>Observaciones

Consulte [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw) para obtener más información.

## <a name="atlpathcanonicalize"></a><a name="canonicalize"></a>ATLPath:: Canonicalization

Esta función es un contenedor sobrecargado de [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>Observaciones

Consulte [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew) para obtener más información.

## <a name="atlpathcombine"></a><a name="combine"></a>ATLPath:: Combine

Esta función es un contenedor sobrecargado de [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

### <a name="syntax"></a>Sintaxis

```cpp
inline char* Combine(
   char* pszDest,
   const char* pszDir,
   const char* pszFile
);

inline wchar_t* Combine(
   wchar_t* pszDest,
   const wchar_t* pszDir,
   const wchar_t* pszFile);
```

### <a name="remarks"></a>Observaciones

Consulte PathCombine para obtener más información.

## <a name="atlpathcommonprefix"></a><a name="commonprefix"></a>ATLPath:: CommonPrefix

Esta función es un contenedor sobrecargado de [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

### <a name="syntax"></a>Sintaxis

```cpp
inline int CommonPrefix(
   const char* pszFile1,
   const char* pszFile2,
   char* pszDest);

inline int CommonPrefix(
   const wchar_t* pszFile1,
   const wchar_t* pszFile2,
   wchar_t* pszDest);
```

### <a name="remarks"></a>Observaciones

Consulte [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw) para obtener más información.

## <a name="atlpathcompactpath"></a><a name="compactpath"></a>ATLPath:: CompactPath

Esta función es un contenedor sobrecargado de [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL CompactPath(
   HDC hDC,
   char* pszPath,
   UINT dx);

inline BOOL CompactPath(
   HDC hDC,
   wchar_t* pszPath,
   UINT dx);
```

### <a name="remarks"></a>Observaciones

Consulte [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw) para obtener más información.

## <a name="atlpathcompactpathex"></a><a name="compactpathex"></a>ATLPath:: CompactPathEx

Esta función es un contenedor sobrecargado de [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL CompactPathEx(
   char* pszDest,
   const char* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);

inline BOOL CompactPathEx(
   wchar_t* pszDest,
   const wchar_t* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);
```

### <a name="remarks"></a>Observaciones

Consulte [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw) para obtener más información.

## <a name="atlpathfileexists"></a><a name="fileexists"></a>ATLPath:: FileExists

Esta función es un contenedor sobrecargado de [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw) para obtener más información.

## <a name="atlpathfindextension"></a><a name="findextension"></a>ATLPath:: FindExtension

Esta función es un contenedor sobrecargado de [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

### <a name="syntax"></a>Sintaxis

```cpp
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw) para obtener más información.

## <a name="atlpathfindfilename"></a><a name="findfilename"></a>ATLPath:: FindFileName

Esta función es un contenedor sobrecargado de [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

### <a name="syntax"></a>Sintaxis

```cpp
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) para obtener más información.

## <a name="atlpathgetdrivenumber"></a><a name="getdrivenumber"></a>ATLPath:: GetDriveNumber

Esta función es un contenedor sobrecargado de [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

### <a name="syntax"></a>Sintaxis

```cpp
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw) para obtener más información.

## <a name="atlpathisdirectory"></a><a name="isdirectory"></a>ATLPath:: IsDirectory

Esta función es un contenedor sobrecargado de [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

```cpp
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte PathIsDirectory para obtener más información.

## <a name="atlpathisfilespec"></a><a name="isfilespec"></a>ATLPath:: IsFileSpec

Esta función es un contenedor sobrecargado de [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw) para obtener más información.

## <a name="atlpathisprefix"></a><a name="isprefix"></a>ATLPath:: IsPrefix

Esta función es un contenedor sobrecargado de [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw) para obtener más información.

## <a name="atlpathisrelative"></a><a name="isrelative"></a>ATLPath:: IsRelative

Esta función es un contenedor sobrecargado de [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew) para obtener más información.

## <a name="atlpathisroot"></a><a name="isroot"></a>ATLPath:: IsRoot

Esta función es un contenedor sobrecargado de [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw) para obtener más información.

## <a name="atlpathissameroot"></a><a name="issameroot"></a>ATLPath:: IsSameRoot

Esta función es un contenedor sobrecargado de [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>Observaciones

Consulte [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw) para obtener más información.

## <a name="atlpathisunc"></a><a name="isunc"></a>ATLPath:: IsUNC

Esta función es un contenedor sobrecargado de [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw) para obtener más información.

## <a name="atlpathisuncserver"></a><a name="isuncserver"></a>ATLPath:: IsUNCServer

Esta función es un contenedor sobrecargado de [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw) para obtener más información.

## <a name="atlpathisuncservershare"></a><a name="isuncservershare"></a>ATLPath:: IsUNCServerShare

Esta función es un contenedor sobrecargado de [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew) para obtener más información.

## <a name="atlpathmakepretty"></a><a name="makepretty"></a>ATLPath:: MakePretty

Esta función es un contenedor sobrecargado de [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw) para obtener más información.

## <a name="atlpathmatchspec"></a><a name="matchspec"></a>ATLPath:: MatchSpec

Esta función es un contenedor sobrecargado de [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>Observaciones

Consulte [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw) para obtener más información.

## <a name="atlpathquotespaces"></a><a name="quotespaces"></a>ATLPath:: QuoteSpaces

Esta función es un contenedor sobrecargado de [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

### <a name="syntax"></a>Sintaxis

```cpp
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw) para obtener más información.

## <a name="atlpathrelativepathto"></a><a name="relativepathto"></a>ATLPath:: RelativePathTo

Esta función es un contenedor sobrecargado de [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL RelativePathTo(
   char* pszPath,
   const char* pszFrom,
   DWORD dwAttrFrom,
   const char* pszTo,
   DWORD dwAttrTo);

inline BOOL RelativePathTo(
   wchar_t* pszPath,
   const wchar_t* pszFrom,
   DWORD dwAttrFrom,
   const wchar_t* pszTo,
   DWORD dwAttrTo);
```

### <a name="remarks"></a>Observaciones

Consulte [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow) para obtener más información.

## <a name="atlpathremoveargs"></a><a name="removeargs"></a>ATLPath:: RemoveArgs

Esta función es un contenedor sobrecargado de [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

### <a name="syntax"></a>Sintaxis

```cpp
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw) para obtener más información.

## <a name="atlpathremovebackslash"></a><a name="removebackslash"></a>ATLPath:: RemoveBackslash

Esta función es un contenedor sobrecargado de [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

### <a name="syntax"></a>Sintaxis

```cpp
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw) para obtener más información.

## <a name="atlpathremoveblanks"></a><a name="removeblanks"></a>ATLPath:: RemoveBlanks

Esta función es un contenedor sobrecargado de [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

### <a name="syntax"></a>Sintaxis

```cpp
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw) para obtener más información.

## <a name="atlpathremoveextension"></a><a name="removeextension"></a>ATLPath:: RemoveExtension

Esta función es un contenedor sobrecargado de [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

### <a name="syntax"></a>Sintaxis

```cpp
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw) para obtener más información.

## <a name="atlpathremovefilespec"></a><a name="removefilespec"></a>ATLPath:: RemoveFileSpec

Esta función es un contenedor sobrecargado de [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw) para obtener más información.

## <a name="atlpathrenameextension"></a><a name="renameextension"></a>ATLPath:: RenameExtension

Esta función es un contenedor sobrecargado de [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>Observaciones

Consulte [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw) para obtener más información.

## <a name="atlpathskiproot"></a><a name="skiproot"></a>ATLPath:: SkipRoot

Esta función es un contenedor sobrecargado de [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

### <a name="syntax"></a>Sintaxis

```cpp
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw) para obtener más información.

## <a name="atlpathstrippath"></a><a name="strippath"></a>ATLPath:: StripPath

Esta función es un contenedor sobrecargado de [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

### <a name="syntax"></a>Sintaxis

```cpp
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw) para obtener más información.

## <a name="atlpathstriptoroot"></a><a name="striptoroot"></a>ATLPath:: StripToRoot

Esta función es un contenedor sobrecargado de [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

### <a name="syntax"></a>Sintaxis

```cpp
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw) para obtener más información.

## <a name="atlpathunquotespaces"></a><a name="unquotespaces"></a>ATLPath:: UnquoteSpaces

Esta función es un contenedor sobrecargado de [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

### <a name="syntax"></a>Sintaxis

```cpp
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Observaciones

Consulte [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw) para obtener más información.
