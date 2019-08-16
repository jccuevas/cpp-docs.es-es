---
title: Clase CGopherFileFind
ms.date: 11/04/2016
f1_keywords:
- CGopherFileFind
- AFXINET/CGopherFileFind
- AFXINET/CGopherFileFind::CGopherFileFind
- AFXINET/CGopherFileFind::FindFile
- AFXINET/CGopherFileFind::FindNextFile
- AFXINET/CGopherFileFind::GetCreationTime
- AFXINET/CGopherFileFind::GetLastAccessTime
- AFXINET/CGopherFileFind::GetLastWriteTime
- AFXINET/CGopherFileFind::GetLength
- AFXINET/CGopherFileFind::GetLocator
- AFXINET/CGopherFileFind::GetScreenName
- AFXINET/CGopherFileFind::IsDots
helpviewer_keywords:
- CGopherFileFind [MFC], CGopherFileFind
- CGopherFileFind [MFC], FindFile
- CGopherFileFind [MFC], FindNextFile
- CGopherFileFind [MFC], GetCreationTime
- CGopherFileFind [MFC], GetLastAccessTime
- CGopherFileFind [MFC], GetLastWriteTime
- CGopherFileFind [MFC], GetLength
- CGopherFileFind [MFC], GetLocator
- CGopherFileFind [MFC], GetScreenName
- CGopherFileFind [MFC], IsDots
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
ms.openlocfilehash: 55c40fc04934f00ccb541a01cce611d9532bee1a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506175"
---
# <a name="cgopherfilefind-class"></a>Clase CGopherFileFind

Ayuda en las búsquedas de archivos de Internet de servidores gopher.

> [!NOTE]
>  Las clases `CGopherConnection` `CGopherFile` ,`CGopherLocator` , y sus miembros están desusadas porque no funcionan en la plataforma Windows XP, pero seguirán funcionando en plataformas anteriores. `CGopherFileFind`

