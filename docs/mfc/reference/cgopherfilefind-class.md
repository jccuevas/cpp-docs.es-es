---
title: CGopherFileFind (clase)
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
ms.openlocfilehash: 7a42b99c919abd9098bff1897c4c5febf443314d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373678"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind (clase)

Ayuda en las búsquedas de archivos de Internet de servidores gopher.

> [!NOTE]
> Las `CGopherConnection`clases `CGopherFileFind` `CGopherLocator` , `CGopherFile`, , y sus miembros han quedado en desuso porque no funcionan en la plataforma Windows XP, pero seguirán funcionando en plataformas anteriores.

## <a name="syntax"></a>Sintaxis

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|Construye un objeto `CGopherFileFind`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CGopherFileFind::FindFile](#findfile)|Busca un archivo en un servidor gopher.|
|[CGopherFileFind::FindNextFile](#findnextfile)|Continúa una búsqueda de archivos de una llamada anterior a [FindFile](#findfile).|
|[CGopherFileFind::GetCreationTime](#getcreationtime)|Obtiene la hora en que se creó el archivo especificado.|
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|Obtiene la hora a la que se accedió por última vez al archivo especificado.|
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|Obtiene la hora en la que se escribió por última vez el archivo especificado.|
|[CGopherFileFind::GetLength](#getlength)|Obtiene la longitud del archivo encontrado, en bytes.|
|[CGopherFileFind::GetLocator](#getlocator)|Consigue `CGopherLocator` un objeto.|
|[CGopherFileFind::GetScreenName](#getscreenname)|Obtiene el nombre de una pantalla gopher.|
|[CGopherFileFind::IsDots](#isdots)|Comprueba los marcadores de directorio y directorio principal actuales mientras se recorren en iteración los archivos.|

## <a name="remarks"></a>Observaciones

`CGopherFileFind`incluye funciones miembro que comienzan una búsqueda, localizan un archivo y devuelven la dirección URL de un archivo.

Otras clases MFC diseñadas para Internet y los archivos locales buscados incluyen [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) y [CFileFind](../../mfc/reference/cfilefind-class.md). Junto `CGopherFileFind`con , estas clases proporcionan un mecanismo sin problemas para que el usuario encuentre archivos específicos, independientemente del protocolo de servidor, tipo de archivo o ubicación (ya sea un equipo local o un servidor remoto.) Tenga en cuenta que no hay ninguna clase MFC para buscar en servidores HTTP porque HTTP no admite la manipulación directa de archivos requerida por las búsquedas.

> [!NOTE]
> `CGopherFileFind`no admite las siguientes funciones miembro de su clase base [CFileFind:](../../mfc/reference/cfilefind-class.md)

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

Además, cuando `CGopherFileFind`se `CFileFind` usa con , la función miembro [IsDots](../../mfc/reference/cfilefind-class.md#isdots) siempre es FALSE.

Para obtener más información `CGopherFileFind` sobre cómo usar y las otras clases De WinInet, consulte el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="cgopherfilefindcgopherfilefind"></a><a name="cgopherfilefind"></a>CGopherFileFind::CGopherFileFind

Esta función miembro se `CGopherFileFind` llama para construir un objeto.

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*pConexión*<br/>
Un puntero a un [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objeto.

*dwContext*<br/>
Identificador de contexto para la operación. Consulte **Comentarios** para obtener más información sobre *dwContext*.

### <a name="remarks"></a>Observaciones

MFC envía el `CGopherFileFind` valor predeterminado de *dwContext* al objeto desde el `CGopherFileFind` objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) que creó el objeto. Al construir `CGopherFileFind` un objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve a [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo Primeros pasos de [Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

## <a name="cgopherfilefindfindfile"></a><a name="findfile"></a>CGopherFileFind::FindFile

Llame a esta función miembro para buscar un archivo gopher.

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
Una referencia a un [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto.

*pstrString*<br/>
Puntero a una cadena que contiene el nombre de archivo.

*dwFlags*<br/>
Los indicadores que describen cómo manejar esta sesión. Los indicadores válidos son:

- INTERNET_FLAG_RELOAD Obtener los datos del servidor remoto incluso si se almacenan en caché localmente.

- INTERNET_FLAG_DONT_CACHE No almacene en caché los datos, ya sea localmente o en ninguna puerta de enlace.

- INTERNET_FLAG_SECURE Solicitar transacciones seguras en el cable con Secure Sockets Layer o PCT. Esta marca solo es aplicable a las solicitudes HTTP.

- INTERNET_FLAG_USE_EXISTING Si es posible, reutilice las `FindFile` conexiones existentes al servidor para nuevas solicitudes, en lugar de crear una nueva sesión para cada solicitud.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Para obtener información de error ampliada, llame a la función [GetLastError de](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)Win32 .

### <a name="remarks"></a>Observaciones

Después `FindFile` de llamar para recuperar el primer objeto gopher, puede llamar a [FindNextFile](#findnextfile) para recuperar los archivos gopher posteriores.

## <a name="cgopherfilefindfindnextfile"></a><a name="findnextfile"></a>CGopherFileFind::FindNextFile

Llame a esta función miembro para continuar una búsqueda de archivos iniciada con una llamada a [CGopherFileFind::FindFile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si hay más archivos; cero si el archivo encontrado es el último en el directorio o si se produjo un error. Para obtener información de error ampliada, llame a la función [GetLastError de](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)Win32 . Si el archivo encontrado es el último archivo del directorio, o `GetLastError` si no se encuentra ningún archivo coincidente, la función devuelve ERROR_NO_MORE_FILES.

## <a name="cgopherfilefindgetcreationtime"></a><a name="getcreationtime"></a>CGopherFileFind::GetCreationTime

Obtiene el tiempo de creación del archivo actual.

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

Distinto de cero si se realiza correctamente; 0 si no se realiza correctamente. `GetCreationTime`devuelve 0 solo si nunca se `CGopherFileFind` ha llamado a [FindNextFile](#findnextfile) en este objeto.

### <a name="remarks"></a>Observaciones

Debe llamar a [FindNextFile](#findnextfile) al `GetCreationTime`menos una vez antes de llamar a .

> [!NOTE]
> No todos los sistemas de archivos utilizan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos subyacente o el servidor no admite mantener el atributo time. Consulte la estructura [de WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) para obtener información sobre los formatos de tiempo. En algunos sistemas operativos, la hora devuelta está en la zona horaria local de la máquina donde se encuentra el archivo. Consulte la API [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) de Win32 para obtener más información.

## <a name="cgopherfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a>CGopherFileFind::GetLastAccessTime

Obtiene la hora a la que se accedió por última vez al archivo especificado.

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

Distinto de cero si se realiza correctamente; 0 si no se realiza correctamente. `GetLastAccessTime`devuelve 0 solo si nunca se `CGopherFileFind` ha llamado a [FindNextFile](#findnextfile) en este objeto.

### <a name="remarks"></a>Observaciones

Debe llamar a [FindNextFile](#findnextfile) al `GetLastAccessTime`menos una vez antes de llamar a .

> [!NOTE]
> No todos los sistemas de archivos utilizan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos subyacente o el servidor no admite mantener el atributo time. Consulte la estructura [de WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) para obtener información sobre los formatos de tiempo. En algunos sistemas operativos, la hora devuelta está en la zona horaria local de la máquina donde se encuentra el archivo. Consulte la API [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) de Win32 para obtener más información.

## <a name="cgopherfilefindgetlastwritetime"></a><a name="getlastwritetime"></a>CGopherFileFind::GetLastWriteTime

Obtiene la última vez que se cambió el archivo.

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

Distinto de cero si se realiza correctamente; 0 si no se realiza correctamente. `GetLastWriteTime`devuelve 0 solo si nunca se `CGopherFileFind` ha llamado a [FindNextFile](#findnextfile) en este objeto.

### <a name="remarks"></a>Observaciones

Debe llamar a [FindNextFile](#findnextfile) al `GetLastWriteTime`menos una vez antes de llamar a .

> [!NOTE]
> No todos los sistemas de archivos utilizan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos subyacente o el servidor no admite mantener el atributo time. Consulte la estructura [de WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) para obtener información sobre los formatos de tiempo. En algunos sistemas operativos, la hora devuelta está en la zona horaria local de la máquina donde se encuentra el archivo. Consulte la API [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) de Win32 para obtener más información.

## <a name="cgopherfilefindgetlength"></a><a name="getlength"></a>CGopherFileFind::GetLength

Llame a esta función miembro para obtener la longitud, en bytes, del archivo encontrado.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud, en bytes, del archivo encontrado.

### <a name="remarks"></a>Observaciones

`GetLength`utiliza la estructura Win32 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) para obtener el valor del tamaño del archivo en bytes.

> [!NOTE]
> A partir de MFC `GetLength` 7.0, admite tipos enteros de 64 bits. El código existente anteriormente creado con esta versión más reciente de la biblioteca puede dar lugar a advertencias de truncamiento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) (la implementación de la clase base).

## <a name="cgopherfilefindgetlocator"></a><a name="getlocator"></a>CGopherFileFind::GetLocator

Llame a esta función miembro para obtener el [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto que [FindFile](#findfile) utiliza para buscar el archivo gopher.

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto `CGopherLocator` .

## <a name="cgopherfilefindgetscreenname"></a><a name="getscreenname"></a>CGopherFileFind::GetScreenName

Llame a esta función miembro para obtener el nombre de la pantalla gopher.

```
CString GetScreenName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre de la pantalla gopher.

## <a name="cgopherfilefindisdots"></a><a name="isdots"></a>CGopherFileFind::IsDots

Comprueba los marcadores de directorio y directorio principal actuales mientras se recorren en iteración los archivos.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo encontrado tiene el nombre "." o "..", lo que indica que el archivo encontrado es realmente un directorio. De lo contrario 0.

### <a name="remarks"></a>Observaciones

Debe llamar a [FindNextFile](#findnextfile) al `IsDots`menos una vez antes de llamar a .

## <a name="see-also"></a>Consulte también

[Clase CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind (clase)](../../mfc/reference/cftpfilefind-class.md)<br/>
[Clase CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Clase CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Clase CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Clase CHttpFile](../../mfc/reference/chttpfile-class.md)
