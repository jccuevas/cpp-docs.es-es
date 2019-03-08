---
title: Funciones de ruta de acceso de ATL
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
ms.openlocfilehash: 683fd9c6464187e416ea032840507b2062de1fa3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295817"
---
# <a name="atl-path-functions"></a>Funciones de ruta de acceso de ATL

ATL proporciona la clase ATLPath para manipular las rutas de acceso en forma de [CPathT](cpatht-class.md). Este código puede encontrarse en atlpath.h.

### <a name="related-classes"></a>Clases relacionadas

|||
|-|-|
|[CPathT (clase)](cpatht-class.md)|Esta clase representa una ruta de acceso.|

### <a name="related-typedefs"></a>Definiciones de tipo relacionados

|||
|-|-|
|`CPath`|Una especialización de [CPathT](cpatht-class.md) mediante `CString`.|
|`CPathA`|Una especialización de [CPathT](cpatht-class.md) mediante `CStringA`.|
|`CPathW`|Una especialización de [CPathT](cpatht-class.md) mediante `CStringW`.|

### <a name="functions"></a>Funciones

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|Esta función es un contenedor sobrecargado de [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha).|
|[ATLPath::AddExtension](#addextension)|Esta función es un contenedor sobrecargado de [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona).|
|[ATLPath::Append](#append)|Esta función es un contenedor sobrecargado de [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda).|
|[ATLPath::BuildRoot](#buildroot)|Esta función es un contenedor sobrecargado de [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota).|
|[ATLPath::Canonicalize](#canonicalize)|Esta función es un contenedor sobrecargado de [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea).|
|[ATLPath::Combine](#combine)|Esta función es un contenedor sobrecargado de [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea).|
|[ATLPath::CommonPrefix](#commonprefix)|Esta función es un contenedor sobrecargado de [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa).|
|[ATLPath::CompactPath](#compactpath)|Esta función es un contenedor sobrecargado de [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha).|
|[ATLPath::CompactPathEx](#compactpathex)|Esta función es un contenedor sobrecargado de [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa).|
|[ATLPath::FileExists](#fileexists)|Esta función es un contenedor sobrecargado de [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa).|
|[ATLPath::FindExtension](#findextension)|Esta función es un contenedor sobrecargado de [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona).|
|[ATLPath::FindFileName](#findfilename)|Esta función es un contenedor sobrecargado de [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea).|
|[ATLPath::GetDriveNumber](#getdrivenumber)|Esta función es un contenedor sobrecargado de [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera).|
|[ATLPath::IsDirectory](#isdirectory)|Esta función es un contenedor sobrecargado de [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya).|
|[ATLPath::IsFileSpec](#isfilespec)|Esta función es un contenedor sobrecargado de [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca).|
|[ATLPath::IsPrefix](#isprefix)|Esta función es un contenedor sobrecargado de [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa).|
|[ATLPath::IsRelative](#isrelative)|Esta función es un contenedor sobrecargado de [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea).|
|[ATLPath::IsRoot](#isroot)|Esta función es un contenedor sobrecargado de [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota).|
|[ATLPath::IsSameRoot](#issameroot)|Esta función es un contenedor sobrecargado de [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota).|
|[ATLPath::IsUNC](#isunc)|Esta función es un contenedor sobrecargado de [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca).|
|[ATLPath::IsUNCServer](#isuncserver)|Esta función es un contenedor sobrecargado de [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera).|
|[ATLPath::IsUNCServerShare](#isuncservershare)|Esta función es un contenedor sobrecargado de [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea).|
|[ATLPath::MakePretty](#makepretty)|Esta función es un contenedor sobrecargado de [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya).|
|[ATLPath::MatchSpec](#matchspec)|Esta función es un contenedor sobrecargado de [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca).|
|[ATLPath::QuoteSpaces](#quotespaces)|Esta función es un contenedor sobrecargado de [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa).|
|[ATLPath::RelativePathTo](#relativepathto)|Esta función es un contenedor sobrecargado de [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa).|
|[ATLPath::RemoveArgs](#removeargs)|Esta función es un contenedor sobrecargado de [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa).|
|[ATLPath::RemoveBackslash](#removebackslash)|Esta función es un contenedor sobrecargado de [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha).|
|[ATLPath::RemoveBlanks](#removeblanks)|Esta función es un contenedor sobrecargado de [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa).|
|[ATLPath::RemoveExtension](#removeextension)|Esta función es un contenedor sobrecargado de [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona).|
|[ATLPath::RemoveFileSpec](#removefilespec)|Esta función es un contenedor sobrecargado de [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca).|
|[ATLPath::RenameExtension](#renameextension)|Esta función es un contenedor sobrecargado de [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona).|
|[ATLPath::SkipRoot](#skiproot)|Esta función es un contenedor sobrecargado de [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota).|
|[ATLPath::StripPath](#strippath)|Esta función es un contenedor sobrecargado de [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha).|
|[ATLPath::StripToRoot](#striptoroot)|Esta función es un contenedor sobrecargado de [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota).|
|[ATLPath::UnquoteSpaces](#unquotespaces)|Esta función es un contenedor sobrecargado de [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa).|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlpath.h

## <a name="addbackslash"></a> ATLPath::AddBackSlash

Esta función es un contenedor sobrecargado de [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha).

### <a name="syntax"></a>Sintaxis

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha) para obtener más información.

## <a name="addextension"></a> ATLPath::AddExtension

Esta función es un contenedor sobrecargado de [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona).

### <a name="syntax"></a>Sintaxis

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>Comentarios

Consulte [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona) para obtener más información.

## <a name="append"></a> ATLPath::Append

Esta función es un contenedor sobrecargado de [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda).

### <a name="syntax"></a>Sintaxis

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>Comentarios

Consulte [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda) para obtener más información.

## <a name="buildroot"></a> ATLPath::BuildRoot

Esta función es un contenedor sobrecargado de [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota).

### <a name="syntax"></a>Sintaxis

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>Comentarios

Consulte [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota) para obtener más información.

## <a name="canonicalize"></a> ATLPath::Canonicalize

Esta función es un contenedor sobrecargado de [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea).

### <a name="syntax"></a>Sintaxis

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>Comentarios

Consulte [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea) para obtener más información.

## <a name="combine"></a> ATLPath::Combine

Esta función es un contenedor sobrecargado de [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea).

### <a name="syntax"></a>Sintaxis

```
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

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte PathCombine.

## <a name="commonprefix"></a> ATLPath::CommonPrefix

Esta función es un contenedor sobrecargado de [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa).

### <a name="syntax"></a>Sintaxis

```
inline int CommonPrefix(
   const char* pszFile1,
   const char* pszFile2,
   char* pszDest);

inline int CommonPrefix(
   const wchar_t* pszFile1,
   const wchar_t* pszFile2,
   wchar_t* pszDest);
```

### <a name="remarks"></a>Comentarios

Consulte [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa) para obtener más información.

## <a name="compactpath"></a> ATLPath::CompactPath

Esta función es un contenedor sobrecargado de [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha).

### <a name="syntax"></a>Sintaxis

```
inline BOOL CompactPath(
   HDC hDC,
   char* pszPath,
   UINT dx);

inline BOOL CompactPath(
   HDC hDC,
   wchar_t* pszPath,
   UINT dx);
```

### <a name="remarks"></a>Comentarios

Consulte [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha) para obtener más información.

## <a name="compactpathex"></a> ATLPath::CompactPathEx

Esta función es un contenedor sobrecargado de [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa).

### <a name="syntax"></a>Sintaxis

```
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

### <a name="remarks"></a>Comentarios

Consulte [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa) para obtener más información.

## <a name="fileexists"></a> ATLPath::FileExists

Esta función es un contenedor sobrecargado de [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa).

### <a name="syntax"></a>Sintaxis

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa) para obtener más información.

## <a name="findextension"></a> ATLPath::FindExtension

Esta función es un contenedor sobrecargado de [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona).

### <a name="syntax"></a>Sintaxis

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona) para obtener más información.

## <a name="findfilename"></a> ATLPath::FindFileName

Esta función es un contenedor sobrecargado de [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea).

### <a name="syntax"></a>Sintaxis

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) para obtener más información.

## <a name="getdrivenumber"></a> ATLPath::GetDriveNumber

Esta función es un contenedor sobrecargado de [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera).

### <a name="syntax"></a>Sintaxis

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera) para obtener más información.

## <a name="isdirectory"></a>  ATLPath::IsDirectory

Esta función es un contenedor sobrecargado de [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya).

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte PathIsDirectory.

## <a name="isfilespec"></a> ATLPath::IsFileSpec

Esta función es un contenedor sobrecargado de [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca).

### <a name="syntax"></a>Sintaxis

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca) para obtener más información.

## <a name="isprefix"></a> ATLPath::IsPrefix

Esta función es un contenedor sobrecargado de [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa).

### <a name="syntax"></a>Sintaxis

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa) para obtener más información.

## <a name="isrelative"></a> ATLPath::IsRelative

Esta función es un contenedor sobrecargado de [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea).

### <a name="syntax"></a>Sintaxis

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea) para obtener más información.

## <a name="isroot"></a> ATLPath::IsRoot

Esta función es un contenedor sobrecargado de [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota).

### <a name="syntax"></a>Sintaxis

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota) para obtener más información.

## <a name="issameroot"></a> ATLPath::IsSameRoot

Esta función es un contenedor sobrecargado de [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota).

### <a name="syntax"></a>Sintaxis

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>Comentarios

Consulte [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota) para obtener más información.

## <a name="isunc"></a> ATLPath::IsUNC

Esta función es un contenedor sobrecargado de [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca).

### <a name="syntax"></a>Sintaxis

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca) para obtener más información.

## <a name="isuncserver"></a> ATLPath::IsUNCServer

Esta función es un contenedor sobrecargado de [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera).

### <a name="syntax"></a>Sintaxis

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera) para obtener más información.

## <a name="isuncservershare"></a> ATLPath::IsUNCServerShare

Esta función es un contenedor sobrecargado de [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea).

### <a name="syntax"></a>Sintaxis

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea) para obtener más información.

## <a name="makepretty"></a> ATLPath::MakePretty

Esta función es un contenedor sobrecargado de [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya).

### <a name="syntax"></a>Sintaxis

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya) para obtener más información.

## <a name="matchspec"></a> ATLPath::MatchSpec

Esta función es un contenedor sobrecargado de [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca).

### <a name="syntax"></a>Sintaxis

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>Comentarios

Consulte [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca) para obtener más información.

## <a name="quotespaces"></a> ATLPath::QuoteSpaces

Esta función es un contenedor sobrecargado de [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa).

### <a name="syntax"></a>Sintaxis

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa) para obtener más información.

## <a name="relativepathto"></a> ATLPath::RelativePathTo

Esta función es un contenedor sobrecargado de [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa).

### <a name="syntax"></a>Sintaxis

```
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

### <a name="remarks"></a>Comentarios

Consulte [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa) para obtener más información.

## <a name="removeargs"></a> ATLPath::RemoveArgs

Esta función es un contenedor sobrecargado de [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa).

### <a name="syntax"></a>Sintaxis

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa) para obtener más información.

## <a name="removebackslash"></a> ATLPath::RemoveBackslash

Esta función es un contenedor sobrecargado de [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha).

### <a name="syntax"></a>Sintaxis

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha) para obtener más información.

## <a name="removeblanks"></a> ATLPath::RemoveBlanks

Esta función es un contenedor sobrecargado de [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa).

### <a name="syntax"></a>Sintaxis

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa) para obtener más información.

## <a name="removeextension"></a> ATLPath::RemoveExtension

Esta función es un contenedor sobrecargado de [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona).

### <a name="syntax"></a>Sintaxis

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona) para obtener más información.

## <a name="removefilespec"></a> ATLPath::RemoveFileSpec

Esta función es un contenedor sobrecargado de [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca).

### <a name="syntax"></a>Sintaxis

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca) para obtener más información.

## <a name="renameextension"></a> ATLPath::RenameExtension

Esta función es un contenedor sobrecargado de [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona).

### <a name="syntax"></a>Sintaxis

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>Comentarios

Consulte [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona) para obtener más información.

## <a name="skiproot"></a> ATLPath::SkipRoot

Esta función es un contenedor sobrecargado de [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota).

### <a name="syntax"></a>Sintaxis

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota) para obtener más información.

## <a name="strippath"></a> ATLPath::StripPath

Esta función es un contenedor sobrecargado de [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha).

### <a name="syntax"></a>Sintaxis

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha) para obtener más información.

## <a name="striptoroot"></a> ATLPath::StripToRoot

Esta función es un contenedor sobrecargado de [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota).

### <a name="syntax"></a>Sintaxis

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota) para obtener más información.

## <a name="unquotespaces"></a> ATLPath::UnquoteSpaces

Esta función es un contenedor sobrecargado de [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa).

### <a name="syntax"></a>Sintaxis

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentarios

Consulte [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa) para obtener más información.
