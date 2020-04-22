---
title: Clase CPathT
ms.date: 03/27/2019
f1_keywords:
- CPathT
- ATLPATH/ATL::CPathT
- ATLPATH/ATL::CPathT::PCXSTR
- ATLPATH/ATL::CPathT::PXSTR
- ATLPATH/ATL::CPathT::XCHAR
- ATLPATH/ATL::CPathT::CPathT
- ATLPATH/ATL::CPathT::AddBackslash
- ATLPATH/ATL::CPathT::AddExtension
- ATLPATH/ATL::CPathT::Append
- ATLPATH/ATL::CPathT::BuildRoot
- ATLPATH/ATL::CPathT::Canonicalize
- ATLPATH/ATL::CPathT::Combine
- ATLPATH/ATL::CPathT::CommonPrefix
- ATLPATH/ATL::CPathT::CompactPath
- ATLPATH/ATL::CPathT::CompactPathEx
- ATLPATH/ATL::CPathT::FileExists
- ATLPATH/ATL::CPathT::FindExtension
- ATLPATH/ATL::CPathT::FindFileName
- ATLPATH/ATL::CPathT::GetDriveNumber
- ATLPATH/ATL::CPathT::GetExtension
- ATLPATH/ATL::CPathT::IsDirectory
- ATLPATH/ATL::CPathT::IsFileSpec
- ATLPATH/ATL::CPathT::IsPrefix
- ATLPATH/ATL::CPathT::IsRelative
- ATLPATH/ATL::CPathT::IsRoot
- ATLPATH/ATL::CPathT::IsSameRoot
- ATLPATH/ATL::CPathT::IsUNC
- ATLPATH/ATL::CPathT::IsUNCServer
- ATLPATH/ATL::CPathT::IsUNCServerShare
- ATLPATH/ATL::CPathT::MakePretty
- ATLPATH/ATL::CPathT::MatchSpec
- ATLPATH/ATL::CPathT::QuoteSpaces
- ATLPATH/ATL::CPathT::RelativePathTo
- ATLPATH/ATL::CPathT::RemoveArgs
- ATLPATH/ATL::CPathT::RemoveBackslash
- ATLPATH/ATL::CPathT::RemoveBlanks
- ATLPATH/ATL::CPathT::RemoveExtension
- ATLPATH/ATL::CPathT::RemoveFileSpec
- ATLPATH/ATL::CPathT::RenameExtension
- ATLPATH/ATL::CPathT::SkipRoot
- ATLPATH/ATL::CPathT::StripPath
- ATLPATH/ATL::CPathT::StripToRoot
- ATLPATH/ATL::CPathT::UnquoteSpaces
- ATLPATH/ATL::CPathT::m_strPath
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
ms.openlocfilehash: c10b854ae5c2d7167a067675b1391be24b6a8122
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746594"
---
# <a name="cpatht-class"></a>Clase CPathT

Esta clase representa una ruta de acceso.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>Parámetros

