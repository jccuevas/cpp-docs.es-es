---
title: Clase CFileFind
ms.date: 11/04/2016
f1_keywords:
- CFileFind
- AFX/CFileFind
- AFX/CFileFind::CFileFind
- AFX/CFileFind::Close
- AFX/CFileFind::FindFile
- AFX/CFileFind::FindNextFile
- AFX/CFileFind::GetCreationTime
- AFX/CFileFind::GetFileName
- AFX/CFileFind::GetFilePath
- AFX/CFileFind::GetFileTitle
- AFX/CFileFind::GetFileURL
- AFX/CFileFind::GetLastAccessTime
- AFX/CFileFind::GetLastWriteTime
- AFX/CFileFind::GetLength
- AFX/CFileFind::GetRoot
- AFX/CFileFind::IsArchived
- AFX/CFileFind::IsCompressed
- AFX/CFileFind::IsDirectory
- AFX/CFileFind::IsDots
- AFX/CFileFind::IsHidden
- AFX/CFileFind::IsNormal
- AFX/CFileFind::IsReadOnly
- AFX/CFileFind::IsSystem
- AFX/CFileFind::IsTemporary
- AFX/CFileFind::MatchesMask
- AFX/CFileFind::CloseContext
- AFX/CFileFind::m_pTM
helpviewer_keywords:
- CFileFind [MFC], CFileFind
- CFileFind [MFC], Close
- CFileFind [MFC], FindFile
- CFileFind [MFC], FindNextFile
- CFileFind [MFC], GetCreationTime
- CFileFind [MFC], GetFileName
- CFileFind [MFC], GetFilePath
- CFileFind [MFC], GetFileTitle
- CFileFind [MFC], GetFileURL
- CFileFind [MFC], GetLastAccessTime
- CFileFind [MFC], GetLastWriteTime
- CFileFind [MFC], GetLength
- CFileFind [MFC], GetRoot
- CFileFind [MFC], IsArchived
- CFileFind [MFC], IsCompressed
- CFileFind [MFC], IsDirectory
- CFileFind [MFC], IsDots
- CFileFind [MFC], IsHidden
- CFileFind [MFC], IsNormal
- CFileFind [MFC], IsReadOnly
- CFileFind [MFC], IsSystem
- CFileFind [MFC], IsTemporary
- CFileFind [MFC], MatchesMask
- CFileFind [MFC], CloseContext
- CFileFind [MFC], m_pTM
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
ms.openlocfilehash: f2dfd3421d2154b4894b62b71d7993c483a77c53
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916122"
---
# <a name="cfilefind-class"></a>Clase CFileFind

Realiza búsquedas de archivos locales y es la clase base para [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) y [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md), que realizan búsquedas de archivos de Internet.

## <a name="syntax"></a>Sintaxis

