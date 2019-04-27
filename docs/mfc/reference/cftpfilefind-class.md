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
ms.openlocfilehash: 5da739cac1ab852ce64526b24ee2b4f66d40d570
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182139"
---
# <a name="cftpfilefind-class"></a>CFtpFileFind (clase)

Ayuda en las búsquedas del archivo de Internet de servidores FTP.

## <a name="syntax"></a>Sintaxis

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|Construye un objeto `CFtpFileFind`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CFtpFileFind::FindFile](#findfile)|Busca un archivo en un servidor FTP.|
|[CFtpFileFind::FindNextFile](#findnextfile)|Continúa la búsqueda de archivos desde una llamada anterior a [FindFile](#findfile).|
|[CFtpFileFind::GetFileURL](#getfileurl)|Obtiene la dirección URL, incluida la ruta de acceso del archivo se encuentra.|

## <a name="remarks"></a>Comentarios

`CFtpFileFind` incluye funciones de miembro que iniciar una búsqueda, busque un archivo y devuelvan la dirección URL o demás información descriptiva acerca del archivo.

Otras clases MFC, diseñados para Internet y el archivo local que se buscan incluyen [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) y [CFileFind](../../mfc/reference/cfilefind-class.md). Junto con `CFtpFileFind`, estas clases proporcionan un mecanismo de conexión directo para el cliente buscar archivos específicos, independientemente del servidor de protocolo o tipo de archivo (un equipo local o un servidor remoto). Tenga en cuenta que no hay ninguna clase MFC para las búsquedas en los servidores HTTP porque HTTP no admite la manipulación directa de archivos necesaria para realizar búsquedas.

Para obtener más información sobre cómo usar `CFtpFileFind` y las otras clases WinInet, vea el artículo [Internet programar con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="example"></a>Ejemplo

El código siguiente muestra cómo enumerar todos los archivos en el directorio actual del servidor FTP.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

##  <a name="cftpfilefind"></a>  CFtpFileFind::CFtpFileFind

Se llama a esta función miembro para construir un `CFtpFileFind` objeto.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*pConnection*<br/>
Puntero a un objeto `CFtpConnection` . Puede obtener una conexión FTP mediante una llamada a [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).

*dwContext*<br/>
El identificador de contexto para el `CFtpFileFind` objeto. Consulte **comentarios** para obtener más información acerca de este parámetro.

### <a name="remarks"></a>Comentarios

El valor predeterminado de *dwContext* se envía por MFC para la `CFtpFileFind` objeto desde el [CInternetSession](../../mfc/reference/cinternetsession-class.md) de objeto que creó el `CFtpFileFind` objeto. Puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve al [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo [Internet primeros pasos: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de la información general de la clase anteriormente en este tema.

##  <a name="findfile"></a>  CFtpFileFind::FindFile

Llame a esta función miembro para encontrar un archivo de FTP.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Parámetros

*pstrName*<br/>
Un puntero a una cadena que contiene el nombre del archivo que se va a buscar. Si es NULL, la llamada llevará a cabo una búsqueda con caracteres comodín (*).

*dwFlags*<br/>
Las marcas que describen cómo controlar esta sesión. Estas marcas se pueden combinar con el operador OR bit a bit (&#124;) y son los siguientes:

- INTERNET_FLAG_RELOAD obtener los datos de la conexión incluso si localmente se almacena en caché. Se trata de la marca predeterminada.

- INTERNET_FLAG_DONT_CACHE no almacenar en caché los datos, ya sea localmente o en las puertas de enlace.

- INTERNET_FLAG_RAW_DATA invalidar el valor predeterminado para devolver los datos sin procesar ( [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) estructuras para FTP).

- INTERNET_FLAG_SECURE protege las transacciones en la conexión con la capa de Sockets seguros o PCT. Esta marca es aplicable a solo las solicitudes HTTP.

- INTERNET_FLAG_EXISTING_CONNECT si es posible, reutilizar las conexiones existentes en el servidor para el nuevo `FindFile` solicitudes en lugar de crear una nueva sesión para cada solicitud.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Para obtener información de error extendida, llame a la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="remarks"></a>Comentarios

Después de llamar a `FindFile` para recuperar el primer archivo FTP, puede llamar a [FindNextFile](#findnextfile) para recuperar los archivos FTP posteriores.

### <a name="example"></a>Ejemplo

  Vea el ejemplo anterior de este tema.

##  <a name="findnextfile"></a>  CFtpFileFind::FindNextFile

Llame a esta función miembro para continuar la búsqueda de archivos iniciada con una llamada a la [FindFile](#findfile) función miembro.

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si no hay más archivos; cero si el archivo que se encuentra es la última de ellas en el directorio o si se produjo un error. Para obtener información de error extendida, llame a la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360). Si el archivo se encuentra es el último archivo en el directorio, o si no hay coincidencia de archivos pueden encontrarse, el `GetLastError` función devuelve ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Comentarios

Debe llamar a esta función al menos una vez antes de llamar a cualquier función de atributo (consulte [CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).

`FindNextFile` ajusta la función de Win32 [FindNextFile](/windows/desktop/api/fileapi/nf-fileapi-findnextfilea).

### <a name="example"></a>Ejemplo

  Vea el ejemplo anterior de este tema.

##  <a name="getfileurl"></a>  CFtpFileFind::GetFileURL

Llame a esta función miembro para obtener la dirección URL del archivo especificado.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Valor devuelto

El archivo y ruta de acceso del localizador de recursos Universal (URL).

### <a name="remarks"></a>Comentarios

`GetFileURL` es similar a la función miembro [CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath), excepto en que devuelve la dirección URL en el formulario `ftp://moose/dir/file.txt`.

## <a name="see-also"></a>Vea también

[CFileFind (clase)](../../mfc/reference/cfilefind-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind (clase)](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile (clase)](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile (clase)](../../mfc/reference/chttpfile-class.md)