*StringType*<br/>
La clase de cadena ATL/MFC que se va a utilizar para la ruta de acceso (consulte [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)).

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CpathT::PCXSTR](#pcxstr)|Un tipo de cadena constante.|
|[Cpatht::PXSTR](#pxstr)|Tipo string.|
|[CpathT::XCHAR](#xchar)|Tipo de carácter.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Cpatht::CpathT](#cpatht)|El constructor de la ruta de acceso.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPathT::AddBackslash](#addbackslash)|Llame a este método para agregar una barra diagonal inversa al final de una cadena para crear la sintaxis correcta para una ruta de acceso.|
|[CPathT::AddExtension](#addextension)|Llame a este método para agregar una extensión de archivo a una ruta de acceso.|
|[CPathT::Append](#append)|Llame a este método para anexar una cadena a la ruta de acceso actual.|
|[CpathT::BuildRoot](#buildroot)|Llame a este método para crear una ruta de acceso raíz a partir de un número de unidad determinado.|
|[CPathT::Canonicalize](#canonicalize)|Llame a este método para convertir la ruta de acceso a forma canónica.|
|[CPathT::Combinar](#combine)|Llame a este método para concatenar una cadena que representa un nombre de directorio y una cadena que representa un nombre de ruta de acceso de archivo en una ruta de acceso.|
|[CPathT::CommonPrefix](#commonprefix)|Llame a este método para determinar si la ruta de acceso especificada comparte un prefijo común con la ruta de acceso actual.|
|[CPathT::CompactPath](#compactpath)|Llame a este método para truncar una ruta de acceso de archivo para que quepa dentro de un ancho de píxel determinado reemplazando los componentes de ruta de acceso con elipses.|
|[CPathT::CompactPathEx](#compactpathex)|Llame a este método para truncar una ruta de acceso de archivo para que quepa dentro de un número determinado de caracteres reemplazando los componentes de ruta de acceso por elipses.|
|[CPathT::FileExists](#fileexists)|Llame a este método para comprobar si existe el archivo en este nombre de ruta de acceso.|
|[CpathT::FindExtension](#findextension)|Llame a este método para encontrar la posición de la extensión de archivo dentro de la ruta de acceso.|
|[CPathT::FindFileName](#findfilename)|Llame a este método para encontrar la posición del nombre de archivo dentro de la ruta de acceso.|
|[CPathT::GetDriveNumber](#getdrivenumber)|Llame a este método para buscar en la ruta de acceso una letra de unidad dentro del rango de 'A' a 'Z' y devolver el número de unidad correspondiente.|
|[CPathT::GetExtension](#getextension)|Llame a este método para obtener la extensión de archivo de la ruta de acceso.|
|[CpathT::IsDirectory](#isdirectory)|Llame a este método para comprobar si la ruta de acceso es un directorio válido.|
|[CpathT::IsfileSpec](#isfilespec)|Llame a este método para buscar en una ruta de acceso cualquier\\carácter delimitador de ruta de acceso (por ejemplo, ':' o ' ' ). Si no hay caracteres delimitadores de ruta de acceso presentes, la ruta de acceso se considera una ruta de acceso de especificación de archivo.|
|[CpathT::IsPrefix](#isprefix)|Llame a este método para determinar si una ruta de acceso contiene un prefijo válido del tipo pasado por *pszPrefix*.|
|[Cpatht::IsRelative](#isrelative)|Llame a este método para determinar si la ruta de acceso es relativa.|
|[Cpatht::Isroot](#isroot)|Llame a este método para determinar si la ruta de acceso es una raíz de directorio.|
|[Cpatht::IsSameRoot](#issameroot)|Llame a este método para determinar si otra ruta de acceso tiene un componente raíz común con la ruta de acceso actual.|
|[Cpatht::IsUNC](#isunc)|Llame a este método para determinar si la ruta de acceso es una ruta de acceso UNC (convención de nomenclatura universal) válida para un servidor y recurso compartido.|
|[CPathT::IsUNCServer](#isuncserver)|Llame a este método para determinar si la ruta de acceso es una ruta de acceso UNC (convención de nomenclatura universal) válida solo para un servidor.|
|[CpathT::IsUNCServerShare](#isuncservershare)|Llame a este método para determinar si la ruta de acceso \\ \ es una ruta de acceso de recurso compartido UNC (convención de nomenclatura universal) válida,*recurso compartido*de *servidor*\ .|
|[Cpatht::MakePretty](#makepretty)|Llame a este método para convertir una ruta de acceso a todos los caracteres en minúsculas para dar a la ruta de acceso una apariencia coherente.|
|[CPathT::MatchSpec](#matchspec)|Llame a este método para buscar en la ruta de acceso una cadena que contenga un tipo de coincidencia comodín.|
|[CpathT::QuoteSpaces](#quotespaces)|Llame a este método para incluir la ruta entre comillas si contiene espacios.|
|[Cpatht::RelativepathTo](#relativepathto)|Llame a este método para crear una ruta de acceso relativa de un archivo o carpeta a otro.|
|[CPathT::RemoveArgs](#removeargs)|Llame a este método para quitar los argumentos de línea de comandos de la ruta de acceso.|
|[CPathT::RemoveBackslash](#removebackslash)|Llame a este método para quitar la barra diagonal inversa final de la ruta de acceso.|
|[CPathT::RemoveBlanks](#removeblanks)|Llame a este método para quitar todos los espacios iniciales y finales de la ruta de acceso.|
|[CPathT::RemoveExtension](#removeextension)|Llame a este método para quitar la extensión de archivo de la ruta de acceso, si hay uno.|
|[CpathT::RemoveFileSpec](#removefilespec)|Llame a este método para quitar el nombre de archivo final y la barra diagonal inversa de la ruta de acceso, si los tiene.|
|[CPathT::RenameExtension](#renameextension)|Llame a este método para reemplazar la extensión de nombre de archivo en la ruta de acceso con una nueva extensión. Si el nombre de archivo no contiene una extensión, la extensión se adjuntará al final de la cadena.|
|[CpathT::SkipRoot](#skiproot)|Llame a este método para analizar una ruta de acceso, ignorando la letra de unidad o las partes de ruta de acceso UNC/share.|
|[CpathT::StripPath](#strippath)|Llame a este método para quitar la parte de ruta de acceso de una ruta de acceso completa y el nombre de archivo.|
|[Cpatht::StripToRoot](#striptoroot)|Llame a este método para quitar todas las partes de la ruta de acceso, excepto la información raíz.|
|[CpathT::UnquoteSpaces](#unquotespaces)|Llame a este método para quitar comillas desde el principio y el final de una ruta de acceso.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPathT::operator const StringType &](#operator_const_stringtype_amp)|Este operador permite que el objeto se trate como una cadena.|
|[CPathT::operador CPathT::PCXSTR](#operator_cpatht__pcxstr)|Este operador permite que el objeto se trate como una cadena.|
|[CPathT::operator StringType &](#operator_stringtype_amp)|Este operador permite que el objeto se trate como una cadena.|
|[CPathT::operador +](#operator_add_eq)|Este operador anexa una cadena a la ruta de acceso.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Cpatht::m_strPath](#m_strpath)|La ruta de acceso.|

## <a name="remarks"></a>Observaciones

`CPath`, `CPathA`, `CPathW` y son instancias de `CPathT` definido según sigue:

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlpath.h

## <a name="cpathtaddbackslash"></a><a name="addbackslash"></a>CPathT::AddBackslash

Llame a este método para agregar una barra diagonal inversa al final de una cadena para crear la sintaxis correcta para una ruta de acceso. Si la ruta de acceso ya tiene una barra diagonal inversa final, no se agregará ninguna barra diagonal inversa.

```cpp
void AddBackslash();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathAddBackSlash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

## <a name="cpathtaddextension"></a><a name="addextension"></a>CPathT::AddExtension

Llame a este método para agregar una extensión de archivo a una ruta de acceso.

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parámetros

*pszExtension*<br/>
La extensión de archivo que se va a agregar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

## <a name="cpathtappend"></a><a name="append"></a>CPathT::Append

Llame a este método para anexar una cadena a la ruta de acceso actual.

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>Parámetros

*pszMás*<br/>
Cadena que se va a anexar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

## <a name="cpathtbuildroot"></a><a name="buildroot"></a>CpathT::BuildRoot

Llame a este método para crear una ruta de acceso raíz a partir de un número de unidad determinado.

```cpp
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>Parámetros

*Idrive*<br/>
El número de unidad (0 es A:, 1 es B:, y así sucesivamente).

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

## <a name="cpathtcanonicalize"></a><a name="canonicalize"></a>CPathT::Canonicalize

Llame a este método para convertir la ruta de acceso a forma canónica.

```cpp
void Canonicalize();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

## <a name="cpathtcombine"></a><a name="combine"></a>CPathT::Combinar

Llame a este método para concatenar una cadena que representa un nombre de directorio y una cadena que representa un nombre de ruta de acceso de archivo en una ruta de acceso.

```cpp
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>Parámetros

*pszDir*<br/>
Ruta de acceso al directorio.

*pszFile*<br/>
La ruta de acceso del archivo.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

## <a name="cpathtcommonprefix"></a><a name="commonprefix"></a>CPathT::CommonPrefix

Llame a este método para determinar si la ruta de acceso especificada comparte un prefijo común con la ruta de acceso actual.

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>Parámetros

*pszOtros*<br/>
La ruta de acceso para comparar con la actual.

### <a name="return-value"></a>Valor devuelto

Devuelve el prefijo común.

### <a name="remarks"></a>Observaciones

Un prefijo es uno de estos\\\\tipos: "C: ", ".", "..", ".... \\\\". Para obtener más información, vea [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

## <a name="cpathtcompactpath"></a><a name="compactpath"></a>CPathT::CompactPath

Llame a este método para truncar una ruta de acceso de archivo para que quepa dentro de un ancho de píxel determinado reemplazando los componentes de ruta de acceso con elipses.

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>Parámetros

*Hdc*<br/>
El contexto del dispositivo utilizado para las métricas de fuente.

*nAncho*<br/>
El ancho, en píxeles, que la cadena se verá obligado a encajar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

## <a name="cpathtcompactpathex"></a><a name="compactpathex"></a>CPathT::CompactPathEx

Llame a este método para truncar una ruta de acceso de archivo para que quepa dentro de un número determinado de caracteres reemplazando los componentes de ruta de acceso por elipses.

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parámetros

*nMaxChars*<br/>
El número máximo de caracteres que se van a incluir en la nueva cadena, incluido el carácter NULL de terminación.

*dwFlags*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

## <a name="cpathtcpatht"></a><a name="cpatht"></a>Cpatht::CpathT

El constructor.

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>Parámetros

*pszPath*<br/>
El puntero a una cadena de ruta de acceso.

*path*<br/>
La cadena de ruta de acceso.

## <a name="cpathtfileexists"></a><a name="fileexists"></a>CPathT::FileExists

Llame a este método para comprobar si existe el archivo en este nombre de ruta de acceso.

```
BOOL FileExists() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el archivo existe, FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

## <a name="cpathtfindextension"></a><a name="findextension"></a>CpathT::FindExtension

Llame a este método para encontrar la posición de la extensión de archivo dentro de la ruta de acceso.

```
int FindExtension() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del "." anterior a la extensión. Si no se encuentra ninguna extensión, devuelve -1.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

## <a name="cpathtfindfilename"></a><a name="findfilename"></a>CPathT::FindFileName

Llame a este método para encontrar la posición del nombre de archivo dentro de la ruta de acceso.

```
int FindFileName() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del nombre de archivo. Si no se encuentra ningún nombre de archivo, devuelve -1.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

## <a name="cpathtgetdrivenumber"></a><a name="getdrivenumber"></a>CPathT::GetDriveNumber

Llame a este método para buscar en la ruta de acceso una letra de unidad dentro del rango de 'A' a 'Z' y devolver el número de unidad correspondiente.

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de unidad como un entero de 0 a 25 (correspondiente a 'A' a 'Z') si la ruta de acceso tiene una letra de unidad, o -1 en caso contrario.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

## <a name="cpathtgetextension"></a><a name="getextension"></a>CPathT::GetExtension

Llame a este método para obtener la extensión de archivo de la ruta de acceso.

```
StringType GetExtension() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve la extensión de archivo.

## <a name="cpathtisdirectory"></a><a name="isdirectory"></a>CpathT::IsDirectory

Llame a este método para comprobar si la ruta de acceso es un directorio válido.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero (16) si la ruta de acceso es un directorio, FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

## <a name="cpathtisfilespec"></a><a name="isfilespec"></a>CpathT::IsfileSpec

Llame a este método para buscar en una ruta de acceso cualquier\\carácter delimitador de ruta de acceso (por ejemplo, ':' o ' ' ). Si no hay caracteres delimitadores de ruta de acceso presentes, la ruta de acceso se considera una ruta de acceso de especificación de archivo.

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si no hay caracteres delimitadores de ruta de acceso dentro de la ruta de acceso, o FALSE si hay caracteres delimitadores de ruta de acceso.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

## <a name="cpathtisprefix"></a><a name="isprefix"></a>CpathT::IsPrefix

Llame a este método para determinar si una ruta de acceso contiene un prefijo válido del tipo pasado por *pszPrefix*.

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>Parámetros

*pszPrefix*<br/>
El prefijo para el que se va a buscar. Un prefijo es uno de estos\\\\tipos: "C: ", ".", "..", ".... \\\\".

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso contiene el prefijo o FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

## <a name="cpathtisrelative"></a><a name="isrelative"></a>Cpatht::IsRelative

Llame a este método para determinar si la ruta de acceso es relativa.

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso es relativa o FALSE si es absoluta.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

## <a name="cpathtisroot"></a><a name="isroot"></a>Cpatht::Isroot

Llame a este método para determinar si la ruta de acceso es una raíz de directorio.

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso es una raíz o FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

## <a name="cpathtissameroot"></a><a name="issameroot"></a>Cpatht::IsSameRoot

Llame a este método para determinar si otra ruta de acceso tiene un componente raíz común con la ruta de acceso actual.

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>Parámetros

*pszOtros*<br/>
El otro camino.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si ambas cadenas tienen el mismo componente raíz, o FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

## <a name="cpathtisunc"></a><a name="isunc"></a>Cpatht::IsUNC

Llame a este método para determinar si la ruta de acceso es una ruta de acceso UNC (convención de nomenclatura universal) válida para un servidor y recurso compartido.

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso es una ruta de acceso UNC válida, o FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

## <a name="cpathtisuncserver"></a><a name="isuncserver"></a>CPathT::IsUNCServer

Llame a este método para determinar si la ruta de acceso es una ruta de acceso UNC (convención de nomenclatura universal) válida solo para un servidor.

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la cadena es una ruta de acceso UNC válida solo para un servidor (sin nombre de recurso compartido) o FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

## <a name="cpathtisuncservershare"></a><a name="isuncservershare"></a>CpathT::IsUNCServerShare

Llame a este método para determinar si la ruta de acceso \\ \ es una ruta de acceso de recurso compartido UNC (convención de nomenclatura universal) válida,*recurso compartido*de *servidor*\ .

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta \\ \ de acceso está en el*recurso compartido*de *servidor*\ de formularios o FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

## <a name="cpathtm_strpath"></a><a name="m_strpath"></a>Cpatht::m_strPath

La ruta de acceso.

```
StringType m_strPath;
```

### <a name="remarks"></a>Observaciones

`StringType`es el parámetro `CPathT`de plantilla para .

## <a name="cpathtmakepretty"></a><a name="makepretty"></a>Cpatht::MakePretty

Llame a este método para convertir una ruta de acceso a todos los caracteres en minúsculas para dar a la ruta de acceso una apariencia coherente.

```
BOOL MakePretty();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso se ha convertido, o FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

## <a name="cpathtmatchspec"></a><a name="matchspec"></a>CPathT::MatchSpec

Llame a este método para buscar en la ruta de acceso una cadena que contenga un tipo de coincidencia comodín.

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>Parámetros

*pszSpec*<br/>
Puntero a una cadena terminada en null con el tipo de archivo para el que se va a buscar. Por ejemplo, para probar si el archivo en la ruta de acceso actual es un archivo DOC, *pszSpec* debe establecerse en "*.doc".

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la cadena coincide, o FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

## <a name="cpathtoperator-"></a><a name="operator_add_eq"></a>CPathT::operador +

Este operador anexa una cadena a la ruta de acceso.

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>Parámetros

*pszMás*<br/>
Cadena que se va a anexar.

### <a name="return-value"></a>Valor devuelto

Devuelve la ruta de acceso actualizada.

## <a name="cpathtoperator-const-stringtype-amp"></a><a name="operator_const_stringtype_amp"></a>CPathT::operator const StringType&amp;

Este operador permite que el objeto se trate como una cadena.

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una cadena que representa la ruta de acceso actual administrada por este objeto.

## <a name="cpathtoperator-cpathtpcxstr"></a><a name="operator_cpatht__pcxstr"></a>CPathT::operador CPathT::PCXSTR

Este operador permite que el objeto se trate como una cadena.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una cadena que representa la ruta de acceso actual administrada por este objeto.

## <a name="cpathtoperator-stringtype-amp"></a><a name="operator_stringtype_amp"></a>CPathT::operator StringType&amp;

Este operador permite que el objeto se trate como una cadena.

```
operator StringType&() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una cadena que representa la ruta de acceso actual administrada por este objeto.

## <a name="cpathtpcxstr"></a><a name="pcxstr"></a>CpathT::PCXSTR

Un tipo de cadena constante.

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>Observaciones

`StringType`es el parámetro `CPathT`de plantilla para .

## <a name="cpathtpxstr"></a><a name="pxstr"></a>Cpatht::PXSTR

Tipo string.

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>Observaciones

`StringType`es el parámetro `CPathT`de plantilla para .

## <a name="cpathtquotespaces"></a><a name="quotespaces"></a>CpathT::QuoteSpaces

Llame a este método para incluir la ruta entre comillas si contiene espacios.

```cpp
void QuoteSpaces();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

## <a name="cpathtrelativepathto"></a><a name="relativepathto"></a>Cpatht::RelativepathTo

Llame a este método para crear una ruta de acceso relativa de un archivo o carpeta a otro.

```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```

### <a name="parameters"></a>Parámetros

*pszFrom*<br/>
El inicio de la ruta relativa.

*dwAttrFrom*<br/>
Los atributos File de *pszFrom*. Si este valor contiene FILE_ATTRIBUTE_DIRECTORY, se supone que *pszFrom* es un directorio; de lo contrario, se supone *que pszFrom* es un archivo.

*pszTo*<br/>
El punto final de la ruta de acceso relativa.

*dwAttrTo*<br/>
Los atributos File de *pszTo*. Si este valor contiene FILE_ATTRIBUTE_DIRECTORY, se supone que *pszTo* es un directorio; de lo contrario, se supone que *pszTo* es un archivo.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

## <a name="cpathtremoveargs"></a><a name="removeargs"></a>CPathT::RemoveArgs

Llame a este método para quitar los argumentos de línea de comandos de la ruta de acceso.

```cpp
void RemoveArgs();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

## <a name="cpathtremovebackslash"></a><a name="removebackslash"></a>CPathT::RemoveBackslash

Llame a este método para quitar la barra diagonal inversa final de la ruta de acceso.

```cpp
void RemoveBackslash();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

## <a name="cpathtremoveblanks"></a><a name="removeblanks"></a>CPathT::RemoveBlanks

Llame a este método para quitar todos los espacios iniciales y finales de la ruta de acceso.

```cpp
void RemoveBlanks();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

## <a name="cpathtremoveextension"></a><a name="removeextension"></a>CPathT::RemoveExtension

Llame a este método para quitar la extensión de archivo de la ruta de acceso, si hay uno.

```cpp
void RemoveExtension();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

## <a name="cpathtremovefilespec"></a><a name="removefilespec"></a>CpathT::RemoveFileSpec

Llame a este método para quitar el nombre de archivo final y la barra diagonal inversa de la ruta de acceso, si los tiene.

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

## <a name="cpathtrenameextension"></a><a name="renameextension"></a>CPathT::RenameExtension

Llame a este método para reemplazar la extensión de nombre de archivo en la ruta de acceso con una nueva extensión. Si el nombre de archivo no contiene una extensión, la extensión se adjuntará al final de la ruta de acceso.

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parámetros

*pszExtension*<br/>
La nueva extensión de nombre de archivo, precedida por un carácter ".".

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

## <a name="cpathtskiproot"></a><a name="skiproot"></a>CpathT::SkipRoot

Llame a este método para analizar una ruta de acceso, ignorando la letra de unidad o las partes de ruta de acceso de servidor/recurso compartido UNC (convención de nomenclatura universal).

```
int SkipRoot() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del principio de la subruta que sigue a la raíz (letra de unidad o servidor/recurso compartido UNC).

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

## <a name="cpathtstrippath"></a><a name="strippath"></a>CpathT::StripPath

Llame a este método para quitar la parte de ruta de acceso de una ruta de acceso completa y el nombre de archivo.

```cpp
void StripPath();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

## <a name="cpathtstriptoroot"></a><a name="striptoroot"></a>Cpatht::StripToRoot

Llame a este método para quitar todas las partes de la ruta de acceso, excepto la información raíz.

```
BOOL StripToRoot();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se encontró una letra de unidad válida en la ruta de acceso, o FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

## <a name="cpathtunquotespaces"></a><a name="unquotespaces"></a>CpathT::UnquoteSpaces

Llame a este método para quitar comillas desde el principio y el final de una ruta de acceso.

```cpp
void UnquoteSpaces();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

## <a name="cpathtxchar"></a><a name="xchar"></a>CpathT::XCHAR

Tipo de carácter.

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>Observaciones

`StringType`es el parámetro `CPathT`de plantilla para .

## <a name="see-also"></a>Vea también

[Clases](../../atl/reference/atl-classes.md)<br/>
[Clase CStringT](../../atl-mfc-shared/reference/cstringt-class.md)
