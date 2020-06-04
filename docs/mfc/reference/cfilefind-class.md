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
ms.openlocfilehash: 5bb53a6abf7040bd6ee9f5f2cf56b0feb4d62e66
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755032"
---
# <a name="cfilefind-class"></a>Clase CFileFind

Realiza búsquedas de archivos locales y es la clase base para [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) y [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md), que realizan búsquedas de archivos de Internet.

## <a name="syntax"></a>Sintaxis

```
class CFileFind : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFileFind::CFileFind](#cfilefind)|Construye un objeto `CFileFind`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFileFind::Cerrar](#close)|Cierra la solicitud de búsqueda.|
|[CFileFind::FindFile](#findfile)|Busca en un directorio un nombre de archivo especificado.|
|[CFileFind::FindNextFile](#findnextfile)|Continúa una búsqueda de archivos de una llamada anterior a [FindFile](#findfile).|
|[CFileFind::GetCreationTime](#getcreationtime)|Obtiene la hora en que se creó el archivo.|
|[CFileFind::GetFileName](#getfilename)|Obtiene el nombre, incluida la extensión, del archivo encontrado|
|[CFileFind::GetFilePath](#getfilepath)|Obtiene toda la ruta de acceso del archivo encontrado.|
|[CFileFind::GetFileTitle](#getfiletitle)|Obtiene el título del archivo encontrado. El título no incluye la extensión.|
|[CFileFind::GetFileURL](#getfileurl)|Obtiene la dirección URL, incluida la ruta de acceso del archivo, del archivo encontrado.|
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|Obtiene la hora en la que se accedió por última vez al archivo.|
|[CFileFind::GetLastWriteTime](#getlastwritetime)|Obtiene la hora en que se cambió y guardó el archivo por última vez.|
|[CFileFind::GetLength](#getlength)|Obtiene la longitud del archivo encontrado, en bytes.|
|[CFileFind::GetRoot](#getroot)|Obtiene el directorio raíz del archivo encontrado.|
|[CFileFind::IsArchived](#isarchived)|Determina si el archivo encontrado está archivado.|
|[CFileFind::IsCompressed](#iscompressed)|Determina si el archivo encontrado está comprimido.|
|[CFileFind::IsDirectory](#isdirectory)|Determina si el archivo encontrado es un directorio.|
|[CFileFind::IsDots](#isdots)|Determina si el nombre del archivo encontrado tiene el nombre "." o "..", lo que indica que en realidad es un directorio.|
|[CFileFind::IsHidden](#ishidden)|Determina si el archivo encontrado está oculto.|
|[CFileFind::IsNormal](#isnormal)|Determina si el archivo encontrado es normal (en otras palabras, no tiene otros atributos).|
|[CFileFind::IsreadOnly](#isreadonly)|Determina si el archivo encontrado es de solo lectura.|
|[CFileFind::IsSystem](#issystem)|Determina si el archivo encontrado es un archivo del sistema.|
|[CFileFind::IsTemporary](#istemporary)|Determina si el archivo encontrado es temporal.|
|[CFileFind::MatchesMask](#matchesmask)|Indica los atributos de archivo deseados del archivo que se va a encontrar.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CFileFind::CloseContext](#closecontext)|Cierra el archivo especificado por el identificador de búsqueda actual.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CFileFind::m_pTM](#m_ptm)|Puntero a `CAtlTransactionManager` un objeto.|

## <a name="remarks"></a>Observaciones

`CFileFind`incluye funciones miembro que inician una búsqueda, localizan un archivo y devuelven el título, el nombre o la ruta de acceso del archivo. Para las búsquedas de Internet, la función miembro [GetFileURL](#getfileurl) devuelve la dirección URL del archivo.

`CFileFind`es la clase base para otras dos clases `CGopherFileFind` MFC diseñadas para buscar `CFtpFileFind` determinados tipos de servidor: funciona específicamente con servidores gopher y funciona específicamente con servidores FTP. Juntos, estas tres clases proporcionan un mecanismo sin problemas para que el cliente encuentre archivos, independientemente del protocolo de servidor, el tipo de archivo o la ubicación, en un equipo local o en un servidor remoto.

El código siguiente enumerará todos los archivos del directorio actual, imprimiendo el nombre de cada archivo:

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

Para mantener el ejemplo simple, este código `cout` utiliza la clase C++ Standard Library. La `cout` línea podría sustituirse por `CListBox::AddString`una llamada a , por ejemplo, en un programa con una interfaz gráfica de usuario.

Para obtener más información `CFileFind` sobre cómo usar y las otras clases De WinInet, consulte el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="cfilefindcfilefind"></a><a name="cfilefind"></a>CFileFind::CFileFind

Se llama a esta `CFileFind` función miembro cuando se construye un objeto.

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parámetros

*Ptm*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindclose"></a><a name="close"></a>CFileFind::Cerrar

Llame a esta función miembro para finalizar la búsqueda, restablecer el contexto y liberar todos los recursos.

```cpp
void Close();
```

### <a name="remarks"></a>Observaciones

Después `Close`de llamar a , `CFileFind` no es necesario crear una nueva instancia antes de llamar a [FindFile](#findfile) para iniciar una nueva búsqueda.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindclosecontext"></a><a name="closecontext"></a>CFileFind::CloseContext

Cierra el archivo especificado por el identificador de búsqueda actual.

```
virtual void CloseContext();
```

### <a name="remarks"></a>Observaciones

Cierra el archivo especificado por el valor actual del identificador de búsqueda. Invalide esta función para cambiar el comportamiento predeterminado.

Debe llamar a las funciones [FindFile](#findfile) o [FindNextFile](#findnextfile) al menos una vez para recuperar un identificador de búsqueda válido. Las `FindFile` `FindNextFile` funciones y utilizan el identificador de búsqueda para localizar archivos con nombres que coinciden con un nombre determinado.

## <a name="cfilefindfindfile"></a><a name="findfile"></a>CFileFind::FindFile

Llame a esta función miembro para abrir una búsqueda de archivos.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>Parámetros

*pstrName*<br/>
Puntero a una cadena que contiene el nombre del archivo que se va a buscar. Si pasa NULL para *pstrName* `FindFile` ,\*realiza una búsqueda comodín (*. ).

*dwUnused*<br/>
Reservado para `FindFile` hacer polimórfico con clases derivadas. Debe ser 0.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Para obtener información de error ampliada, llame a la función [GetLastError de](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)Win32 .

### <a name="remarks"></a>Observaciones

Después `FindFile` de llamar para comenzar la búsqueda de archivos, llame a [FindNextFile](#findnextfile) para recuperar los archivos posteriores. Debe llamar `FindNextFile` al menos una vez antes de llamar a cualquiera de las siguientes funciones miembro de atributo:

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

  Vea el ejemplo de [CFileFind::IsDirectory](#isdirectory).

## <a name="cfilefindfindnextfile"></a><a name="findnextfile"></a>CFileFind::FindNextFile

Llame a esta función miembro para continuar una búsqueda de archivos desde una llamada anterior a [FindFile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si hay más archivos; cero si el archivo encontrado es el último en el directorio o si se produjo un error. Para obtener información de error ampliada, llame a la función [GetLastError de](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)Win32 . Si el archivo encontrado es el último archivo del directorio, o `GetLastError` si no se encuentra ningún archivo coincidente, la función devuelve ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Observaciones

Debe llamar `FindNextFile` al menos una vez antes de llamar a cualquiera de las siguientes funciones miembro de atributo:

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

`FindNextFile`ajusta la función Debúsqueda de Win32 [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::IsDirectory](#isdirectory).

## <a name="cfilefindgetcreationtime"></a><a name="getcreationtime"></a>CFileFind::GetCreationTime

Llame a esta función miembro para obtener la hora en que se creó el archivo especificado.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parámetros

*pTimeStamp*<br/>
Puntero a una estructura [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) que contiene la hora en que se creó el archivo.

*refTime*<br/>
Una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 si no se realiza correctamente. `GetCreationTime`devuelve 0 solo si nunca se `CFileFind` ha llamado a [FindNextFile](#findnextfile) en este objeto.

### <a name="remarks"></a>Observaciones

Debe llamar a [FindNextFile](#findnextfile) al `GetCreationTime`menos una vez antes de llamar a .

> [!NOTE]
> No todos los sistemas de archivos utilizan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos subyacente o el servidor no admite mantener el atributo time. Consulte la estructura [de WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) para obtener información sobre los formatos de tiempo. En algunos sistemas operativos, la hora devuelta está en la zona horaria local de la máquina donde se encuentra el archivo. Consulte la API [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) de Win32 para obtener más información.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetLength](#getlength).

## <a name="cfilefindgetfilename"></a><a name="getfilename"></a>CFileFind::GetFileName

Llame a esta función miembro para obtener el nombre del archivo encontrado.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre del archivo encontrado más recientemente.

### <a name="remarks"></a>Observaciones

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes de llamar a GetFileName.

`GetFileName`es una `CFileFind` de las tres funciones miembro que devuelven alguna forma del nombre de archivo. La siguiente lista describe los tres y cómo varían:

- `GetFileName`devuelve el nombre del archivo, incluida la extensión. Por ejemplo, `GetFileName` una llamada para generar un mensaje de usuario sobre el archivo *c:-myhtml-myfile.txt* devuelve el nombre de archivo *myfile.txt*.

- [GetFilePath](#getfilepath) devuelve la ruta de acceso completa del archivo. Por ejemplo, `GetFilePath` una llamada para generar un mensaje de usuario sobre el archivo *c:-myhtml-myfile.txt* devuelve la ruta de acceso del archivo *c:-myhtml-myfile.txt*.

- [GetFileTitle](#getfiletitle) devuelve el nombre de archivo, excluyendo la extensión de archivo. Por ejemplo, `GetFileTitle` una llamada para generar un mensaje de usuario sobre el archivo *c:-myhtml-myfile.txt* devuelve el título del archivo *myfile*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

## <a name="cfilefindgetfilepath"></a><a name="getfilepath"></a>CFileFind::GetFilePath

Llame a esta función miembro para obtener la ruta de acceso completa del archivo especificado.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso del archivo especificado.

### <a name="remarks"></a>Observaciones

Debe llamar a [FindNextFile](#findnextfile) al `GetFilePath`menos una vez antes de llamar a .

`GetFilePath`es una `CFileFind` de las tres funciones miembro que devuelven alguna forma del nombre de archivo. La siguiente lista describe los tres y cómo varían:

- [GetFileName](#getfilename) devuelve el nombre de archivo, incluida la extensión. Por ejemplo, `GetFileName` una llamada para generar un mensaje de usuario sobre el archivo *c:-myhtml-myfile.txt* devuelve el nombre de archivo *myfile.txt*.

- `GetFilePath`devuelve la ruta de acceso completa del archivo. Por ejemplo, `GetFilePath` al llamar para generar `c:\myhtml\myfile.txt` un mensaje `c:\myhtml\myfile.txt`de usuario sobre el archivo, se devuelve la ruta de acceso del archivo.

- [GetFileTitle](#getfiletitle) devuelve el nombre de archivo, excluyendo la extensión de archivo. Por ejemplo, `GetFileTitle` una llamada para generar un mensaje de usuario sobre el archivo *c:-myhtml-myfile.txt* devuelve el título del archivo *myfile*.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindgetfiletitle"></a><a name="getfiletitle"></a>CFileFind::GetFileTitle

Llame a esta función miembro para obtener el título del archivo encontrado.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Valor devuelto

El título del archivo.

### <a name="remarks"></a>Observaciones

Debe llamar a [FindNextFile](#findnextfile) al `GetFileTitle`menos una vez antes de llamar a .

`GetFileTitle`es una `CFileFind` de las tres funciones miembro que devuelven alguna forma del nombre de archivo. La siguiente lista describe los tres y cómo varían:

- [GetFileName](#getfilename) devuelve el nombre de archivo, incluida la extensión. Por ejemplo, `GetFileName` una llamada para generar un mensaje de usuario sobre el archivo *c:-myhtml-myfile.txt* devuelve el nombre de archivo *myfile.txt*.

- [GetFilePath](#getfilepath) devuelve la ruta de acceso completa del archivo. Por ejemplo, `GetFilePath` una llamada para generar un mensaje de usuario sobre el archivo *c:-myhtml-myfile.txt* devuelve la ruta de acceso del archivo *c:-myhtml-myfile.txt*.

- `GetFileTitle`devuelve el nombre de archivo, excluyendo la extensión de archivo. Por ejemplo, `GetFileTitle` una llamada para generar un mensaje de usuario sobre el archivo *c:-myhtml-myfile.txt* devuelve el título del archivo *myfile*.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindgetfileurl"></a><a name="getfileurl"></a>CFileFind::GetFileURL

Llame a esta función miembro para recuperar la dirección URL especificada.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Valor devuelto

La dirección URL completa.

### <a name="remarks"></a>Observaciones

Debe llamar a [FindNextFile](#findnextfile) al `GetFileURL`menos una vez antes de llamar a .

`GetFileURL`es similar a la función miembro [GetFilePath](#getfilepath), `file://path`excepto que devuelve la dirección URL en el formulario . Por ejemplo, `GetFileURL` al llamar para obtener la dirección `file://c:\myhtml\myfile.txt`URL completa de *myfile.txt,* se devuelve la dirección URL.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a>CFileFind::GetLastAccessTime