## <a name="syntax"></a>Sintaxis

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|Construye un objeto `CGopherFileFind`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CGopherFileFind::FindFile](#findfile)|Busca un archivo en un servidor gopher.|
|[CGopherFileFind::FindNextFile](#findnextfile)|Continúa una búsqueda de archivos de una llamada anterior a [findfile](#findfile).|
|[CGopherFileFind::GetCreationTime](#getcreationtime)|Obtiene la hora a la que se creó el archivo especificado.|
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|Obtiene la hora a la que se produjo el último acceso al archivo especificado.|
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|Obtiene la hora a la que se escribió por última vez en el archivo especificado.|
|[CGopherFileFind::GetLength](#getlength)|Obtiene la longitud del archivo encontrado, en bytes.|
|[CGopherFileFind::GetLocator](#getlocator)|Obtiene un `CGopherLocator` objeto.|
|[CGopherFileFind::GetScreenName](#getscreenname)|Obtiene el nombre de una pantalla Gopher.|
|[CGopherFileFind::IsDots](#isdots)|Comprueba el directorio actual y los marcadores del directorio principal mientras se recorren en iteración los archivos.|

## <a name="remarks"></a>Comentarios

`CGopherFileFind`incluye funciones miembro que inician una búsqueda, localizan un archivo y devuelven la dirección URL de un archivo.

Otras clases MFC diseñadas para Internet y el archivo local buscado incluyen [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) y [CFileFind](../../mfc/reference/cfilefind-class.md). Junto con `CGopherFileFind`, estas clases proporcionan un mecanismo sin problemas para que el usuario encuentre archivos específicos, independientemente del Protocolo de servidor, el tipo de archivo o la ubicación (un equipo local o un servidor remoto). Tenga en cuenta que no hay ninguna clase MFC para realizar búsquedas en servidores HTTP porque HTTP no admite la manipulación directa de archivos requerida por las búsquedas.

> [!NOTE]
> `CGopherFileFind`no admite las siguientes funciones miembro de su clase base [CFileFind](../../mfc/reference/cfilefind-class.md):

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

Además, cuando se usa con `CGopherFileFind`, la `CFileFind` función miembro [IsDots](../../mfc/reference/cfilefind-class.md#isdots) siempre es false.

Para obtener más información sobre cómo usar `CGopherFileFind` y las demás clases WinInet, vea el artículo [programación en Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet. h

##  <a name="cgopherfilefind"></a>  CGopherFileFind::CGopherFileFind

Se llama a esta función miembro para construir `CGopherFileFind` un objeto.

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*pConnection*<br/>
Un puntero a un objeto [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) .

*dwContext*<br/>
Identificador de contexto para la operación. Vea la **sección Comentarios** para obtener más información sobre *dwContext*.

### <a name="remarks"></a>Comentarios

MFC envía el valor predeterminado de *dwContext* `CGopherFileFind` al objeto desde el objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) que creó el `CGopherFileFind` objeto. Al construir un `CGopherFileFind` objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo [Internet First Steps: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

##  <a name="findfile"></a>  CGopherFileFind::FindFile

Llame a esta función miembro para buscar un archivo Gopher.

```
virtual BOOL FindFile(
    CGopherLocator& refLocator,
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);

virtual BOOL FindFile(
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Parámetros

*refLocator*<br/>
Referencia a un objeto [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

*pstrString*<br/>
Puntero a una cadena que contiene el nombre de archivo.

*dwFlags*<br/>
Marcas que describen cómo controlar esta sesión. Las marcas válidas son:

- INTERNET_FLAG_RELOAD obtenga los datos del servidor remoto, incluso si está almacenado en caché localmente.

- INTERNET_FLAG_DONT_CACHE no almacenan en caché los datos, ya sea de forma local o en cualquier puerta de enlace.

- INTERNET_FLAG_SECURE solicitud de transacciones seguras en la conexión con Capa de sockets seguros o PCT. Esta marca solo es aplicable a las solicitudes HTTP.

- INTERNET_FLAG_USE_EXISTING si es posible, vuelva a usar las conexiones existentes con el `FindFile` servidor para las nuevas solicitudes, en lugar de crear una nueva sesión para cada solicitud.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Para obtener información de error extendida, llame a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)de Win32.

### <a name="remarks"></a>Comentarios

Después de `FindFile` llamar a para recuperar el primer objeto Gopher, puede llamar a [FindNextFile](#findnextfile) para recuperar los archivos Gopher posteriores.

##  <a name="findnextfile"></a>  CGopherFileFind::FindNextFile

Llame a esta función miembro para continuar con una búsqueda de archivos iniciada con una llamada a [CGopherFileFind:: findfile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si hay más archivos; cero si el archivo encontrado es el último del directorio o si se produjo un error. Para obtener información de error extendida, llame a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)de Win32. Si el archivo encontrado es el último archivo en el directorio o si no se encuentran archivos coincidentes, la `GetLastError` función devuelve ERROR_NO_MORE_FILES.

##  <a name="getcreationtime"></a>  CGopherFileFind::GetCreationTime

Obtiene la hora de creación del archivo actual.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parámetros

*pTimeStamp*<br/>
Puntero a una estructura [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) que contiene la hora a la que se creó el archivo.

*refTime*<br/>
Referencia a un objeto [ctime](../../atl-mfc-shared/reference/ctime-class.md) .

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 si no se realiza correctamente. `GetCreationTime`devuelve 0 solo si no se ha llamado a [FindNextFile](#findnextfile) nunca `CGopherFileFind` en este objeto.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `GetCreationTime`de llamar a.

> [!NOTE]
>  No todos los sistemas de archivos usan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos subyacente o el servidor no admiten el atributo Time. Vea la estructura [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) para obtener información sobre los formatos de hora. En algunos sistemas operativos, la hora devuelta está en la zona horaria local del equipo donde se encuentra el archivo. Vea la API [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) de Win32 para obtener más información.

##  <a name="getlastaccesstime"></a>  CGopherFileFind::GetLastAccessTime

Obtiene la hora a la que se produjo el último acceso al archivo especificado.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Parámetros

*refTime*<br/>
Referencia a un objeto [ctime](../../atl-mfc-shared/reference/ctime-class.md) .

*pTimeStamp*<br/>
Puntero a una estructura [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) que contiene la hora a la que se produjo el último acceso al archivo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 si no se realiza correctamente. `GetLastAccessTime`devuelve 0 solo si no se ha llamado a [FindNextFile](#findnextfile) nunca `CGopherFileFind` en este objeto.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `GetLastAccessTime`de llamar a.

> [!NOTE]
>  No todos los sistemas de archivos usan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos subyacente o el servidor no admiten el atributo Time. Vea la estructura [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) para obtener información sobre los formatos de hora. En algunos sistemas operativos, la hora devuelta está en la zona horaria local del equipo donde se encuentra el archivo. Vea la API [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) de Win32 para obtener más información.

##  <a name="getlastwritetime"></a>  CGopherFileFind::GetLastWriteTime

Obtiene la última vez que se cambió el archivo.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parámetros

*pTimeStamp*<br/>
Puntero a una estructura [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) que contiene la hora a la que se escribió por última vez en el archivo.

*refTime*<br/>
Referencia a un objeto [ctime](../../atl-mfc-shared/reference/ctime-class.md) .

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 si no se realiza correctamente. `GetLastWriteTime`devuelve 0 solo si no se ha llamado a [FindNextFile](#findnextfile) nunca `CGopherFileFind` en este objeto.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `GetLastWriteTime`de llamar a.

> [!NOTE]
>  No todos los sistemas de archivos usan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos subyacente o el servidor no admiten el atributo Time. Vea la estructura [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) para obtener información sobre los formatos de hora. En algunos sistemas operativos, la hora devuelta está en la zona horaria local del equipo donde se encuentra el archivo. Vea la API [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) de Win32 para obtener más información.

##  <a name="getlength"></a>  CGopherFileFind::GetLength

Llame a esta función miembro para obtener la longitud, en bytes, del archivo encontrado.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud, en bytes, del archivo encontrado.

### <a name="remarks"></a>Comentarios

`GetLength`utiliza la estructura de Win32 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) para obtener el valor del tamaño de archivo en bytes.

> [!NOTE]
>  A partir de MFC 7,0 `GetLength` , admite tipos enteros de 64 bits. El código existente creado con esta versión más reciente de la biblioteca puede producir advertencias de truncamiento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFile:: GetLength](../../mfc/reference/cfile-class.md#getlength) (la implementación de la clase base).

##  <a name="getlocator"></a>  CGopherFileFind::GetLocator

Llame a esta función miembro para obtener el objeto [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) que [findfile](#findfile) usa para buscar el archivo Gopher.

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto `CGopherLocator`.

##  <a name="getscreenname"></a>  CGopherFileFind::GetScreenName

Llame a esta función miembro para obtener el nombre de la pantalla Gopher.

```
CString GetScreenName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre de la pantalla Gopher.

##  <a name="isdots"></a>  CGopherFileFind::IsDots

Comprueba el directorio actual y los marcadores del directorio principal mientras se recorren en iteración los archivos.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo encontrado tiene el nombre "." o "..", lo que indica que el archivo encontrado es realmente un directorio. De lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes `IsDots`de llamar a.

## <a name="see-also"></a>Vea también

[CFileFind (clase)](../../mfc/reference/cfilefind-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind (clase)](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind (clase)](../../mfc/reference/cfilefind-class.md)<br/>
[CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile (clase)](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile (clase)](../../mfc/reference/chttpfile-class.md)
