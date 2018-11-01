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
ms.openlocfilehash: 7d5c8ceeaeb87b2e0f099ac027bbacc744598e8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662415"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind (clase)

Ayuda en las búsquedas de archivos de Internet de servidores gopher.

> [!NOTE]
>  Las clases `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` y sus miembros se han quedado en desuso porque no funcionan en la plataforma Windows XP, pero seguirán funcionando en las plataformas anteriores.

## <a name="syntax"></a>Sintaxis

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|Construye un objeto `CGopherFileFind`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CGopherFileFind:: FindFile](#findfile)|Busca un archivo en un servidor gopher.|
|[CGopherFileFind:: FindNextFile](#findnextfile)|Continúa la búsqueda de archivos desde una llamada anterior a [FindFile](#findfile).|
|[CGopherFileFind::GetCreationTime](#getcreationtime)|Obtiene la hora en que se creó el archivo especificado.|
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|Obtiene la hora de que último acceso al archivo especificado.|
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|Obtiene la hora en que se escribió el archivo especificado por última.|
|[CGopherFileFind::GetLength](#getlength)|Obtiene la longitud del archivo se encuentra, en bytes.|
|[CGopherFileFind:: GetLocator](#getlocator)|Obtener un `CGopherLocator` objeto.|
|[CGopherFileFind::GetScreenName](#getscreenname)|Obtiene el nombre de una pantalla de gopher.|
|[CGopherFileFind::IsDots](#isdots)|Comprueba si los marcadores de Active directory y el elemento primario actuales al recorrer en iteración los archivos.|

## <a name="remarks"></a>Comentarios

`CGopherFileFind` incluye funciones de miembro que se inicia la búsqueda, busque un archivo y devuelven la dirección URL de un archivo.

Otras clases MFC, diseñados para Internet y el archivo local que se buscan incluyen [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) y [CFileFind](../../mfc/reference/cfilefind-class.md). Junto con `CGopherFileFind`, estas clases proporcionan un mecanismo de conexión directo para el usuario pueda buscar archivos específicos, con independencia del protocolo de servidor, el tipo de archivo o la ubicación (un equipo local o un servidor remoto.) Tenga en cuenta que no hay ninguna clase MFC para las búsquedas en los servidores HTTP porque HTTP no admite la manipulación de archivos directas requerida por las búsquedas.

> [!NOTE]
> `CGopherFileFind` no admite las siguientes funciones de miembro de su clase base [CFileFind](../../mfc/reference/cfilefind-class.md):

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

Además, cuando se usa con `CGopherFileFind`, `CFileFind` función miembro [IsDots](../../mfc/reference/cfilefind-class.md#isdots) siempre es FALSE.

Para obtener más información sobre cómo usar `CGopherFileFind` y las otras clases WinInet, vea el artículo [Internet programar con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

##  <a name="cgopherfilefind"></a>  CGopherFileFind::CGopherFileFind

Se llama a esta función miembro para construir un `CGopherFileFind` objeto.

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*pConnection*<br/>
Un puntero a un [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objeto.

*dwContext*<br/>
El identificador de contexto para la operación. Consulte **comentarios** para obtener más información acerca de *dwContext*.

### <a name="remarks"></a>Comentarios

El valor predeterminado de *dwContext* se envía por MFC para la `CGopherFileFind` objeto desde el [CInternetSession](../../mfc/reference/cinternetsession-class.md) de objeto que creó el `CGopherFileFind` objeto. Cuando se construye un `CGopherFileFind` de objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve al [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

##  <a name="findfile"></a>  CGopherFileFind:: FindFile

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
Un puntero a una cadena que contiene el nombre de archivo.

*dwFlags*<br/>
Las marcas que describen cómo controlar esta sesión. Las marcas válidas son:

- INTERNET_FLAG_RELOAD obtener los datos del servidor remoto, incluso si localmente se almacena en caché.

- INTERNET_FLAG_DONT_CACHE no almacenar en caché los datos, ya sea localmente o en las puertas de enlace.

- Solicitar INTERNET_FLAG_SECURE transacciones seguras en la conexión con la capa de Sockets seguros o PCT. Esta marca es aplicable a solo las solicitudes HTTP.

- INTERNET_FLAG_USE_EXISTING si es posible, reutilizar las conexiones existentes en el servidor para el nuevo `FindFile` solicitudes, en lugar de crear una nueva sesión para cada solicitud.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Para obtener información de error extendida, llame a la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="remarks"></a>Comentarios

Después de llamar a `FindFile` para recuperar el primer objeto gopher, puede llamar a [FindNextFile](#findnextfile) para recuperar archivos gopher posteriores.

##  <a name="findnextfile"></a>  CGopherFileFind:: FindNextFile

Llame a esta función miembro para continuar la búsqueda de archivos iniciada con una llamada a [CGopherFileFind:: FindFile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si no hay más archivos; cero si el archivo que se encuentra es la última de ellas en el directorio o si se produjo un error. Para obtener información de error extendida, llame a la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360). Si el archivo se encuentra es el último archivo en el directorio, o si no hay coincidencia de archivos pueden encontrarse, el `GetLastError` función devuelve ERROR_NO_MORE_FILES.

##  <a name="getcreationtime"></a>  CGopherFileFind::GetCreationTime

Obtiene la hora de creación para el archivo actual.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parámetros

*pTimeStamp*<br/>
Un puntero a un [FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) estructura que contiene la hora en que se creó el archivo.

*refTime*<br/>
Una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 si no lo consigue. `GetCreationTime` Devuelve 0 si sólo [FindNextFile](#findnextfile) nunca se ha llamado en esto `CGopherFileFind` objeto.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes de llamar a `GetCreationTime`.

> [!NOTE]
>  No todos los sistemas de archivos usan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos subyacente o el servidor no es compatible con mantener el atributo de tiempo. Consulte la [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) estructura para obtener información sobre formatos de hora. En algunos sistemas operativos, la hora devuelta está en el momento en zona local a la máquina se está ubicado el archivo. Consulte Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) API para obtener más información.

##  <a name="getlastaccesstime"></a>  CGopherFileFind::GetLastAccessTime

Obtiene la hora de que último acceso al archivo especificado.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Parámetros

*refTime*<br/>
Una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto.

*pTimeStamp*<br/>
Un puntero a un [FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) estructura que contiene la hora de último acceso al archivo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 si no lo consigue. `GetLastAccessTime` Devuelve 0 si sólo [FindNextFile](#findnextfile) nunca se ha llamado en esto `CGopherFileFind` objeto.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes de llamar a `GetLastAccessTime`.

> [!NOTE]
>  No todos los sistemas de archivos usan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos subyacente o el servidor no es compatible con mantener el atributo de tiempo. Consulte la [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) estructura para obtener información sobre formatos de hora. En algunos sistemas operativos, la hora devuelta está en el momento en zona local a la máquina se está ubicado el archivo. Consulte Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) API para obtener más información.

##  <a name="getlastwritetime"></a>  CGopherFileFind::GetLastWriteTime

Obtiene la última vez que se modificó el archivo.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parámetros

*pTimeStamp*<br/>
Un puntero a un [FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) estructura que contiene la hora en que se escribió por última vez el archivo a.

*refTime*<br/>
Una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; 0 si no lo consigue. `GetLastWriteTime` Devuelve 0 si sólo [FindNextFile](#findnextfile) nunca se ha llamado en esto `CGopherFileFind` objeto.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes de llamar a `GetLastWriteTime`.

> [!NOTE]
>  No todos los sistemas de archivos usan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos subyacente o el servidor no es compatible con mantener el atributo de tiempo. Consulte la [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) estructura para obtener información sobre formatos de hora. En algunos sistemas operativos, la hora devuelta está en el momento en zona local a la máquina se está ubicado el archivo. Consulte Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) API para obtener más información.

##  <a name="getlength"></a>  CGopherFileFind::GetLength

Llame a esta función miembro para obtener la longitud, en bytes, del archivo se encuentra.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud, en bytes, del archivo se encuentra.

### <a name="remarks"></a>Comentarios

`GetLength` utiliza la estructura de Win32 [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) para obtener el valor del tamaño del archivo en bytes.

> [!NOTE]
>  A partir de MFC 7.0, `GetLength` admite tipos de entero de 64 bits. Creadas con esta versión más reciente de la biblioteca de código existentes anteriormente puede producir advertencias de truncamiento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) (la implementación de clase base).

##  <a name="getlocator"></a>  CGopherFileFind:: GetLocator

Llame a esta función miembro para obtener el [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto que [FindFile](#findfile) utiliza para buscar el archivo gopher.

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>Valor devuelto

Un objeto `CGopherLocator`.

##  <a name="getscreenname"></a>  CGopherFileFind::GetScreenName

Llame a esta función miembro para obtener el nombre de la pantalla de gopher.

```
CString GetScreenName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre de la pantalla de gopher.

##  <a name="isdots"></a>  CGopherFileFind::IsDots

Comprueba si los marcadores de Active directory y el elemento primario actuales al recorrer en iteración los archivos.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo se encuentra con el nombre "."o"..", lo que indica que el archivo encontrado es realmente un directorio. En caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes de llamar a `IsDots`.

## <a name="see-also"></a>Vea también

[CFileFind (clase)](../../mfc/reference/cfilefind-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind (clase)](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind (clase)](../../mfc/reference/cfilefind-class.md)<br/>
[CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile (clase)](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile (clase)](../../mfc/reference/chttpfile-class.md)
