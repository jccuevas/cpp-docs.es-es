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
ms.openlocfilehash: ba1c831d772deef34449d17adc2c8e7a6f90eaef
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "69496616"
---
# <a name="cpatht-class"></a>Clase CPathT

Esta clase representa una ruta de acceso.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>Parámetros

*StringType*<br/>
Clase de cadena de ATL/MFC que se va a utilizar para la ruta de acceso (vea [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)).

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|[CPathT::P CXSTR](#pcxstr)|Tipo de cadena de constante.|
|[CPathT::P XSTR](#pxstr)|Tipo de cadena.|
|[CPathT::XCHAR](#xchar)|Tipo de carácter.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CPathT::CPathT](#cpatht)|Constructor para la ruta de acceso.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CPathT::AddBackslash](#addbackslash)|Llame a este método para agregar una barra diagonal inversa al final de una cadena con el fin de crear la sintaxis correcta para una ruta de acceso.|
|[CPathT::AddExtension](#addextension)|Llame a este método para agregar una extensión de archivo a una ruta de acceso.|
|[CPathT:: Append](#append)|Llame a este método para anexar una cadena a la ruta de acceso actual.|
|[CPathT:: objeto buildroot](#buildroot)|Llame a este método para crear una ruta de acceso raíz a partir de un número de unidad determinado.|
|[CPathT:: Canonicalization](#canonicalize)|Llame a este método para convertir la ruta de acceso al formato canónico.|
|[CPathT:: Combine](#combine)|Llame a este método para concatenar una cadena que represente un nombre de directorio y una cadena que represente un nombre de ruta de acceso de archivo en una ruta de acceso.|
|[CPathT::CommonPrefix](#commonprefix)|Llame a este método para determinar si la ruta de acceso especificada comparte un prefijo común con la ruta de acceso actual.|
|[CPathT::CompactPath](#compactpath)|Llame a este método para truncar una ruta de acceso de archivo para ajustarse a un ancho de píxel determinado reemplazando los componentes de la ruta de acceso con puntos suspensivos.|
|[CPathT::CompactPathEx](#compactpathex)|Llame a este método para truncar una ruta de acceso de archivo para ajustarse a un número determinado de caracteres reemplazando los componentes de la ruta de acceso con puntos suspensivos.|
|[CPathT:: FileExists](#fileexists)|Llame a este método para comprobar si existe el archivo en este nombre de ruta de acceso.|
|[CPathT::FindExtension](#findextension)|Llame a este método para buscar la posición de la extensión de archivo dentro de la ruta de acceso.|
|[CPathT::FindFileName](#findfilename)|Llame a este método para buscar la posición del nombre de archivo dentro de la ruta de acceso.|
|[CPathT::GetDriveNumber](#getdrivenumber)|Llame a este método para buscar en la ruta de acceso una letra de unidad en el intervalo de ' A ' a ' Z ' y devolver el número de unidad correspondiente.|
|[CPathT:: GetExtension](#getextension)|Llame a este método para obtener la extensión de archivo de la ruta de acceso.|
|[CPathT::IsDirectory](#isdirectory)|Llame a este método para comprobar si la ruta de acceso es un directorio válido.|
|[CPathT::IsFileSpec](#isfilespec)|Llame a este método para buscar en una ruta de acceso todos los caracteres delimitadores de ruta de acceso (por ejemplo, ': ' o ' \\ '). Si no hay caracteres que delimiten la ruta de acceso, la ruta de acceso se considera una ruta de acceso de especificación de archivo.|
|[CPathT::IsPrefix](#isprefix)|Llame a este método para determinar si una ruta de acceso contiene un prefijo válido del tipo pasado por *pszPrefix*.|
|[CPathT::IsRelative](#isrelative)|Llame a este método para determinar si la ruta de acceso es relativa.|
|[CPathT:: IsRoot](#isroot)|Llame a este método para determinar si la ruta de acceso es una raíz de directorio.|
|[CPathT::IsSameRoot](#issameroot)|Llame a este método para determinar si otra ruta de acceso tiene un componente raíz común con la ruta de acceso actual.|
|[CPathT::IsUNC](#isunc)|Llame a este método para determinar si la ruta de acceso es una ruta de acceso UNC (Convención de nomenclatura universal) válida para un servidor y un recurso compartido.|
|[CPathT::IsUNCServer](#isuncserver)|Llame a este método para determinar si la ruta de acceso es una ruta de acceso UNC (Convención de nomenclatura universal) válida solo para un servidor.|
|[CPathT::IsUNCServerShare](#isuncservershare)|Llame a este método para determinar si la ruta de acceso es una ruta de acceso compartida UNC (Convención de nomenclatura universal) válida, \\ \ *server* \ *share*.|
|[CPathT::MakePretty](#makepretty)|Llame a este método para convertir una ruta de acceso a todos los caracteres en minúsculas para dar una apariencia coherente a la ruta de acceso.|
|[CPathT::MatchSpec](#matchspec)|Llame a este método para buscar en la ruta de acceso una cadena que contenga un tipo de coincidencia de caracteres comodín.|
|[CPathT::QuoteSpaces](#quotespaces)|Llame a este método para escribir la ruta de acceso entre comillas si contiene espacios.|
|[CPathT::RelativePathTo](#relativepathto)|Llame a este método para crear una ruta de acceso relativa de un archivo o una carpeta a otra.|
|[CPathT::RemoveArgs](#removeargs)|Llame a este método para quitar de la ruta de acceso los argumentos de la línea de comandos.|
|[CPathT::RemoveBackslash](#removebackslash)|Llame a este método para quitar la barra diagonal inversa final de la ruta de acceso.|
|[CPathT::RemoveBlanks](#removeblanks)|Llame a este método para quitar todos los espacios iniciales y finales de la ruta de acceso.|
|[CPathT::RemoveExtension](#removeextension)|Llame a este método para quitar la extensión de archivo de la ruta de acceso, si la hay.|
|[CPathT::RemoveFileSpec](#removefilespec)|Llame a este método para quitar el nombre de archivo final y la barra diagonal inversa de la ruta de acceso, si los tiene.|
|[CPathT::RenameExtension](#renameextension)|Llame a este método para reemplazar la extensión de nombre de archivo de la ruta de acceso por una nueva extensión. Si el nombre de archivo no contiene una extensión, la extensión se adjuntará al final de la cadena.|
|[CPathT::SkipRoot](#skiproot)|Llame a este método para analizar una ruta de acceso, omitiendo las partes de la letra de unidad o del servidor UNC o de la ruta de acceso del recurso compartido.|
|[CPathT::StripPath](#strippath)|Llame a este método para quitar la parte de la ruta de acceso de una ruta de acceso completa y un nombre de archivo.|
|[CPathT::StripToRoot](#striptoroot)|Llame a este método para quitar todas las partes de la ruta de acceso excepto la información raíz.|
|[CPathT::UnquoteSpaces](#unquotespaces)|Llame a este método para quitar las comillas del principio y el final de una ruta de acceso.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CPathT:: Operator const StringType &](#operator_const_stringtype_amp)|Este operador permite que el objeto se trate como una cadena.|
|[CPathT:: Operator CPathT::P CXSTR](#operator_cpatht__pcxstr)|Este operador permite que el objeto se trate como una cadena.|
|[CPathT:: Operator StringType &](#operator_stringtype_amp)|Este operador permite que el objeto se trate como una cadena.|
|[CPathT:: Operator + =](#operator_add_eq)|Este operador anexa una cadena a la ruta de acceso.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CPathT::m_strPath](#m_strpath)|La ruta de acceso.|

## <a name="remarks"></a>Comentarios

`CPath`, `CPathA` y `CPathW` son instancias de `CPathT` definidas de la siguiente manera:

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlpath. h

##  <a name="addbackslash"></a>CPathT::AddBackslash

Llame a este método para agregar una barra diagonal inversa al final de una cadena con el fin de crear la sintaxis correcta para una ruta de acceso. Si la ruta de acceso ya tiene una barra diagonal inversa al final, no se agregará ninguna barra diagonal inversa.

```
void AddBackslash();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathAddBackSlash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

##  <a name="addextension"></a>CPathT::AddExtension

Llame a este método para agregar una extensión de archivo a una ruta de acceso.

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parámetros

*pszExtension*<br/>
Extensión de archivo que se va a agregar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

##  <a name="append"></a>CPathT:: Append

Llame a este método para anexar una cadena a la ruta de acceso actual.

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>Parámetros

*pszMore*<br/>
Cadena que se va a anexar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

##  <a name="buildroot"></a>CPathT:: objeto buildroot

Llame a este método para crear una ruta de acceso raíz a partir de un número de unidad determinado.

```
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>Parámetros

*iDrive*<br/>
El número de unidad (0 es:, 1 es B:, etc.).

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

##  <a name="canonicalize"></a>CPathT:: Canonicalization

Llame a este método para convertir la ruta de acceso al formato canónico.

```
void Canonicalize();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

##  <a name="combine"></a>CPathT:: Combine

Llame a este método para concatenar una cadena que represente un nombre de directorio y una cadena que represente un nombre de ruta de acceso de archivo en una ruta de acceso.

```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>Parámetros

*pszDir*<br/>
Ruta de acceso al directorio.

*pszFile*<br/>
Ruta de acceso del archivo.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

##  <a name="commonprefix"></a>CPathT::CommonPrefix

Llame a este método para determinar si la ruta de acceso especificada comparte un prefijo común con la ruta de acceso actual.

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>Parámetros

*pszOther*<br/>
Ruta de acceso que se va a comparar con la actual.

### <a name="return-value"></a>Valor devuelto

Devuelve el prefijo común.

### <a name="remarks"></a>Comentarios

Un prefijo es uno de estos tipos: "C: \\ \\", ".", "..", ".. \\ \\ ". Para obtener más información, vea [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

##  <a name="compactpath"></a>CPathT::CompactPath

Llame a este método para truncar una ruta de acceso de archivo para ajustarse a un ancho de píxel determinado reemplazando los componentes de la ruta de acceso con puntos suspensivos.

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>Parámetros

*Cámaras*<br/>
Contexto de dispositivo usado para las métricas de fuente.

*nWidth*<br/>
Ancho, en píxeles, que se forzará a que quepa la cadena.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

##  <a name="compactpathex"></a>CPathT::CompactPathEx

Llame a este método para truncar una ruta de acceso de archivo para ajustarse a un número determinado de caracteres reemplazando los componentes de la ruta de acceso con puntos suspensivos.

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parámetros

*nMaxChars*<br/>
Número máximo de caracteres que se van a incluir en la nueva cadena, incluido el carácter nulo de terminación.

*dwFlags*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

##  <a name="cpatht"></a>CPathT::CPathT

El constructor.

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>Parámetros

*pszPath*<br/>
Puntero a una cadena de ruta de acceso.

*path*<br/>
Cadena de ruta de acceso.

##  <a name="fileexists"></a>CPathT:: FileExists

Llame a este método para comprobar si existe el archivo en este nombre de ruta de acceso.

```
BOOL FileExists() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el archivo existe, FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

##  <a name="findextension"></a>CPathT::FindExtension

Llame a este método para buscar la posición de la extensión de archivo dentro de la ruta de acceso.

```
int FindExtension() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del "." que precede a la extensión. Si no se encuentra ninguna extensión, devuelve-1.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

##  <a name="findfilename"></a>CPathT::FindFileName

Llame a este método para buscar la posición del nombre de archivo dentro de la ruta de acceso.

```
int FindFileName() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del nombre de archivo. Si no se encuentra ningún nombre de archivo, devuelve-1.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

##  <a name="getdrivenumber"></a>CPathT::GetDriveNumber

Llame a este método para buscar en la ruta de acceso una letra de unidad en el intervalo de ' A ' a ' Z ' y devolver el número de unidad correspondiente.

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de unidad como un entero comprendido entre 0 y 25 (correspondiente a ' A ' a ' Z ') si la ruta de acceso tiene una letra de unidad o-1 en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

##  <a name="getextension"></a>CPathT:: GetExtension

Llame a este método para obtener la extensión de archivo de la ruta de acceso.

```
StringType GetExtension() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve la extensión de archivo.

##  <a name="isdirectory"></a>CPathT::IsDirectory

Llame a este método para comprobar si la ruta de acceso es un directorio válido.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero (16) si la ruta de acceso es un directorio; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

##  <a name="isfilespec"></a>CPathT::IsFileSpec

Llame a este método para buscar en una ruta de acceso todos los caracteres delimitadores de ruta de acceso (por ejemplo, ': ' o ' \\ '). Si no hay caracteres que delimiten la ruta de acceso, la ruta de acceso se considera una ruta de acceso de especificación de archivo.

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si no hay caracteres de delimitación de la ruta de acceso en la ruta de acceso o FALSE si hay caracteres de delimitación de la ruta de acceso.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

##  <a name="isprefix"></a>CPathT::IsPrefix

Llame a este método para determinar si una ruta de acceso contiene un prefijo válido del tipo pasado por *pszPrefix*.

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>Parámetros

*pszPrefix*<br/>
Prefijo que se va a buscar. Un prefijo es uno de estos tipos: "C: \\ \\", ".", "..", ".. \\ \\ ".

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso contiene el prefijo o FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

##  <a name="isrelative"></a>CPathT::IsRelative

Llame a este método para determinar si la ruta de acceso es relativa.

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso es relativa o FALSE si es absoluta.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

##  <a name="isroot"></a>CPathT:: IsRoot

Llame a este método para determinar si la ruta de acceso es una raíz de directorio.

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso es una raíz o FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

##  <a name="issameroot"></a>CPathT::IsSameRoot

Llame a este método para determinar si otra ruta de acceso tiene un componente raíz común con la ruta de acceso actual.

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>Parámetros

*pszOther*<br/>
La otra ruta de acceso.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si ambas cadenas tienen el mismo componente raíz o FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

##  <a name="isunc"></a>CPathT::IsUNC

Llame a este método para determinar si la ruta de acceso es una ruta de acceso UNC (Convención de nomenclatura universal) válida para un servidor y un recurso compartido.

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso es una ruta de acceso UNC válida o FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

##  <a name="isuncserver"></a>CPathT::IsUNCServer

Llame a este método para determinar si la ruta de acceso es una ruta de acceso UNC (Convención de nomenclatura universal) válida solo para un servidor.

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la cadena es una ruta de acceso UNC válida para un servidor únicamente (sin nombre de recurso compartido) o FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

##  <a name="isuncservershare"></a>CPathT::IsUNCServerShare

Llame a este método para determinar si la ruta de acceso es una ruta de acceso compartida UNC (Convención de nomenclatura universal) válida, \\ \ *server* \ *share*.

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso tiene el formato \\ \ *servidor* \ *recurso compartido*, o bien false en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

##  <a name="m_strpath"></a>CPathT::m_strPath

La ruta de acceso.

```
StringType m_strPath;
```

### <a name="remarks"></a>Comentarios

`StringType` es el parámetro de plantilla que se va a `CPathT`.

##  <a name="makepretty"></a>CPathT::MakePretty

Llame a este método para convertir una ruta de acceso a todos los caracteres en minúsculas para dar una apariencia coherente a la ruta de acceso.

```
BOOL MakePretty();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso se ha convertido o FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

##  <a name="matchspec"></a>CPathT::MatchSpec

Llame a este método para buscar en la ruta de acceso una cadena que contenga un tipo de coincidencia de caracteres comodín.

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>Parámetros

*pszSpec*<br/>
Puntero a una cadena terminada en NULL con el tipo de archivo que se va a buscar. Por ejemplo, para comprobar si el archivo de la ruta de acceso actual es un archivo de documento, *pszSpec* debe establecerse en "*. doc".

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la cadena coincide con, o FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

##  <a name="operator_add_eq"></a>CPathT:: Operator + =

Este operador anexa una cadena a la ruta de acceso.

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>Parámetros

*pszMore*<br/>
Cadena que se va a anexar.

### <a name="return-value"></a>Valor devuelto

Devuelve la ruta de acceso actualizada.

##  <a name="operator_const_stringtype_amp"></a>CPathT:: Operator const StringType &amp;

Este operador permite que el objeto se trate como una cadena.

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una cadena que representa la ruta de acceso actual administrada por este objeto.

##  <a name="operator_cpatht__pcxstr"></a>CPathT:: Operator CPathT::P CXSTR

Este operador permite que el objeto se trate como una cadena.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una cadena que representa la ruta de acceso actual administrada por este objeto.

##  <a name="operator_stringtype_amp"></a>CPathT:: Operator StringType &amp;

Este operador permite que el objeto se trate como una cadena.

```
operator StringType&() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una cadena que representa la ruta de acceso actual administrada por este objeto.

##  <a name="pcxstr"></a>CPathT::P CXSTR

Tipo de cadena de constante.

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>Comentarios

`StringType` es el parámetro de plantilla que se va a `CPathT`.

##  <a name="pxstr"></a>CPathT::P XSTR

Tipo de cadena.

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>Comentarios

`StringType` es el parámetro de plantilla que se va a `CPathT`.

##  <a name="quotespaces"></a>CPathT::QuoteSpaces

Llame a este método para escribir la ruta de acceso entre comillas si contiene espacios.

```
void QuoteSpaces();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

##  <a name="relativepathto"></a>CPathT::RelativePathTo

Llame a este método para crear una ruta de acceso relativa de un archivo o una carpeta a otra.

```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```

### <a name="parameters"></a>Parámetros

*pszFrom*<br/>
Inicio de la ruta de acceso relativa.

*dwAttrFrom*<br/>
Atributos de archivo de *pszFrom*. Si este valor contiene FILE_ATTRIBUTE_DIRECTORY, se supone que *pszFrom* es un directorio; de lo contrario, se supone que *pszFrom* es un archivo.

*pszTo*<br/>
Punto final de la ruta de acceso relativa.

*dwAttrTo*<br/>
Atributos de archivo de *pszTo*. Si este valor contiene FILE_ATTRIBUTE_DIRECTORY, se supone que *pszTo* es un directorio; de lo contrario, se supone que *pszTo* es un archivo.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

##  <a name="removeargs"></a>CPathT::RemoveArgs

Llame a este método para quitar de la ruta de acceso los argumentos de la línea de comandos.

```
void RemoveArgs();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

##  <a name="removebackslash"></a>CPathT::RemoveBackslash

Llame a este método para quitar la barra diagonal inversa final de la ruta de acceso.

```
void RemoveBackslash();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

##  <a name="removeblanks"></a>CPathT::RemoveBlanks

Llame a este método para quitar todos los espacios iniciales y finales de la ruta de acceso.

```
void RemoveBlanks();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

##  <a name="removeextension"></a>CPathT::RemoveExtension

Llame a este método para quitar la extensión de archivo de la ruta de acceso, si la hay.

```
void RemoveExtension();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

##  <a name="removefilespec"></a>CPathT::RemoveFileSpec

Llame a este método para quitar el nombre de archivo final y la barra diagonal inversa de la ruta de acceso, si los tiene.

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

##  <a name="renameextension"></a>CPathT::RenameExtension

Llame a este método para reemplazar la extensión de nombre de archivo de la ruta de acceso por una nueva extensión. Si el nombre de archivo no contiene una extensión, la extensión se adjuntará al final de la ruta de acceso.

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parámetros

*pszExtension*<br/>
La nueva extensión de nombre de archivo, precedida de un carácter ".".

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

##  <a name="skiproot"></a>CPathT::SkipRoot

Llame a este método para analizar una ruta de acceso, omitiendo las partes de la letra de unidad o UNC (Convención de nomenclatura universal) o del recurso compartido.

```
int SkipRoot() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del principio del subtrazado que sigue a la raíz (letra de unidad o servidor o recurso compartido UNC).

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

##  <a name="strippath"></a>CPathT::StripPath

Llame a este método para quitar la parte de la ruta de acceso de una ruta de acceso completa y un nombre de archivo.

```
void StripPath();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

##  <a name="striptoroot"></a>CPathT::StripToRoot

Llame a este método para quitar todas las partes de la ruta de acceso excepto la información raíz.

```
BOOL StripToRoot();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ha encontrado una letra de unidad válida en la ruta de acceso o FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

##  <a name="unquotespaces"></a>CPathT::UnquoteSpaces

Llame a este método para quitar las comillas del principio y el final de una ruta de acceso.

```
void UnquoteSpaces();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

##  <a name="xchar"></a>CPathT::XCHAR

Tipo de carácter.

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>Comentarios

`StringType` es el parámetro de plantilla que se va a `CPathT`.

## <a name="see-also"></a>Vea también

[Clases](../../atl/reference/atl-classes.md)<br/>
[CStringT (clase)](../../atl-mfc-shared/reference/cstringt-class.md)