```
class CFileFind : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFileFind::CFileFind](#cfilefind)|Construye un objeto `CFileFind`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFileFind::Close](#close)|Cierra la solicitud de búsqueda.|
|[CFileFind::FindFile](#findfile)|Busca un nombre de archivo especificado en un directorio.|
|[CFileFind::FindNextFile](#findnextfile)|Continúa una búsqueda de archivos de una llamada anterior a [findfile](#findfile).|
|[CFileFind::GetCreationTime](#getcreationtime)|Obtiene la hora a la que se creó el archivo.|
|[CFileFind::GetFileName](#getfilename)|Obtiene el nombre, incluida la extensión, del archivo encontrado.|
|[CFileFind::GetFilePath](#getfilepath)|Obtiene la ruta de acceso completa del archivo encontrado.|
|[CFileFind::GetFileTitle](#getfiletitle)|Obtiene el título del archivo encontrado. El título no incluye la extensión.|
|[CFileFind::GetFileURL](#getfileurl)|Obtiene la dirección URL, incluida la ruta de acceso del archivo, del archivo encontrado.|
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|Obtiene la hora a la que se produjo el último acceso al archivo.|
|[CFileFind::GetLastWriteTime](#getlastwritetime)|Obtiene la hora a la que se modificó y guardó el archivo por última vez.|
|[CFileFind::GetLength](#getlength)|Obtiene la longitud del archivo encontrado, en bytes.|
|[CFileFind::GetRoot](#getroot)|Obtiene el directorio raíz del archivo encontrado.|
|[CFileFind::IsArchived](#isarchived)|Determina si el archivo encontrado se ha archivado.|
|[CFileFind::IsCompressed](#iscompressed)|Determina si el archivo encontrado está comprimido.|
|[CFileFind::IsDirectory](#isdirectory)|Determina si el archivo encontrado es un directorio.|
|[CFileFind::IsDots](#isdots)|Determina si el nombre del archivo encontrado tiene el nombre "." o "..", lo que indica que es realmente un directorio.|
|[CFileFind::IsHidden](#ishidden)|Determina si el archivo encontrado está oculto.|
|[CFileFind::IsNormal](#isnormal)|Determina si el archivo encontrado es normal (es decir, no tiene ningún otro atributo).|
|[CFileFind::IsReadOnly](#isreadonly)|Determina si el archivo encontrado es de solo lectura.|
|[CFileFind::IsSystem](#issystem)|Determina si el archivo encontrado es un archivo del sistema.|
|[CFileFind::IsTemporary](#istemporary)|Determina si el archivo encontrado es temporal.|
|[CFileFind::MatchesMask](#matchesmask)|Indica los atributos de archivo deseados del archivo que se va a buscar.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFileFind::CloseContext](#closecontext)|Cierra el archivo especificado por el identificador de búsqueda actual.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFileFind::m_pTM](#m_ptm)|Puntero a un `CAtlTransactionManager` objeto.|

## <a name="remarks"></a>Comentarios

`CFileFind`incluye funciones miembro que inician una búsqueda, localizan un archivo y devuelven el título, el nombre o la ruta de acceso del archivo. En las búsquedas de Internet, la función miembro [GetFileURL](#getfileurl) devuelve la dirección URL del archivo.

`CFileFind`es la clase base para otras dos clases MFC diseñadas para buscar tipos de servidor concretos `CGopherFileFind` : funciona específicamente con servidores Gopher y `CFtpFileFind` funciona de forma específica con servidores FTP. Juntas, estas tres clases proporcionan un mecanismo sin problemas para que el cliente busque archivos, independientemente del protocolo del servidor, el tipo de archivo o la ubicación en un equipo local o en un servidor remoto.

En el código siguiente se enumeran todos los archivos del directorio actual, imprimiendo el nombre de cada archivo:

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

Para simplificar el ejemplo, este código usa la C++ clase de `cout` biblioteca estándar. La `cout` línea se puede reemplazar por una llamada a `CListBox::AddString`, por ejemplo, en un programa con una interfaz gráfica de usuario.

Para obtener más información sobre cómo usar `CFileFind` y las demás clases WinInet, vea el artículo [programación en Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="cfilefind"></a>  CFileFind::CFileFind

Se llama a esta función miembro cuando `CFileFind` se construye un objeto.

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parámetros

*pTM*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetFileName](#getfilename).

##  <a name="close"></a>  CFileFind::Close

Llame a esta función miembro para finalizar la búsqueda, restablecer el contexto y liberar todos los recursos.

```
void Close();
```

### <a name="remarks"></a>Comentarios

Después de `Close`llamar a, no es necesario crear una nueva `CFileFind` instancia de antes de llamar a [findfile](#findfile) para iniciar una nueva búsqueda.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetFileName](#getfilename).

##  <a name="closecontext"></a>  CFileFind::CloseContext

Cierra el archivo especificado por el identificador de búsqueda actual.

```
virtual void CloseContext();
```

### <a name="remarks"></a>Comentarios

Cierra el archivo especificado por el valor actual del identificador de búsqueda. Invalide esta función para cambiar el comportamiento predeterminado.

Debe llamar a las funciones [findfile](#findfile) o [FindNextFile](#findnextfile) al menos una vez para recuperar un identificador de búsqueda válido. Las `FindFile` funciones `FindNextFile` y usan el identificador de búsqueda para buscar archivos con nombres que coincidan con un nombre determinado.

##  <a name="findfile"></a>  CFileFind::FindFile

Llame a esta función miembro para abrir una búsqueda de archivos.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>Parámetros

*pstrName*<br/>
Puntero a una cadena que contiene el nombre del archivo que se va a buscar. Si pasa null para *pstrName*, `FindFile` realiza una búsqueda de caracteres comodín (\**.).

*dwUnused*<br/>
Reservado para crear `FindFile` polimórficos con clases derivadas. Debe ser 0.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Para obtener información de error extendida, llame a la función [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror)de Win32.

### <a name="remarks"></a>Comentarios

Después de `FindFile` llamar a para iniciar la búsqueda de archivos, llame a [FindNextFile](#findnextfile) para recuperar los archivos siguientes. Debe llamar `FindNextFile` a al menos una vez antes de llamar a cualquiera de las siguientes funciones miembro de atributo:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [IsNormal](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: IsDirectory](#isdirectory).

##  <a name="findnextfile"></a>  CFileFind::FindNextFile

Llame a esta función miembro para continuar la búsqueda de un archivo desde una llamada anterior a [findfile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si hay más archivos; cero si el archivo encontrado es el último del directorio o si se produjo un error. Para obtener información de error extendida, llame a la función [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror)de Win32. Si el archivo encontrado es el último archivo en el directorio o si no se encuentran archivos coincidentes, la `GetLastError` función devuelve ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Comentarios

Debe llamar `FindNextFile` a al menos una vez antes de llamar a cualquiera de las siguientes funciones miembro de atributo:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [IsNormal](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

`FindNextFile`ajusta la función [FindNextFile](/windows/desktop/api/fileapi/nf-fileapi-findnextfilea)de Win32.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: IsDirectory](#isdirectory).

##  <a name="getcreationtime"></a>  CFileFind::GetCreationTime

Llame a esta función miembro para obtener la hora en que se creó el archivo especificado.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parámetros

*pTimeStamp*<br/>
Puntero a una estructura [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) que contiene la hora a la que se creó el archivo.

*refTime*<br/>
Referencia a un objeto [ctime](../../atl-mfc-shared/reference/ctime-class.md) .

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 si no se realiza correctamente. `GetCreationTime`devuelve 0 solo si no se ha llamado a [FindNextFile](#findnextfile) nunca `CFileFind` en este objeto.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `GetCreationTime`de llamar a.

> [!NOTE]
>  No todos los sistemas de archivos usan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos subyacente o el servidor no admiten el atributo Time. Vea la estructura [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) para obtener información sobre los formatos de hora. En algunos sistemas de operaciones, la hora devuelta está en la zona horaria local del equipo donde se encuentra el archivo. Vea la API [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) de Win32 para obtener más información.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetLength](#getlength).

##  <a name="getfilename"></a>  CFileFind::GetFileName

Llame a esta función miembro para obtener el nombre del archivo encontrado.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre del archivo encontrado más recientemente.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes de llamar a GetFileName.

`GetFileName`es una de las `CFileFind` tres funciones miembro que devuelven alguna forma de nombre de archivo. En la lista siguiente se describen los tres y el modo en que varían:

- `GetFileName`Devuelve el nombre de archivo, incluida la extensión. Por ejemplo, al `GetFileName` llamar a para generar un mensaje de usuario sobre el archivo *c:\myhtml\myfile.txt* se devuelve el nombre de archivo *. txt*.

- [GetFilePath](#getfilepath) devuelve la ruta de acceso completa del archivo. Por ejemplo, al `GetFilePath` llamar a para generar un mensaje de usuario sobre el archivo *c:\myhtml\myfile.txt* se devuelve la ruta de acceso del archivo *c:\myhtml\myfile.txt*.

- [GetFileTitle](#getfiletitle) devuelve el nombre de archivo, sin incluir la extensión de archivo. Por ejemplo, al `GetFileTitle` llamar a para generar un mensaje de usuario sobre el archivo *c:\myhtml\myfile.txt* sedevuelve el título del archivo archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

##  <a name="getfilepath"></a>  CFileFind::GetFilePath

Llame a esta función miembro para obtener la ruta de acceso completa del archivo especificado.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Valor devuelto

Ruta de acceso del archivo especificado.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `GetFilePath`de llamar a.

`GetFilePath`es una de las `CFileFind` tres funciones miembro que devuelven alguna forma de nombre de archivo. En la lista siguiente se describen los tres y el modo en que varían:

- [GetFileName](#getfilename) devuelve el nombre de archivo, incluida la extensión. Por ejemplo, al `GetFileName` llamar a para generar un mensaje de usuario sobre el archivo *c:\myhtml\myfile.txt* se devuelve el nombre de archivo *. txt*.

- `GetFilePath`Devuelve la ruta de acceso completa del archivo. Por ejemplo, si `GetFilePath` se llama a para generar un mensaje de `c:\myhtml\myfile.txt` usuario sobre el archivo `c:\myhtml\myfile.txt`, se devuelve la ruta de acceso del archivo.

- [GetFileTitle](#getfiletitle) devuelve el nombre de archivo, sin incluir la extensión de archivo. Por ejemplo, al `GetFileTitle` llamar a para generar un mensaje de usuario sobre el archivo *c:\myhtml\myfile.txt* sedevuelve el título del archivo archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetFileName](#getfilename).

##  <a name="getfiletitle"></a>  CFileFind::GetFileTitle

Llame a esta función miembro para obtener el título del archivo encontrado.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Valor devuelto

Título del archivo.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `GetFileTitle`de llamar a.

`GetFileTitle`es una de las `CFileFind` tres funciones miembro que devuelven alguna forma de nombre de archivo. En la lista siguiente se describen los tres y el modo en que varían:

- [GetFileName](#getfilename) devuelve el nombre de archivo, incluida la extensión. Por ejemplo, al `GetFileName` llamar a para generar un mensaje de usuario sobre el archivo *c:\myhtml\myfile.txt* se devuelve el nombre de archivo *. txt*.

- [GetFilePath](#getfilepath) devuelve la ruta de acceso completa del archivo. Por ejemplo, al `GetFilePath` llamar a para generar un mensaje de usuario sobre el archivo *c:\myhtml\myfile.txt* se devuelve la ruta de acceso del archivo *c:\myhtml\myfile.txt*.

- `GetFileTitle`Devuelve el nombre de archivo, sin incluir la extensión de archivo. Por ejemplo, al `GetFileTitle` llamar a para generar un mensaje de usuario sobre el archivo *c:\myhtml\myfile.txt* sedevuelve el título del archivo archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetFileName](#getfilename).

##  <a name="getfileurl"></a>  CFileFind::GetFileURL

Llame a esta función miembro para recuperar la dirección URL especificada.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Valor devuelto

Dirección URL completa.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `GetFileURL`de llamar a.

`GetFileURL`es similar a la función miembro [GetFilePath](#getfilepath), salvo que devuelve la dirección URL con el formato `file://path`. Por ejemplo, llamar `GetFileURL` a para obtener la dirección URL completa de *archivo. txt* devuelve la `file://c:\myhtml\myfile.txt`dirección URL.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetFileName](#getfilename).

