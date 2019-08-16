---
title: Clase CFtpFileFind
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
ms.openlocfilehash: 2f4a394e29be135cac95edf6f504d8b066f53414
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506245"
---
# <a name="cftpfilefind-class"></a>Clase CFtpFileFind

Ayuda en las búsquedas del archivo de Internet de servidores FTP.

## <a name="syntax"></a>Sintaxis

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|Construye un objeto `CFtpFileFind`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFtpFileFind::FindFile](#findfile)|Busca un archivo en un servidor FTP.|
|[CFtpFileFind::FindNextFile](#findnextfile)|Continúa una búsqueda de archivos de una llamada anterior a [findfile](#findfile).|
|[CFtpFileFind::GetFileURL](#getfileurl)|Obtiene la dirección URL, incluida la ruta de acceso, del archivo encontrado.|

## <a name="remarks"></a>Comentarios

`CFtpFileFind`incluye funciones miembro que inician una búsqueda, localizan un archivo y devuelven la dirección URL u otra información descriptiva sobre el archivo.

Otras clases MFC diseñadas para Internet y el archivo local buscado incluyen [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) y [CFileFind](../../mfc/reference/cfilefind-class.md). Junto con `CFtpFileFind`, estas clases proporcionan un mecanismo sin problemas para que el cliente busque archivos específicos, independientemente del Protocolo de servidor o del tipo de archivo (ya sea un equipo local o un servidor remoto). Tenga en cuenta que no hay ninguna clase MFC para realizar búsquedas en servidores HTTP porque HTTP no admite la manipulación directa de archivos necesaria para las búsquedas.

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

##  <a name="cftpfilefind"></a>  CFtpFileFind::CFtpFileFind

Se llama a esta función miembro para construir `CFtpFileFind` un objeto.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*pConnection*<br/>
Puntero a un objeto `CFtpConnection` . Puede obtener una conexión FTP llamando a [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).

*dwContext*<br/>
Identificador de contexto para el `CFtpFileFind` objeto. Vea la **sección Comentarios** para obtener más información sobre este parámetro.

### <a name="remarks"></a>Comentarios

MFC envía el valor predeterminado de *dwContext* `CFtpFileFind` al objeto desde el objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) que creó el `CFtpFileFind` objeto. Puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo [Internet First Steps: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de la información general de la clase anteriormente en este tema.

##  <a name="findfile"></a>  CFtpFileFind::FindFile

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
Marcas que describen cómo controlar esta sesión. Estas marcas se pueden combinar con el operador OR bit a&#124;bit () y son como se indica a continuación:

- INTERNET_FLAG_RELOAD obtiene los datos de la conexión incluso si se almacenan en caché localmente. Esta es la marca predeterminada.

- INTERNET_FLAG_DONT_CACHE no almacenan en caché los datos, ya sea de forma local o en cualquier puerta de enlace.

- INTERNET_FLAG_RAW_DATA invalida el valor predeterminado para devolver los datos sin procesar (estructuras [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) para FTP).

- INTERNET_FLAG_SECURE protege las transacciones en la conexión con Capa de sockets seguros o PCT. Esta marca solo es aplicable a las solicitudes HTTP.

- INTERNET_FLAG_EXISTING_CONNECT si es posible, vuelva a usar las conexiones existentes con el `FindFile` servidor para las nuevas solicitudes en lugar de crear una nueva sesión para cada solicitud.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Para obtener información de error extendida, llame a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)de Win32.

### <a name="remarks"></a>Comentarios

Después de `FindFile` llamar a para recuperar el primer archivo FTP, puede llamar a [FindNextFile](#findnextfile) para recuperar los archivos FTP posteriores.

### <a name="example"></a>Ejemplo

  Vea el ejemplo anterior de este tema.

##  <a name="findnextfile"></a>  CFtpFileFind::FindNextFile

Llame a esta función miembro para continuar con una búsqueda de archivos iniciada con una llamada a la función miembro [findfile](#findfile) .

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si hay más archivos; cero si el archivo encontrado es el último del directorio o si se produjo un error. Para obtener información de error extendida, llame a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)de Win32. Si el archivo encontrado es el último archivo en el directorio o si no se encuentran archivos coincidentes, la `GetLastError` función devuelve ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Comentarios

Debe llamar a esta función al menos una vez antes de llamar a cualquier función de atributo (vea [CFileFind:: FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).

`FindNextFile`ajusta la función [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew)de Win32.

### <a name="example"></a>Ejemplo

  Vea el ejemplo anterior de este tema.

##  <a name="getfileurl"></a>  CFtpFileFind::GetFileURL

Llame a esta función miembro para obtener la dirección URL del archivo especificado.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Valor devuelto

El archivo y la ruta de acceso del localizador de recursos universal (URL).

### <a name="remarks"></a>Comentarios

`GetFileURL`es similar a la función miembro [CFileFind:: GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath), salvo que devuelve la dirección URL con el formato `ftp://moose/dir/file.txt`.

## <a name="see-also"></a>Vea también

[CFileFind (clase)](../../mfc/reference/cfilefind-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind (clase)](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile (clase)](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile (clase)](../../mfc/reference/chttpfile-class.md)
