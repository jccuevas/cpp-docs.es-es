---
title: CPathT (clase)
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
ms.openlocfilehash: 109f9baefd0e6775db05eeba8cb78542bf60a9ac
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565797"
---
# <a name="cpatht-class"></a>CPathT (clase)

Esta clase representa una ruta de acceso.

> [!IMPORTANT]
> Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>Parámetros

*StringType*<br/>
La clase de cadena ATL/MFC que se usará para la ruta de acceso (vea [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)).

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|[CPathT::PCXSTR](#pcxstr)|Un tipo de cadena constante.|
|[CPathT::PXSTR](#pxstr)|Un tipo de cadena.|
|[CPathT::XCHAR](#xchar)|Tipo de carácter.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CPathT::CPathT](#cpatht)|El constructor para la ruta de acceso.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CPathT::AddBackslash](#addbackslash)|Llame a este método para agregar una barra diagonal inversa al final de una cadena para crear la sintaxis correcta para una ruta de acceso.|
|[CPathT::AddExtension](#addextension)|Llame a este método para agregar una extensión de archivo a una ruta de acceso.|
|[CPathT::Append](#append)|Llame a este método para anexar una cadena a la ruta de acceso actual.|
|[CPathT::BuildRoot](#buildroot)|Llame a este método para crear una ruta de acceso raíz de un número determinado de unidad.|
|[CPathT::Canonicalize](#canonicalize)|Llame a este método para convertir la ruta de acceso en forma canónica.|
|[CPathT::Combine](#combine)|Llame a este método para concatenar una cadena que representa un nombre de directorio y una cadena que representa un nombre de ruta de acceso de archivo en una ruta de acceso.|
|[CPathT::CommonPrefix](#commonprefix)|Llame a este método para determinar si la ruta de acceso especificado comparte un prefijo común con la ruta de acceso actual.|
|[CPathT::CompactPath](#compactpath)|Llame a este método para truncar una ruta de acceso de archivo para que quepa dentro de un ancho de píxel determinado mediante la sustitución de componentes de ruta de acceso con el botón de puntos suspensivos.|
|[CPathT::CompactPathEx](#compactpathex)|Llame a este método para truncar una ruta de acceso de archivo para que quepa dentro de un número determinado de caracteres mediante la sustitución de componentes de ruta de acceso con el botón de puntos suspensivos.|
|[CPathT::FileExists](#fileexists)|Llame a este método para comprobar si existe el archivo en este nombre de ruta de acceso.|
|[CPathT::FindExtension](#findextension)|Llame a este método para buscar la posición de la extensión de archivo dentro de la ruta de acceso.|
|[CPathT::FindFileName](#findfilename)|Llame a este método para buscar la posición del nombre de archivo dentro de la ruta de acceso.|
|[CPathT::GetDriveNumber](#getdrivenumber)|Llame a este método para buscar la ruta de acceso para una letra de unidad en el intervalo de 'A' a 'Z' y devolver el número de unidad correspondiente.|
|[CPathT::GetExtension](#getextension)|Llame a este método para obtener la extensión de archivo de la ruta de acceso.|
|[CPathT::IsDirectory](#isdirectory)|Llame a este método para comprobar si la ruta de acceso es un directorio válido.|
|[CPathT::IsFileSpec](#isfilespec)|Llame a este método para buscar una ruta de acceso para los caracteres de delimitación de ruta de acceso (por ejemplo, ':' o '\\'). Si no hay ningún carácter delimitación de ruta de acceso está presente, se considera que la ruta de acceso es una ruta de acceso de la especificación de archivo.|
|[CPathT::IsPrefix](#isprefix)|Llame a este método para determinar si una ruta de acceso contiene un prefijo válido del tipo pasado por *pszPrefix*.|
|[CPathT::IsRelative](#isrelative)|Llame a este método para determinar si la ruta de acceso es relativa.|
|[CPathT::IsRoot](#isroot)|Llame a este método para determinar si la ruta de acceso es una directorio raíz.|
|[CPathT::IsSameRoot](#issameroot)|Llame a este método para determinar si otra ruta de acceso tiene un componente raíz común con la ruta de acceso actual.|
|[CPathT::IsUNC](#isunc)|Llame a este método para determinar si la ruta de acceso es una ruta de acceso UNC (convención de nomenclatura universal) válida para un servidor y compartir.|
|[CPathT::IsUNCServer](#isuncserver)|Llame a este método para determinar si la ruta de acceso es una ruta de acceso UNC (convención de nomenclatura universal) válida para un solo servidor.|
|[CPathT::IsUNCServerShare](#isuncservershare)|Llame a este método para determinar si la ruta de acceso es una ruta válida de recurso compartido UNC (convención de nomenclatura universal), \\ \  *server*\ *compartir*.|
|[CPathT::MakePretty](#makepretty)|Llame a este método para convertir una ruta de acceso a todos los caracteres en minúsculas para dar una apariencia coherente de la ruta de acceso.|
|[CPathT::MatchSpec](#matchspec)|Llame a este método para buscar la ruta de acceso para una cadena que contiene un tipo de coincidencia de caracteres comodín.|
|[CPathT::QuoteSpaces](#quotespaces)|Llame a este método para que escriba la ruta de acceso entre comillas si contiene espacios en blanco.|
|[CPathT::RelativePathTo](#relativepathto)|Llame a este método para crear una ruta de acceso relativa de un archivo o carpeta a otra.|
|[CPathT::RemoveArgs](#removeargs)|Llame a este método para quitar los argumentos de línea de comandos de la ruta de acceso.|
|[CPathT::RemoveBackslash](#removebackslash)|Llame a este método para quitar la barra diagonal inversa final de la ruta de acceso.|
|[CPathT::RemoveBlanks](#removeblanks)|Llame a este método para quitar todos los espacios iniciales y finales de la ruta de acceso.|
|[CPathT::RemoveExtension](#removeextension)|Llame a este método para quitar la extensión de archivo de la ruta de acceso, si hay alguno.|
|[CPathT::RemoveFileSpec](#removefilespec)|Llame a este método para quitar el nombre de archivo al final y la barra diagonal inversa de la ruta de acceso, si lo tiene.|
|[CPathT::RenameExtension](#renameextension)|Llame a este método para reemplazar la extensión de nombre de archivo en la ruta de acceso con una nueva extensión. Si el nombre de archivo no contiene una extensión, la extensión se adjuntará al final de la cadena.|
|[CPathT::SkipRoot](#skiproot)|Llame a este método para analizar una ruta de acceso, se omitirá la letra de unidad o partes de ruta de acceso de servidor o recurso compartido UNC.|
|[CPathT::StripPath](#strippath)|Llame a este método para quitar la parte de la ruta de acceso de una ruta de acceso completa y nombre de archivo.|
|[CPathT::StripToRoot](#striptoroot)|Llame a este método para quitar todas las partes de la ruta de acceso, salvo la información de raíz.|
|[CPathT::UnquoteSpaces](#unquotespaces)|Llame a este método para quitar las comillas de principio y al final de una ruta de acceso.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CPathT::operator const StringType &](#operator_const_stringtype_amp)|Este operador permite que el objeto se traten como una cadena.|
|[CPathT::operator CPathT::PCXSTR](#operator_cpatht__pcxstr)|Este operador permite que el objeto se traten como una cadena.|
|[CPathT::operator StringType &](#operator_stringtype_amp)|Este operador permite que el objeto se traten como una cadena.|
|[CPathT::operator +=](#operator_add_eq)|Este operador anexa una cadena a la ruta de acceso.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CPathT::m_strPath](#m_strpath)|La ruta de acceso.|

## <a name="remarks"></a>Comentarios

`CPath`, `CPathA`, y `CPathW` son creaciones de instancias de `CPathT` define como sigue:

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlpath.h

##  <a name="addbackslash"></a>  CPathT::AddBackslash

Llame a este método para agregar una barra diagonal inversa al final de una cadena para crear la sintaxis correcta para una ruta de acceso. Si la ruta de acceso ya tiene una barra diagonal inversa, no se agregará ninguna barra diagonal inversa.

```
void AddBackslash();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathAddBackSlash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha).

##  <a name="addextension"></a>  CPathT::AddExtension

Llame a este método para agregar una extensión de archivo a una ruta de acceso.

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parámetros

*pszExtension*<br/>
Para agregar la extensión de archivo.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona).

##  <a name="append"></a>  CPathT::Append

Llame a este método para anexar una cadena a la ruta de acceso actual.

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>Parámetros

*pszMore*<br/>
Cadena que se va a anexar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda).

##  <a name="buildroot"></a>  CPathT::BuildRoot

Llame a este método para crear una ruta de acceso raíz de un número determinado de unidad.

```
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>Parámetros

*iDrive*<br/>
El número de unidad (0 es r:, 1 es B: y así sucesivamente).

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota).

##  <a name="canonicalize"></a>  CPathT::Canonicalize

Llame a este método para convertir la ruta de acceso en forma canónica.

```
void Canonicalize();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea).

##  <a name="combine"></a>  CPathT::Combine

Llame a este método para concatenar una cadena que representa un nombre de directorio y una cadena que representa un nombre de ruta de acceso de archivo en una ruta de acceso.

```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>Parámetros

*pszDir*<br/>
La ruta de acceso del directorio.

*pszFile*<br/>
La ruta de acceso de archivo.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea).

##  <a name="commonprefix"></a>  CPathT::CommonPrefix

Llame a este método para determinar si la ruta de acceso especificado comparte un prefijo común con la ruta de acceso actual.

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>Parámetros

*pszOther*<br/>
La ruta de acceso que se compara con la actual.

### <a name="return-value"></a>Valor devuelto

Devuelve el prefijo común.

### <a name="remarks"></a>Comentarios

Un prefijo es uno de estos tipos: "C:\\\\", ".", "..", "..\\\\". Para obtener más información, consulte [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa).

##  <a name="compactpath"></a>  CPathT::CompactPath

Llame a este método para truncar una ruta de acceso de archivo para que quepa dentro de un ancho de píxel determinado mediante la sustitución de componentes de ruta de acceso con el botón de puntos suspensivos.

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>Parámetros

*hDC*<br/>
El contexto de dispositivo utilizado para las métricas de fuente.

*nWidth*<br/>
El ancho, en píxeles, que se forzará la cadena para que quepa en.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha).

##  <a name="compactpathex"></a>  CPathT::CompactPathEx

Llame a este método para truncar una ruta de acceso de archivo para que quepa dentro de un número determinado de caracteres mediante la sustitución de componentes de ruta de acceso con el botón de puntos suspensivos.

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parámetros

*nMaxChars*<br/>
El número máximo de caracteres que se van a incluirse en la nueva cadena, incluido el carácter nulo final.

*dwFlags*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa).

##  <a name="cpatht"></a>  CPathT::CPathT

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
La cadena de ruta de acceso.

##  <a name="fileexists"></a>  CPathT::FileExists

Llame a este método para comprobar si existe el archivo en este nombre de ruta de acceso.

```
BOOL FileExists() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el archivo existe, FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa).

##  <a name="findextension"></a>  CPathT::FindExtension

Llame a este método para buscar la posición de la extensión de archivo dentro de la ruta de acceso.

```
int FindExtension() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve la posición de la "." delante de la extensión. Si no se encuentra ninguna extensión, devuelve -1.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona).

##  <a name="findfilename"></a>  CPathT::FindFileName

Llame a este método para buscar la posición del nombre de archivo dentro de la ruta de acceso.

```
int FindFileName() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del nombre de archivo. Si no se encuentra ningún nombre de archivo, devuelve -1.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea).

##  <a name="getdrivenumber"></a>  CPathT::GetDriveNumber

Llame a este método para buscar la ruta de acceso para una letra de unidad en el intervalo de 'A' a 'Z' y devolver el número de unidad correspondiente.

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de unidad como un número entero comprendido entre 0 y 25 (correspondiente a 'A' a 'Z') si la ruta de acceso tiene una letra de unidad, o -1 si no.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera).

##  <a name="getextension"></a>  CPathT::GetExtension

Llame a este método para obtener la extensión de archivo de la ruta de acceso.

```
StringType GetExtension() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve la extensión de archivo.

##  <a name="isdirectory"></a>  CPathT::IsDirectory

Llame a este método para comprobar si la ruta de acceso es un directorio válido.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero (16) si la ruta de acceso es un directorio.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya).

##  <a name="isfilespec"></a>  CPathT::IsFileSpec

Llame a este método para buscar una ruta de acceso para los caracteres de delimitación de ruta de acceso (por ejemplo, ':' o '\\'). Si no hay ningún carácter delimitación de ruta de acceso está presente, se considera que la ruta de acceso es una ruta de acceso de la especificación de archivo.

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si no hay ningún carácter de delimitación de ruta de acceso dentro de la ruta de acceso, o FALSE si no hay caracteres delimitación de ruta de acceso.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca).

##  <a name="isprefix"></a>  CPathT::IsPrefix

Llame a este método para determinar si una ruta de acceso contiene un prefijo válido del tipo pasado por *pszPrefix*.

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>Parámetros

*pszPrefix*<br/>
El prefijo que se va a buscar. Un prefijo es uno de estos tipos: "C:\\\\", ".", "..", "..\\\\".

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso contiene el prefijo o falso en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa).

##  <a name="isrelative"></a>  CPathT::IsRelative

Llame a este método para determinar si la ruta de acceso es relativa.

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso es relativa, o FALSE si es absoluto.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea).

##  <a name="isroot"></a>  CPathT::IsRoot

Llame a este método para determinar si la ruta de acceso es una directorio raíz.

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso es una raíz, o FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota).

##  <a name="issameroot"></a>  CPathT::IsSameRoot

Llame a este método para determinar si otra ruta de acceso tiene un componente raíz común con la ruta de acceso actual.

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>Parámetros

*pszOther*<br/>
La otra ruta de acceso.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si ambas tienen el mismo componente raíz, o falso en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota).

##  <a name="isunc"></a>  CPathT::IsUNC

Llame a este método para determinar si la ruta de acceso es una ruta de acceso UNC (convención de nomenclatura universal) válida para un servidor y compartir.

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso es una ruta de acceso UNC válida o FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca).

##  <a name="isuncserver"></a>  CPathT::IsUNCServer

Llame a este método para determinar si la ruta de acceso es una ruta de acceso UNC (convención de nomenclatura universal) válida para un solo servidor.

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la cadena es una ruta de acceso UNC para un solo servidor (sin nombre de recurso compartido) válido o FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera).

##  <a name="isuncservershare"></a>  CPathT::IsUNCServerShare

Llame a este método para determinar si la ruta de acceso es una ruta válida de recurso compartido UNC (convención de nomenclatura universal), \\ \  *server*\ *compartir*.

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la ruta de acceso se encuentra en el formulario \\ \  *server*\ *compartir*, o falso en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea).

##  <a name="m_strpath"></a>  CPathT::m_strPath

La ruta de acceso.

```
StringType m_strPath;
```

### <a name="remarks"></a>Comentarios

`StringType` es el parámetro de plantilla `CPathT`.

##  <a name="makepretty"></a>  CPathT::MakePretty

Llame a este método para convertir una ruta de acceso a todos los caracteres en minúsculas para dar una apariencia coherente de la ruta de acceso.

```
BOOL MakePretty();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ha convertido la ruta de acceso, o FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya).

##  <a name="matchspec"></a>  CPathT::MatchSpec

Llame a este método para buscar la ruta de acceso para una cadena que contiene un tipo de coincidencia de caracteres comodín.

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>Parámetros

*pszSpec*<br/>
Puntero a una cadena terminada en null con el tipo de archivo que se va a buscar. Por ejemplo, para comprobar si el archivo en la ruta de acceso actual es un archivo de documento, *pszSpec* debe establecerse en "* .doc".

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la cadena coincide con, o FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca).

##  <a name="operator_add_eq"></a>  CPathT::operator +=

Este operador anexa una cadena a la ruta de acceso.

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>Parámetros

*pszMore*<br/>
Cadena que se va a anexar.

### <a name="return-value"></a>Valor devuelto

Devuelve la ruta de acceso actualizada.

##  <a name="operator_const_stringtype_amp"></a>  StringType const CPathT::operator &amp;

Este operador permite que el objeto se traten como una cadena.

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una cadena que representa la ruta de acceso actual administrado por este objeto.

##  <a name="operator_cpatht__pcxstr"></a>  CPathT::operator CPathT::PCXSTR

Este operador permite que el objeto se traten como una cadena.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una cadena que representa la ruta de acceso actual administrado por este objeto.

##  <a name="operator_stringtype_amp"></a>  CPathT::operator StringType &amp;

Este operador permite que el objeto se traten como una cadena.

```
operator StringType&() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una cadena que representa la ruta de acceso actual administrado por este objeto.

##  <a name="pcxstr"></a>  CPathT::PCXSTR

Un tipo de cadena constante.

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>Comentarios

`StringType` es el parámetro de plantilla `CPathT`.

##  <a name="pxstr"></a>  CPathT::PXSTR

Un tipo de cadena.

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>Comentarios

`StringType` es el parámetro de plantilla `CPathT`.

##  <a name="quotespaces"></a>  CPathT::QuoteSpaces

Llame a este método para que escriba la ruta de acceso entre comillas si contiene espacios en blanco.

```
void QuoteSpaces();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa).

##  <a name="relativepathto"></a>  CPathT::RelativePathTo

Llame a este método para crear una ruta de acceso relativa de un archivo o carpeta a otra.

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
Los atributos de archivo *pszFrom*. Si este valor contiene FILE_ATTRIBUTE_DIRECTORY, *pszFrom* se considera que ser un directorio; de lo contrario, *pszFrom* se supone que es un archivo.

*pszTo*<br/>
El punto final de la ruta de acceso relativa.

*dwAttrTo*<br/>
Los atributos de archivo *pszTo*. Si este valor contiene FILE_ATTRIBUTE_DIRECTORY, *pszTo* se considera que ser un directorio; de lo contrario, *pszTo* se supone que es un archivo.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa).

##  <a name="removeargs"></a>  CPathT::RemoveArgs

Llame a este método para quitar los argumentos de línea de comandos de la ruta de acceso.

```
void RemoveArgs();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa).

##  <a name="removebackslash"></a>  CPathT::RemoveBackslash

Llame a este método para quitar la barra diagonal inversa final de la ruta de acceso.

```
void RemoveBackslash();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha).

##  <a name="removeblanks"></a>  CPathT::RemoveBlanks

Llame a este método para quitar todos los espacios iniciales y finales de la ruta de acceso.

```
void RemoveBlanks();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa).

##  <a name="removeextension"></a>  CPathT::RemoveExtension

Llame a este método para quitar la extensión de archivo de la ruta de acceso, si hay alguno.

```
void RemoveExtension();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona).

##  <a name="removefilespec"></a>  CPathT::RemoveFileSpec

Llame a este método para quitar el nombre de archivo al final y la barra diagonal inversa de la ruta de acceso, si lo tiene.

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca).

##  <a name="renameextension"></a>  CPathT::RenameExtension

Llame a este método para reemplazar la extensión de nombre de archivo en la ruta de acceso con una nueva extensión. Si el nombre de archivo no contiene una extensión, la extensión se adjuntará al final de la ruta de acceso.

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parámetros

*pszExtension*<br/>
La nueva extensión de nombre de archivo, precedida por un "." caracteres.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona).

##  <a name="skiproot"></a>  CPathT::SkipRoot

Llame a este método para analizar una ruta de acceso, se omitirá la letra de unidad o partes de ruta de acceso de servidor o recurso compartido UNC (convención de nomenclatura universal).

```
int SkipRoot() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del principio de la subruta de acceso que sigue a la raíz (letra de unidad o servidor o recurso compartido UNC).

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota).

##  <a name="strippath"></a>  CPathT::StripPath

Llame a este método para quitar la parte de la ruta de acceso de una ruta de acceso completa y nombre de archivo.

```
void StripPath();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha).

##  <a name="striptoroot"></a>  CPathT::StripToRoot

Llame a este método para quitar todas las partes de la ruta de acceso, salvo la información de raíz.

```
BOOL StripToRoot();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si una letra de unidad válido se encontró en la ruta de acceso, o FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota).

##  <a name="unquotespaces"></a>  CPathT::UnquoteSpaces

Llame a este método para quitar las comillas de principio y al final de una ruta de acceso.

```
void UnquoteSpaces();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa).

##  <a name="xchar"></a>  CPathT::XCHAR

Tipo de carácter.

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>Comentarios

`StringType` es el parámetro de plantilla `CPathT`.

## <a name="see-also"></a>Vea también

[Clases](../../atl/reference/atl-classes.md)<br/>
[CStringT (clase)](../../atl-mfc-shared/reference/cstringt-class.md)