##  <a name="getlastaccesstime"></a>  CFileFind::GetLastAccessTime

Llame a esta función miembro para obtener la hora a la que se produjo el último acceso al archivo especificado.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Parámetros

*refTime*<br/>
Referencia a un objeto [ctime](../../atl-mfc-shared/reference/ctime-class.md) .

*pTimeStamp*<br/>
Puntero a una estructura [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) que contiene la hora a la que se produjo el último acceso al archivo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 si no se realiza correctamente. `GetLastAccessTime`devuelve 0 solo si no se ha llamado a [FindNextFile](#findnextfile) nunca `CFileFind` en este objeto.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `GetLastAccessTime`de llamar a.

> [!NOTE]
>  No todos los sistemas de archivos usan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos subyacente o el servidor no admiten el atributo Time. Vea la estructura [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) para obtener información sobre los formatos de hora. En algunos sistemas de operaciones, la hora devuelta está en la zona horaria local del equipo donde se encuentra el archivo. Vea la API [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) de Win32 para obtener más información.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetLength](#getlength).

##  <a name="getlastwritetime"></a>  CFileFind::GetLastWriteTime

Llame a esta función miembro para obtener la última vez que se cambió el archivo.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parámetros

*pTimeStamp*<br/>
Puntero a una estructura [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) que contiene la hora a la que se escribió por última vez en el archivo.

*refTime*<br/>
Referencia a un objeto [ctime](../../atl-mfc-shared/reference/ctime-class.md) .

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 si no se realiza correctamente. `GetLastWriteTime`devuelve 0 solo si no se ha llamado a [FindNextFile](#findnextfile) nunca `CFileFind` en este objeto.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `GetLastWriteTime`de llamar a.

> [!NOTE]
>  No todos los sistemas de archivos usan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos subyacente o el servidor no admiten el atributo Time. Vea la estructura [Win32_Find_Data](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) para obtener información sobre los formatos de hora. En algunos sistemas de operaciones, la hora devuelta está en la zona horaria local del equipo donde se encuentra el archivo. Vea la API [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) de Win32 para obtener más información.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetLength](#getlength).

##  <a name="getlength"></a>  CFileFind::GetLength

Llame a esta función miembro para obtener la longitud del archivo encontrado, en bytes.

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud del archivo encontrado, en bytes.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `GetLength`de llamar a.

`GetLength`utiliza la estructura [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) de Win32 para obtener y devolver el valor del tamaño del archivo, en bytes.

> [!NOTE]
>  A partir de MFC 7,0 `GetLength` , admite tipos enteros de 64 bits. El código existente creado con esta versión más reciente de la biblioteca puede producir advertencias de truncamiento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

##  <a name="getroot"></a>  CFileFind::GetRoot

Llame a esta función miembro para obtener la raíz del archivo encontrado.

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>Valor devuelto

Raíz de la búsqueda activa.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `GetRoot`de llamar a.

Esta función miembro devuelve el especificador de unidad y el nombre de ruta de acceso que se usan para iniciar una búsqueda. Por ejemplo, al llamar a [FindFile](#findfile) con `*.dat`, `GetRoot` devuelve una cadena vacía. Pasar una ruta de acceso, `c:\windows\system\*.dll`como, a `GetRoot` los `c:\windows\system\`resultados que `FindFile` devuelven.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetFileName](#getfilename).

##  <a name="isarchived"></a>  CFileFind::IsArchived

Llame a esta función miembro para determinar si el archivo encontrado se ha archivado.

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Las aplicaciones marcan un archivo de almacenamiento, del que se va a realizar una copia de seguridad o que se va a quitar, con FILE_ATTRIBUTE_ARCHIVE, un atributo de archivo identificado en la estructura [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) .

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `IsArchived`de llamar a.

Vea la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de los atributos de archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetLength](#getlength).

##  <a name="iscompressed"></a>  CFileFind::IsCompressed

Llame a esta función miembro para determinar si el archivo encontrado está comprimido.

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Un archivo comprimido se marca con FILE_ATTRIBUTE_COMPRESSED, un atributo de archivo identificado en la estructura [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) . Para un archivo, este atributo indica que todos los datos del archivo están comprimidos. Para un directorio, este atributo indica que la compresión es el valor predeterminado para los archivos y subdirectorios creados recientemente.

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `IsCompressed`de llamar a.

Vea la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de los atributos de archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetLength](#getlength).

##  <a name="isdirectory"></a>  CFileFind::IsDirectory

Llame a esta función miembro para determinar si el archivo encontrado es un directorio.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Un archivo que es un directorio se marca con FILE_ATTRIBUTE_DIRECTORY un atributo de archivo identificado en la estructura [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) .

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `IsDirectory`de llamar a.

Vea la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de los atributos de archivo.

### <a name="example"></a>Ejemplo

Este pequeño programa recorre todos los directorios de C:\ unidad e imprime el nombre del directorio.

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

##  <a name="isdots"></a>  CFileFind::IsDots

Llame a esta función miembro para comprobar el directorio actual y los marcadores del directorio principal mientras se recorren en iteración los archivos.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo encontrado tiene el nombre "." o "..", lo que indica que el archivo encontrado es realmente un directorio. De lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `IsDots`de llamar a.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: IsDirectory](#isdirectory).

##  <a name="ishidden"></a>  CFileFind::IsHidden

Llame a esta función miembro para determinar si el archivo encontrado está oculto.

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Archivos ocultos, marcados con FILE_ATTRIBUTE_HIDDEN, un atributo de archivo identificado en la estructura [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) . Los archivos ocultos no se incluyen en una lista de directorios normales.

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `IsHidden`de llamar a.

Vea la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de los atributos de archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetLength](#getlength).

##  <a name="isnormal"></a>  CFileFind::IsNormal

Llame a esta función miembro para determinar si el archivo encontrado es un archivo normal.

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Archivos marcados con FILE_ATTRIBUTE_NORMAL, un atributo de archivo identificado en la estructura [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) . Un archivo normal no tiene ningún otro conjunto de atributos. Todos los demás atributos de archivo reemplazan a este atributo.

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `IsNormal`de llamar a.

Vea la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de los atributos de archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetLength](#getlength).

##  <a name="isreadonly"></a>  CFileFind::IsReadOnly

Llame a esta función miembro para determinar si el archivo encontrado es de solo lectura.

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Un archivo de solo lectura se marca con FILE_ATTRIBUTE_READONLY, un atributo de archivo identificado en la estructura [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) . Las aplicaciones pueden leer estos archivos, pero no pueden escribir en ellos ni eliminarlos.

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `IsReadOnly`de llamar a.

Vea la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de los atributos de archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetLength](#getlength).

##  <a name="issystem"></a>  CFileFind::IsSystem

Llame a esta función miembro para determinar si el archivo encontrado es un archivo del sistema.

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Un archivo del sistema se marca con FILE_ATTRIBUTE_SYSTEM,, un atributo de archivo identificado en la estructura [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) . Un archivo del sistema es parte del sistema operativo, o lo utiliza exclusivamente.

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `IsSystem`de llamar a.

Vea la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de los atributos de archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetLength](#getlength).

##  <a name="istemporary"></a>  CFileFind::IsTemporary

Llame a esta función miembro para determinar si el archivo encontrado es un archivo temporal.

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Un archivo temporal se marca con FILE_ATTRIBUTE_TEMPORARY, un atributo de archivo identificado en la estructura [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) . Se usa un archivo temporal para el almacenamiento temporal. Las aplicaciones solo deben escribir en el archivo si es absolutamente necesario. La mayoría de los datos del archivo permanecen en la memoria sin vaciarse en el medio porque el archivo se eliminará pronto.

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `IsTemporary`de llamar a.

Vea la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de los atributos de archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind:: GetLength](#getlength).

##  <a name="m_ptm"></a>  CFileFind::m_pTM

Puntero a un `CAtlTransactionManager` objeto.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Comentarios

##  <a name="matchesmask"></a>  CFileFind::MatchesMask

Llame a esta función miembro para probar los atributos de archivo en el archivo encontrado.

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>Parámetros

*dwMask*<br/>
Especifica uno o más atributos de archivo, identificados en la estructura [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa) , para el archivo encontrado. Para buscar varios atributos, utilice el operador OR bit a&#124;bit (). Cualquier combinación de los siguientes atributos es aceptable:

- FILE_ATTRIBUTE_ARCHIVE el archivo es un archivo de almacenamiento. Las aplicaciones usan este atributo para marcar los archivos para la copia de seguridad o la eliminación.

- FILE_ATTRIBUTE_COMPRESSED el archivo o el directorio está comprimido. Para un archivo, esto significa que todos los datos del archivo están comprimidos. Para un directorio, esto significa que la compresión es el valor predeterminado para los archivos y subdirectorios recién creados.

- FILE_ATTRIBUTE_DIRECTORY el archivo es un directorio.

- FILE_ATTRIBUTE_NORMAL el archivo no tiene ningún otro conjunto de atributos. Este atributo solo es válido si se usa por sí solo. Todos los demás atributos de archivo reemplazan a este atributo.

- FILE_ATTRIBUTE_HIDDEN el archivo está oculto. No se incluirá en una lista de directorios normal.

- FILE_ATTRIBUTE_READONLY el archivo es de solo lectura. Las aplicaciones pueden leer el archivo pero no pueden escribir en él ni eliminarlo.

- FILE_ATTRIBUTE_SYSTEM el archivo forma parte de o lo utiliza exclusivamente el sistema operativo.

- FILE_ATTRIBUTE_TEMPORARY el archivo se usa para el almacenamiento temporal. Las aplicaciones solo deben escribir en el archivo si es absolutamente necesario. La mayoría de los datos del archivo permanecen en la memoria sin vaciarse en el medio porque el archivo se eliminará pronto.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Para obtener información de error extendida, llame a la función [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror)de Win32.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `MatchesMask`de llamar a.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind (clase)](../../mfc/reference/cftpfilefind-class.md)<br/>
[CGopherFileFind (clase)](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile (clase)](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile (clase)](../../mfc/reference/chttpfile-class.md)