Llame a esta función miembro para obtener la hora en que se tuvo acceso por última vez al archivo especificado.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Parámetros

*refTime*<br/>
Una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto.

*pTimeStamp*<br/>
Puntero a una estructura [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) que contiene la última vez que se tuvo acceso al archivo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 si no se realiza correctamente. `GetLastAccessTime`devuelve 0 solo si nunca se `CFileFind` ha llamado a [FindNextFile](#findnextfile) en este objeto.

### <a name="remarks"></a>Observaciones

Debe llamar a [FindNextFile](#findnextfile) al `GetLastAccessTime`menos una vez antes de llamar a .

> [!NOTE]
> No todos los sistemas de archivos utilizan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos subyacente o el servidor no admite mantener el atributo time. Consulte la estructura [de WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) para obtener información sobre los formatos de tiempo. En algunos sistemas operativos, la hora devuelta está en la zona horaria local de la máquina donde se encuentra el archivo. Consulte la API [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) de Win32 para obtener más información.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetLength](#getlength).

## <a name="cfilefindgetlastwritetime"></a><a name="getlastwritetime"></a>CFileFind::GetLastWriteTime

Llame a esta función miembro para obtener la última vez que se cambió el archivo.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parámetros

*pTimeStamp*<br/>
Puntero a una estructura [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) que contiene la última vez que se escribió el archivo.

*refTime*<br/>
Una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 si no se realiza correctamente. `GetLastWriteTime`devuelve 0 solo si nunca se `CFileFind` ha llamado a [FindNextFile](#findnextfile) en este objeto.

### <a name="remarks"></a>Observaciones

Debe llamar a [FindNextFile](#findnextfile) al `GetLastWriteTime`menos una vez antes de llamar a .

> [!NOTE]
> No todos los sistemas de archivos utilizan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos subyacente o el servidor no admite mantener el atributo time. Consulte la estructura [de WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) para obtener información sobre los formatos de tiempo. En algunos sistemas operativos, la hora devuelta está en la zona horaria local de la máquina donde se encuentra el archivo. Consulte la API [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) de Win32 para obtener más información.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetLength](#getlength).

## <a name="cfilefindgetlength"></a><a name="getlength"></a>CFileFind::GetLength

Llame a esta función miembro para obtener la longitud del archivo encontrado, en bytes.

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud del archivo encontrado, en bytes.

### <a name="remarks"></a>Observaciones

Debe llamar a [FindNextFile](#findnextfile) al `GetLength`menos una vez antes de llamar a .

`GetLength`utiliza la estructura Win32 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) para obtener y devolver el valor del tamaño del archivo, en bytes.

> [!NOTE]
> A partir de MFC `GetLength` 7.0, admite tipos enteros de 64 bits. El código existente anteriormente compilado con esta versión más reciente de la biblioteca puede dar lugar a advertencias de truncamiento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

## <a name="cfilefindgetroot"></a><a name="getroot"></a>CFileFind::GetRoot

Llame a esta función miembro para obtener la raíz del archivo encontrado.

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>Valor devuelto

La raíz de la búsqueda activa.

### <a name="remarks"></a>Observaciones

Debe llamar a [FindNextFile](#findnextfile) al `GetRoot`menos una vez antes de llamar a .

Esta función miembro devuelve el especificador de unidad y el nombre de ruta de acceso utilizados para iniciar una búsqueda. Por ejemplo, llamar `*.dat` a `GetRoot` [FindFile](#findfile) con resultados en la devolución de una cadena vacía. Pasar una ruta `c:\windows\system\*.dll`de `FindFile` acceso, como , a los resultados `GetRoot` que devuelven `c:\windows\system\`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindisarchived"></a><a name="isarchived"></a>CFileFind::IsArchived

Llame a esta función miembro para determinar si se archiva el archivo encontrado.

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Las aplicaciones marcan un archivo de archivado, que se va a realizar una copia de seguridad o quitar, con FILE_ATTRIBUTE_ARCHIVE, un atributo de archivo identificado en la estructura [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)

Debe llamar a [FindNextFile](#findnextfile) al `IsArchived`menos una vez antes de llamar a .

Consulte la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de atributos de archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetLength](#getlength).

## <a name="cfilefindiscompressed"></a><a name="iscompressed"></a>CFileFind::IsCompressed

Llame a esta función miembro para determinar si el archivo encontrado está comprimido.

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Un archivo comprimido se marca con FILE_ATTRIBUTE_COMPRESSED, un atributo de archivo identificado en la estructura [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Para un archivo, este atributo indica que todos los datos del archivo están comprimidos. Para un directorio, este atributo indica que la compresión es el valor predeterminado para los archivos y subdirectorios recién creados.

Debe llamar a [FindNextFile](#findnextfile) al `IsCompressed`menos una vez antes de llamar a .

Consulte la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de atributos de archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetLength](#getlength).

## <a name="cfilefindisdirectory"></a><a name="isdirectory"></a>CFileFind::IsDirectory

Llame a esta función miembro para determinar si el archivo encontrado es un directorio.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Un archivo que es un directorio se marca con FILE_ATTRIBUTE_DIRECTORY un atributo de archivo identificado en la estructura [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)

Debe llamar a [FindNextFile](#findnextfile) al `IsDirectory`menos una vez antes de llamar a .

Consulte la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de atributos de archivo.

### <a name="example"></a>Ejemplo

Este pequeño programa refunde todos los directorios de la C: unidad e imprime el nombre del directorio.

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

## <a name="cfilefindisdots"></a><a name="isdots"></a>CFileFind::IsDots

Llame a esta función miembro para probar el directorio actual y los marcadores de directorio primario mientras recorre en iteración los archivos.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo encontrado tiene el nombre "." o "..", lo que indica que el archivo encontrado es realmente un directorio. De lo contrario 0.

### <a name="remarks"></a>Observaciones

Debe llamar a [FindNextFile](#findnextfile) al `IsDots`menos una vez antes de llamar a .

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::IsDirectory](#isdirectory).

## <a name="cfilefindishidden"></a><a name="ishidden"></a>CFileFind::IsHidden

Llame a esta función miembro para determinar si el archivo encontrado está oculto.

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Archivos ocultos, que están marcados con FILE_ATTRIBUTE_HIDDEN, un atributo de archivo identificado en la estructura [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Un archivo oculto no se incluye en una lista de directorios normal.

Debe llamar a [FindNextFile](#findnextfile) al `IsHidden`menos una vez antes de llamar a .

Consulte la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de atributos de archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetLength](#getlength).

## <a name="cfilefindisnormal"></a><a name="isnormal"></a>CFileFind::IsNormal

Llame a esta función miembro para determinar si el archivo encontrado es un archivo normal.

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Archivos marcados con FILE_ATTRIBUTE_NORMAL, un atributo de archivo identificado en la estructura [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Un archivo normal no tiene otros atributos establecidos. Todos los demás atributos de archivo invalidan este atributo.

Debe llamar a [FindNextFile](#findnextfile) al `IsNormal`menos una vez antes de llamar a .

Consulte la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de atributos de archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetLength](#getlength).

## <a name="cfilefindisreadonly"></a><a name="isreadonly"></a>CFileFind::IsreadOnly

Llame a esta función miembro para determinar si el archivo encontrado es de solo lectura.

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Un archivo de solo lectura se marca con FILE_ATTRIBUTE_READONLY, un atributo de archivo identificado en la estructura [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Las aplicaciones pueden leer un archivo de este tipo, pero no pueden escribir en él ni eliminarlo.

Debe llamar a [FindNextFile](#findnextfile) al `IsReadOnly`menos una vez antes de llamar a .

Consulte la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de atributos de archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetLength](#getlength).

## <a name="cfilefindissystem"></a><a name="issystem"></a>CFileFind::IsSystem

Llame a esta función miembro para determinar si el archivo encontrado es un archivo del sistema.

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Un archivo de sistema se marca con FILE_ATTRIBUTE_SYSTEM, un atributo de archivo identificado en la estructura [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Un archivo de sistema forma parte del sistema operativo o lo utiliza exclusivamente.

Debe llamar a [FindNextFile](#findnextfile) al `IsSystem`menos una vez antes de llamar a .

Consulte la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de atributos de archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetLength](#getlength).

## <a name="cfilefindistemporary"></a><a name="istemporary"></a>CFileFind::IsTemporary

Llame a esta función miembro para determinar si el archivo encontrado es un archivo temporal.

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Un archivo temporal se marca con FILE_ATTRIBUTE_TEMPORARY, un atributo de archivo identificado en la estructura [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Se utiliza un archivo temporal para el almacenamiento temporal. Las aplicaciones deben escribir en el archivo sólo si es absolutamente necesario. La mayoría de los datos del archivo permanecen en la memoria sin ser vaciados en el medio porque el archivo se eliminará pronto.

Debe llamar a [FindNextFile](#findnextfile) al `IsTemporary`menos una vez antes de llamar a .

Consulte la función miembro [MatchesMask](#matchesmask) para obtener una lista completa de atributos de archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFileFind::GetLength](#getlength).

## <a name="cfilefindm_ptm"></a><a name="m_ptm"></a>CFileFind::m_pTM

Puntero a `CAtlTransactionManager` un objeto.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Observaciones

## <a name="cfilefindmatchesmask"></a><a name="matchesmask"></a>CFileFind::MatchesMask

Llame a esta función miembro para probar los atributos de archivo en el archivo encontrado.

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>Parámetros

*dwMask*<br/>
Especifica uno o varios atributos de archivo, identificados en la estructura [WIN32_FIND_DATA,](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) para el archivo encontrado. Para buscar varios atributos, utilice el operador OR (&#124;) bit a bit. Cualquier combinación de los siguientes atributos es aceptable:

- FILE_ATTRIBUTE_ARCHIVE El archivo es un archivo de almacenamiento. Las aplicaciones utilizan este atributo para marcar los archivos para la copia de seguridad o eliminación.

- FILE_ATTRIBUTE_COMPRESSED El archivo o directorio está comprimido. Para un archivo, esto significa que todos los datos del archivo están comprimidos. Para un directorio, esto significa que la compresión es el valor predeterminado para los archivos y subdirectorios recién creados.

- FILE_ATTRIBUTE_DIRECTORY El archivo es un directorio.

- FILE_ATTRIBUTE_NORMAL El archivo no tiene ningún otro atributo establecido. Este atributo solo es válido si se usa solo. Todos los demás atributos de archivo invalidan este atributo.

- FILE_ATTRIBUTE_HIDDEN El archivo está oculto. No debe incluirse en una lista de directorios normal.

- FILE_ATTRIBUTE_READONLY El archivo es de solo lectura. Las aplicaciones pueden leer el archivo, pero no pueden escribir en él ni eliminarlo.

- FILE_ATTRIBUTE_SYSTEM El archivo forma parte o es utilizado exclusivamente por el sistema operativo.

- FILE_ATTRIBUTE_TEMPORARY El archivo se utiliza para el almacenamiento temporal. Las aplicaciones deben escribir en el archivo sólo si es absolutamente necesario. La mayoría de los datos del archivo permanecen en la memoria sin ser vaciados en el medio porque el archivo se eliminará pronto.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Para obtener información de error ampliada, llame a la función [GetLastError de](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)Win32 .

### <a name="remarks"></a>Observaciones

Debe llamar a [FindNextFile](#findnextfile) al `MatchesMask`menos una vez antes de llamar a .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]

## <a name="see-also"></a>Consulte también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind (clase)](../../mfc/reference/cftpfilefind-class.md)<br/>
[CGopherFileFind (clase)](../../mfc/reference/cgopherfilefind-class.md)<br/>
[Clase CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Clase CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Clase CHttpFile](../../mfc/reference/chttpfile-class.md)
