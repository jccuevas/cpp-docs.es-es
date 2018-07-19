---
title: Funciones de ruta de acceso ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad0db4641731f4c92550fad075b759957383c52a
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027582"
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
|[ATLPath::AddBackslash](#addbackslash)|Esta función es un contenedor sobrecargado de [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561).|  
|[ATLPath::AddExtension](#addextension)|Esta función es un contenedor sobrecargado de [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563).|  
|[ATLPath::Append](#append)|Esta función es un contenedor sobrecargado de [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565).|  
|[ATLPath::BuildRoot](#buildroot)|Esta función es un contenedor sobrecargado de [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567).|  
|[ATLPath::Canonicalize](#canonicalize)|Esta función es un contenedor sobrecargado de [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569).|  
|[ATLPath::Combine](#combine)|Esta función es un contenedor sobrecargado de [PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571).|  
|[ATLPath::CommonPrefix](#commonprefix)|Esta función es un contenedor sobrecargado de [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574).|  
|[ATLPath::CompactPath](#compactpath)|Esta función es un contenedor sobrecargado de [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575).|  
|[ATLPath::CompactPathEx](#compactpathex)|Esta función es un contenedor sobrecargado de [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578).|  
|[ATLPath::FileExists](#fileexists)|Esta función es un contenedor sobrecargado de [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584).|  
|[ATLPath::FindExtension](#findextension)|Esta función es un contenedor sobrecargado de [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587).|  
|[ATLPath::FindFileName](#findfilename)|Esta función es un contenedor sobrecargado de [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589).|  
|[ATLPath::GetDriveNumber](#getdrivenumber)|Esta función es un contenedor sobrecargado de [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612).|  
|[ATLPath::IsDirectory](#isdirectory)|Esta función es un contenedor sobrecargado de [PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621).|  
|[ATLPath::IsFileSpec](#isfilespec)|Esta función es un contenedor sobrecargado de [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627).|  
|[ATLPath::IsPrefix](#isprefix)|Esta función es un contenedor sobrecargado de [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650).|  
|[ATLPath::IsRelative](#isrelative)|Esta función es un contenedor sobrecargado de [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660).|  
|[ATLPath::IsRoot](#isroot)|Esta función es un contenedor sobrecargado de [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674).|  
|[ATLPath::IsSameRoot](#issameroot)|Esta función es un contenedor sobrecargado de [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687).|  
|[ATLPath::IsUNC](#isunc)|Esta función es un contenedor sobrecargado de [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712).|  
|[ATLPath::IsUNCServer](#isuncserver)|Esta función es un contenedor sobrecargado de [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722).|  
|[ATLPath::IsUNCServerShare](#isuncservershare)|Esta función es un contenedor sobrecargado de [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723).|  
|[ATLPath::MakePretty](#makepretty)|Esta función es un contenedor sobrecargado de [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725).|  
|[ATLPath::MatchSpec](#matchspec)|Esta función es un contenedor sobrecargado de [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727).|  
|[ATLPath::QuoteSpaces](#quotespaces)|Esta función es un contenedor sobrecargado de [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739).|  
|[ATLPath::RelativePathTo](#relativepathto)|Esta función es un contenedor sobrecargado de [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740).|  
|[ATLPath::RemoveArgs](#removeargs)|Esta función es un contenedor sobrecargado de [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742).|  
|[ATLPath::RemoveBackslash](#removebackslash)|Esta función es un contenedor sobrecargado de [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743).|  
|[ATLPath::RemoveBlanks](#removeblanks)|Esta función es un contenedor sobrecargado de [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745).|  
|[ATLPath::RemoveExtension](#removeextension)|Esta función es un contenedor sobrecargado de [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746).|  
|[ATLPath::RemoveFileSpec](#removefilespec)|Esta función es un contenedor sobrecargado de [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748).|  
|[ATLPath::RenameExtension](#renameextension)|Esta función es un contenedor sobrecargado de [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749).|  
|[ATLPath::SkipRoot](#skiproot)|Esta función es un contenedor sobrecargado de [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754).|  
|[ATLPath::StripPath](#strippath)|Esta función es un contenedor sobrecargado de [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756).|  
|[ATLPath::StripToRoot](#striptoroot)|Esta función es un contenedor sobrecargado de [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757).|  
|[ATLPath::UnquoteSpaces](#unquotespaces)|Esta función es un contenedor sobrecargado de [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763).|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlpath.h  

## <a name="addbackslash"></a> ATLPath::AddBackSlash

Esta función es un contenedor sobrecargado de [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline char* AddBackslash(char* pszPath);  
inline wchar_t* AddBackslash(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561) para obtener más información.  
  
 
  

## <a name="addextension"></a> ATLPath::AddExtension
 Esta función es un contenedor sobrecargado de [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL AddExtension(char* pszPath, const char* pszExtension);  
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563) para obtener más información. 
  
## <a name="append"></a> ATLPath::Append
 Esta función es un contenedor sobrecargado de [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL Append(char* pszPath, const char* pszMore);  
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565) para obtener más información.  
  
 
  

## <a name="buildroot"></a> ATLPath::BuildRoot
 Esta función es un contenedor sobrecargado de [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline char* BuildRoot(char* pszPath, int iDrive);  
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567) para obtener más información.  
  
 
  

## <a name="canonicalize"></a> ATLPath::Canonicalize
 Esta función es un contenedor sobrecargado de [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);  
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569) para obtener más información.  
  
 
  

## <a name="combine"></a> ATLPath::Combine 
Esta función es un contenedor sobrecargado de [PathCombine](https://msdn.microsoft.com/library/windows/desktop/bb773571).  

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
 Esta función es un contenedor sobrecargado de [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574).  
  
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
 Consulte [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574) para obtener más información.  
  
 
  

## <a name="compactpath"></a> ATLPath::CompactPath
 Esta función es un contenedor sobrecargado de [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575).  
  
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
 Consulte [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575) para obtener más información.  
  
 
  

## <a name="compactpathex"></a> ATLPath::CompactPathEx
 Esta función es un contenedor sobrecargado de [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578).  
  
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
 Consulte [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578) para obtener más información.  
  
 
  

## <a name="fileexists"></a> ATLPath::FileExists
 Esta función es un contenedor sobrecargado de [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL FileExists(const char* pszPath);  
inline BOOL FileExists(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584) para obtener más información.  
  
 
  

## <a name="findextension"></a> ATLPath::FindExtension
 Esta función es un contenedor sobrecargado de [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline char* FindExtension(const char* pszPath);  
inline wchar_t* FindExtension(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587) para obtener más información.  
  
 
  

## <a name="findfilename"></a> ATLPath::FindFileName
 Esta función es un contenedor sobrecargado de [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline char* FindFileName(const char* pszPath);  
inline wchar_t* FindFileName(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589) para obtener más información.  
  
 
  

## <a name="getdrivenumber"></a> ATLPath::GetDriveNumber  
 Esta función es un contenedor sobrecargado de [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline int GetDriveNumber(const char* pszPath);  
inline int GetDriveNumber(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612) para obtener más información.  
  
 


## <a name="isdirectory"></a>  ATLPath::IsDirectory 
Esta función es un contenedor sobrecargado de [PathIsDirectory](https://msdn.microsoft.com/library/windows/desktop/bb773621).

```  
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```  
### <a name="remarks"></a>Comentarios
Para obtener más información, consulte PathIsDirectory.  

## <a name="isfilespec"></a> ATLPath::IsFileSpec
 Esta función es un contenedor sobrecargado de [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL IsFileSpec(const char* pszPath);  
inline BOOL IsFileSpec(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627) para obtener más información.  
  
 
  

## <a name="isprefix"></a> ATLPath::IsPrefix
 Esta función es un contenedor sobrecargado de [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);  
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650) para obtener más información.  
  
 
  

## <a name="isrelative"></a> ATLPath::IsRelative
 Esta función es un contenedor sobrecargado de [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL IsRelative(const char* pszPath);  
inline BOOL IsRelative(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660) para obtener más información.  
  
 
  

## <a name="isroot"></a> ATLPath::IsRoot
 Esta función es un contenedor sobrecargado de [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL IsRoot(const char* pszPath);  
inline BOOL IsRoot(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674) para obtener más información.  
  
 
  

## <a name="issameroot"></a> ATLPath::IsSameRoot
 Esta función es un contenedor sobrecargado de [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);  
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687) para obtener más información.  
  
 
  

## <a name="isunc"></a> ATLPath::IsUNC
 Esta función es un contenedor sobrecargado de [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL IsUNC(const char* pszPath);  
inline BOOL IsUNC(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712) para obtener más información.  
  
 
  

## <a name="isuncserver"></a> ATLPath::IsUNCServer
 Esta función es un contenedor sobrecargado de [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL IsUNCServer(const char* pszPath);  
inline BOOL IsUNCServer(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722) para obtener más información.  
  
 
  

## <a name="isuncservershare"></a> ATLPath::IsUNCServerShare
 Esta función es un contenedor sobrecargado de [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL IsUNCServerShare(const char* pszPath);  
inline BOOL IsUNCServerShare(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723) para obtener más información.  
  
 
  

## <a name="makepretty"></a> ATLPath::MakePretty
 Esta función es un contenedor sobrecargado de [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL MakePretty(char* pszPath);  
inline BOOL MakePretty(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725) para obtener más información.  
  
 
  

## <a name="matchspec"></a> ATLPath::MatchSpec  
 Esta función es un contenedor sobrecargado de [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);  
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727) para obtener más información.  
  
 
  

## <a name="quotespaces"></a> ATLPath::QuoteSpaces  
 Esta función es un contenedor sobrecargado de [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline void QuoteSpaces(char* pszPath);  
inline void QuoteSpaces(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739) para obtener más información.  
  
 
  

## <a name="relativepathto"></a> ATLPath::RelativePathTo
 Esta función es un contenedor sobrecargado de [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740).  
  
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
 Consulte [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740) para obtener más información.  
  
 
  

## <a name="removeargs"></a> ATLPath::RemoveArgs  
 Esta función es un contenedor sobrecargado de [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline void RemoveArgs(char* pszPath);  
inline void RemoveArgs(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742) para obtener más información.  
  
 
  

## <a name="removebackslash"></a> ATLPath::RemoveBackslash
 Esta función es un contenedor sobrecargado de [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline char* RemoveBackslash(char* pszPath);  
inline wchar_t* RemoveBackslash(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743) para obtener más información.  
  
 
  

## <a name="removeblanks"></a> ATLPath::RemoveBlanks
 Esta función es un contenedor sobrecargado de [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline void RemoveBlanks(char* pszPath);  
inline void RemoveBlanks(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745) para obtener más información.  
  
 
  

## <a name="removeextension"></a> ATLPath::RemoveExtension
 Esta función es un contenedor sobrecargado de [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline void RemoveExtension(char* pszPath);  
inline void RemoveExtension(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746) para obtener más información.  
  
 
  

## <a name="removefilespec"></a> ATLPath::RemoveFileSpec
 Esta función es un contenedor sobrecargado de [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL RemoveFileSpec(char* pszPath);  
inline BOOL RemoveFileSpec(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748) para obtener más información.  
  
 
  

## <a name="renameextension"></a> ATLPath::RenameExtension
 Esta función es un contenedor sobrecargado de [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL RenameExtension(char* pszPath, const char* pszExt);  
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749) para obtener más información.  
  
 
  

## <a name="skiproot"></a> ATLPath::SkipRoot
 Esta función es un contenedor sobrecargado de [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline char* SkipRoot(const char* pszPath);  
inline wchar_t* SkipRoot(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754) para obtener más información.  
  
 
  

## <a name="strippath"></a> ATLPath::StripPath
 Esta función es un contenedor sobrecargado de [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline void StripPath(char* pszPath);  
inline void StripPath(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756) para obtener más información.  
  
 
  


## <a name="striptoroot"></a> ATLPath::StripToRoot
 Esta función es un contenedor sobrecargado de [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline BOOL StripToRoot(char* pszPath);  
inline BOOL StripToRoot(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757) para obtener más información.  
  
 
  

## <a name="unquotespaces"></a> ATLPath::UnquoteSpaces
 Esta función es un contenedor sobrecargado de [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
inline void UnquoteSpaces(char* pszPath);  
inline void UnquoteSpaces(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763) para obtener más información.  
  
 
  
 
