---
title: CFtpFileFind (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: cf4afb4a683c2d0cf5f2977107d02ee300a53cb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373751"
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

|Nombre|Descripción|
|----------|-----------------|
|[CFtpFileFind::FindFile](#findfile)|Busca un archivo en un servidor FTP.|
|[CFtpFileFind::FindNextFile](#findnextfile)|Continúa una búsqueda de archivos de una llamada anterior a [FindFile](#findfile).|
|[CFtpFileFind::GetFileURL](#getfileurl)|Obtiene la dirección URL, incluida la ruta de acceso, del archivo encontrado.|

## <a name="remarks"></a>Observaciones

`CFtpFileFind`incluye funciones miembro que comienzan una búsqueda, localizan un archivo y devuelven la dirección URL u otra información descriptiva sobre el archivo.

Otras clases MFC diseñadas para Internet y los archivos locales buscados incluyen [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) y [CFileFind](../../mfc/reference/cfilefind-class.md). Junto `CFtpFileFind`con , estas clases proporcionan un mecanismo sin problemas para que el cliente encuentre archivos específicos, independientemente del protocolo de servidor o el tipo de archivo (ya sea un equipo local o un servidor remoto). Tenga en cuenta que no hay ninguna clase MFC para buscar en servidores HTTP porque HTTP no admite la manipulación directa de archivos necesaria para las búsquedas.

Para obtener más información `CFtpFileFind` sobre cómo usar y las otras clases De WinInet, consulte el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="example"></a>Ejemplo

El código siguiente muestra cómo enumerar todos los archivos en el directorio actual del servidor FTP.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="cftpfilefindcftpfilefind"></a><a name="cftpfilefind"></a>CFtpFileFind::CFtpFileFind

Esta función miembro se `CFtpFileFind` llama para construir un objeto.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*pConexión*<br/>
Puntero a un objeto `CFtpConnection` . Puede obtener una conexión FTP llamando a [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).

*dwContext*<br/>
Identificador de contexto `CFtpFileFind` para el objeto. Consulte **Comentarios** para obtener más información sobre este parámetro.

### <a name="remarks"></a>Observaciones

MFC envía el `CFtpFileFind` valor predeterminado de *dwContext* al objeto desde el `CFtpFileFind` objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) que creó el objeto. Puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve a [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo Primeros pasos de [Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

### <a name="example"></a>Ejemplo

  Vea el ejemplo en la información general de la clase anterioren este tema.

## <a name="cftpfilefindfindfile"></a><a name="findfile"></a>CFtpFileFind::FindFile

Llame a esta función miembro para buscar un archivo FTP.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Parámetros

*pstrName*<br/>
Puntero a una cadena que contiene el nombre del archivo que se va a buscar. Si NULL, la llamada realizará una búsqueda con caracteres comodín (*).

*dwFlags*<br/>
Los indicadores que describen cómo manejar esta sesión. Estos indicadores se pueden combinar con el operador OR bit a bit (&#124;) y son los siguientes:

- INTERNET_FLAG_RELOAD Obtener los datos de la conexión incluso si se almacena localmente en caché. Esta es la marca predeterminada.

- INTERNET_FLAG_DONT_CACHE No almacene en caché los datos, ya sea localmente o en ninguna puerta de enlace.

- INTERNET_FLAG_RAW_DATA Invalidar el valor predeterminado para devolver los datos sin [procesar (estructuras WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) para FTP).

- INTERNET_FLAG_SECURE Protege las transacciones en el cable con Secure Sockets Layer o PCT. Esta marca solo es aplicable a las solicitudes HTTP.

- INTERNET_FLAG_EXISTING_CONNECT Si es posible, reutilice las `FindFile` conexiones existentes al servidor para nuevas solicitudes en lugar de crear una nueva sesión para cada solicitud.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Para obtener información de error ampliada, llame a la función [GetLastError de](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)Win32 .

### <a name="remarks"></a>Observaciones

Después `FindFile` de llamar para recuperar el primer archivo FTP, puede llamar a [FindNextFile](#findnextfile) para recuperar los archivos FTP posteriores.

### <a name="example"></a>Ejemplo

  Vea el ejemplo anterior de este tema.

## <a name="cftpfilefindfindnextfile"></a><a name="findnextfile"></a>CFtpFileFind::FindNextFile

Llame a esta función miembro para continuar una búsqueda de archivos iniciada con una llamada a la [FindFile](#findfile) función miembro.

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si hay más archivos; cero si el archivo encontrado es el último en el directorio o si se produjo un error. Para obtener información de error ampliada, llame a la función [GetLastError de](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)Win32 . Si el archivo encontrado es el último archivo del directorio, o `GetLastError` si no se encuentra ningún archivo coincidente, la función devuelve ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Observaciones

Debe llamar a esta función al menos una vez antes de llamar a cualquier función de atributo (consulte [CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).

`FindNextFile`ajusta la función Debúsqueda de Win32 [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew).

### <a name="example"></a>Ejemplo

  Vea el ejemplo anterior en este tema.

## <a name="cftpfilefindgetfileurl"></a><a name="getfileurl"></a>CFtpFileFind::GetFileURL

Llame a esta función miembro para obtener la dirección URL del archivo especificado.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Valor devuelto

El archivo y la ruta de acceso del Localizador universal de recursos (URL).

### <a name="remarks"></a>Observaciones

`GetFileURL`es similar a la función miembro [CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath), `ftp://moose/dir/file.txt`excepto que devuelve la dirección URL en el formulario .

## <a name="see-also"></a>Consulte también

[Clase CFileFind](../../mfc/reference/cfilefind-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind (clase)](../../mfc/reference/cgopherfilefind-class.md)<br/>
[Clase CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Clase CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[Clase CHttpFile](../../mfc/reference/chttpfile-class.md)
