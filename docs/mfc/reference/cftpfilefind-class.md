---
title: CFtpFileFind (clase)
ms.date: 05/28/2020
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
helpviewer_keywords:
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
ms.openlocfilehash: e53e16f738f0436cbd02074c10ca24dbcc9d0fd8
ms.sourcegitcommit: 426e327c9f7c3a3b02300e3f924f9786d62958e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "84206237"
---
# <a name="cftpfilefind-class"></a>CFtpFileFind (clase)

Ayuda en las búsquedas del archivo de Internet de servidores FTP.

## <a name="syntax"></a>Sintaxis

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|Construye un objeto `CFtpFileFind`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|Descripción|
|----------|-----------------|
|[CFtpFileFind:: FindFile](#findfile)|Busca un archivo en un servidor FTP.|
|[CFtpFileFind:: FindNextFile](#findnextfile)|Continúa una búsqueda de archivos de una llamada anterior a [findfile](#findfile).|
|[CFtpFileFind::GetFileURL](#getfileurl)|Obtiene la dirección URL, incluida la ruta de acceso, del archivo encontrado.|

## <a name="remarks"></a>Comentarios

`CFtpFileFind`incluye funciones miembro que inician una búsqueda, localizan un archivo y devuelven la dirección URL u otra información descriptiva sobre el archivo.

Otras clases MFC diseñadas para Internet y el archivo local buscado incluyen [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) y [CFileFind](../../mfc/reference/cfilefind-class.md). Junto con `CFtpFileFind` , estas clases proporcionan un mecanismo sin problemas para que el cliente busque archivos específicos, independientemente del Protocolo de servidor o del tipo de archivo (ya sea un equipo local o un servidor remoto). No hay ninguna clase MFC para realizar búsquedas en servidores HTTP porque HTTP no admite la manipulación directa de archivos necesaria para las búsquedas.

Para obtener más información sobre cómo usar `CFtpFileFind` y las demás clases WinInet, vea el artículo [programación en Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="example"></a>Ejemplo

En el código siguiente se muestra cómo enumerar todos los archivos del directorio actual del servidor FTP.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet. h

## <a name="cftpfilefindcftpfilefind"></a><a name="cftpfilefind"></a>CFtpFileFind::CFtpFileFind

Se llama a esta función miembro para construir un `CFtpFileFind` objeto.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*pConnection*<br/>
Puntero a un objeto `CFtpConnection` . Puede obtener una conexión FTP llamando a [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).

*dwContext*<br/>
Identificador de contexto para el `CFtpFileFind` objeto. Para obtener más información, vea los **comentarios**siguientes.

### <a name="remarks"></a>Comentarios

MFC envía el valor predeterminado de *dwContext* al `CFtpFileFind` objeto desde el objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) que creó el `CFtpFileFind` objeto. Puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Vea el artículo [Internet First Steps: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de la información general de la clase anteriormente en este tema.

## <a name="cftpfilefindfindfile"></a><a name="findfile"></a>CFtpFileFind:: FindFile

Llame a esta función miembro para buscar un archivo FTP.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Parámetros

*pstrName*<br/>
Puntero a una cadena que contiene el nombre del archivo que se va a buscar. Si es NULL, la llamada llevará a cabo una búsqueda con caracteres comodín (*).

*dwFlags*<br/>
Marcas que describen cómo controlar esta sesión. Estas marcas se pueden combinar con el operador OR bit a bit (&#124;) y son como se indica a continuación:

- `INTERNET_FLAG_RELOAD`Obtenga los datos de la conexión incluso si se almacenan en caché localmente. Esta es la marca predeterminada.

- `INTERNET_FLAG_DONT_CACHE`No almacene en caché los datos, ya sea de forma local o en cualquier puerta de enlace.

- `INTERNET_FLAG_RAW_DATA`Reemplace el valor predeterminado para devolver los datos sin procesar ( [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) estructuras para FTP).

- `INTERNET_FLAG_SECURE`Protege las transacciones en la conexión con Capa de sockets seguros o PCT. Esta marca solo se aplica a las solicitudes HTTP.

- `INTERNET_FLAG_EXISTING_CONNECT`Si es posible, reutilice las conexiones existentes al servidor para `FindFile` las nuevas solicitudes en lugar de crear una nueva sesión para cada solicitud.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Para obtener información de error extendida, llame a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)de Win32.

### <a name="remarks"></a>Comentarios

Después de llamar `FindFile` a para recuperar el primer archivo FTP, puede llamar a [FindNextFile](#findnextfile) para recuperar los archivos FTP posteriores.

### <a name="example"></a>Ejemplo

  Vea el ejemplo anterior de este tema.

## <a name="cftpfilefindfindnextfile"></a><a name="findnextfile"></a>CFtpFileFind:: FindNextFile

Llame a esta función miembro para continuar con una búsqueda de archivos iniciada con una llamada a la función miembro [findfile](#findfile) .

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si hay más archivos; cero si el archivo encontrado es el último del directorio o si se produjo un error. Para obtener información de error extendida, llame a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)de Win32. Si el archivo encontrado es el último archivo en el directorio, o si no se encuentran archivos coincidentes, la `GetLastError` función devuelve ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Comentarios

Debe llamar a esta función al menos una vez antes de llamar a cualquier función de atributo (vea [CFileFind:: FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).

`FindNextFile`ajusta la función [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew)de Win32.

### <a name="example"></a>Ejemplo

  Vea el ejemplo anterior de este tema.

## <a name="cftpfilefindgetfileurl"></a><a name="getfileurl"></a>CFtpFileFind::GetFileURL

Llame a esta función miembro para obtener la dirección URL del archivo especificado.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Valor devuelto

El archivo y la ruta de acceso del localizador de recursos universal (URL).

### <a name="remarks"></a>Comentarios

`GetFileURL`es similar a la función miembro [CFileFind:: GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath) , salvo que proporciona el resultado en formato de dirección URL. Como con `CFileFind::GetFilePath` , el resultado no incluye el nombre de archivo. Por ejemplo, se `file1.txt` encuentra en `//moose/dir/file1.txt:` devuelve `ftp://moose/dir/` .

## <a name="see-also"></a>Vea también

[Clase CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind (clase)](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)<br/>
[Clase CGopherFile (](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile (clase)](../../mfc/reference/chttpfile-class.md)
