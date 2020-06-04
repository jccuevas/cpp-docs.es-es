---
title: Clase CHttpFile
ms.date: 11/04/2016
f1_keywords:
- CHttpFile
- AFXINET/CHttpFile
- AFXINET/CHttpFile::CHttpFile
- AFXINET/CHttpFile::AddRequestHeaders
- AFXINET/CHttpFile::EndRequest
- AFXINET/CHttpFile::GetFileURL
- AFXINET/CHttpFile::GetObject
- AFXINET/CHttpFile::GetVerb
- AFXINET/CHttpFile::QueryInfo
- AFXINET/CHttpFile::QueryInfoStatusCode
- AFXINET/CHttpFile::SendRequest
- AFXINET/CHttpFile::SendRequestEx
helpviewer_keywords:
- CHttpFile [MFC], CHttpFile
- CHttpFile [MFC], AddRequestHeaders
- CHttpFile [MFC], EndRequest
- CHttpFile [MFC], GetFileURL
- CHttpFile [MFC], GetObject
- CHttpFile [MFC], GetVerb
- CHttpFile [MFC], QueryInfo
- CHttpFile [MFC], QueryInfoStatusCode
- CHttpFile [MFC], SendRequest
- CHttpFile [MFC], SendRequestEx
ms.assetid: 399e7c68-bbce-4374-8c55-206e9c7baac6
ms.openlocfilehash: cba3ba7d86577703de2bf5709d66bbd5e0298863
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368394"
---
# <a name="chttpfile-class"></a>Clase CHttpFile

Proporciona la funcionalidad para solicitar y leer archivos en un servidor HTTP.

## <a name="syntax"></a>Sintaxis

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CHttpFile::CHttpFile](#chttpfile)|Crea un objeto `CHttpFile` .|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|Agrega encabezados a la solicitud enviada a un servidor HTTP.|
|[CHttpFile::EndRequest](#endrequest)|Finaliza una solicitud enviada a un servidor HTTP con la función miembro [SendRequestEx.](#sendrequestex)|
|[CHttpFile::GetFileURL](#getfileurl)|Obtiene la dirección URL del archivo especificado.|
|[CHttpFile::GetObject](#getobject)|Obtiene el objeto de destino del verbo de una solicitud a un servidor HTTP.|
|[CHttpFile::GetVerb](#getverb)|Obtiene el verbo que se usó en una solicitud a un servidor HTTP.|
|[CHttpFile::QueryInfo](#queryinfo)|Devuelve los encabezados de respuesta o solicitud del servidor HTTP.|
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|Recupera el código de estado asociado a una `dwStatusCode` solicitud HTTP y lo coloca en el parámetro proporcionado.|
|[CHttpFile::SendRequest](#sendrequest)|Envía una solicitud a un servidor HTTP.|
|[CHttpFile::SendRequestEx](#sendrequestex)|Envía una solicitud a un servidor HTTP mediante `CInternetFile`los métodos [Write](../../mfc/reference/cinternetfile-class.md#write) o [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) de .|

## <a name="remarks"></a>Observaciones

Si la sesión de Internet lee datos de un `CHttpFile`servidor HTTP, debe crear una instancia de .

Para obtener más `CHttpFile` información sobre cómo funciona con las otras clases de Internet MFC, vea el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="chttpfileaddrequestheaders"></a><a name="addrequestheaders"></a>CHttpFile::AddRequestHeaders

Llame a esta función miembro para agregar uno o más encabezados de solicitud HTTP al identificador de solicitud HTTP.

```
BOOL AddRequestHeaders(
    LPCTSTR pstrHeaders,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW,
    int dwHeadersLen = -1);

BOOL AddRequestHeaders(
    CString& str,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW);
```

### <a name="parameters"></a>Parámetros

*pstrHeaders*<br/>
Puntero a una cadena que contiene el encabezado o encabezados que se anexan a la solicitud. Cada encabezado debe ser terminado por un par CR/LF.

*dwFlags*<br/>
Modifica la semántica de los nuevos encabezados. Puede ser uno de los siguientes:

- HTTP_ADDREQ_FLAG_COALESCE Combina encabezados del mismo nombre, utilizando la marca para agregar el primer encabezado encontrado al encabezado siguiente. Por ejemplo, "Aceptar:\*texto/ " seguido\*de "Aceptar: audio/ " da como\*resultado\*la formación del encabezado único "Aceptar: texto / , audio / ". Corresponde a la aplicación que realiza la llamada garantizar un esquema cohesivo con respecto a los datos recibidos por las solicitudes enviadas con encabezados combinados o independientes.

- HTTP_ADDREQ_FLAG_REPLACE Realiza una eliminación y agregar para reemplazar el encabezado actual. El nombre del encabezado se usará para quitar el encabezado actual y se usará el valor completo para agregar el nuevo encabezado. Si el valor-encabezado está vacío y se encuentra el encabezado, se quita. Si no está vacío, se reemplaza el valor de encabezado.

- HTTP_ADDREQ_FLAG_ADD_IF_NEW Solo agrega el encabezado si aún no existe. Si existe, se devuelve un error.

- HTTP_ADDREQ_FLAG_ADD Se utiliza con REPLACE. Agrega el encabezado si no existe.

*dwHeadersLen*<br/>
La longitud, en caracteres, de *pstrHeaders*. Si se trata de -1L, se supone que *pstrHeaders* es de terminada cero y se calcula la longitud.

*Str*<br/>
Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el encabezado de solicitud o encabezados que se van a agregar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

### <a name="remarks"></a>Observaciones

`AddRequestHeaders`anexa encabezados adicionales de formato libre al identificador de solicitud HTTP. Está diseñado para ser utilizado por clientes sofisticados que necesitan un control detallado sobre la solicitud exacta enviada al servidor HTTP.

> [!NOTE]
> La aplicación puede pasar varios encabezados en *pstrHeaders* o *str* para una `AddRequestHeaders` llamada mediante HTTP_ADDREQ_FLAG_ADD o HTTP_ADDREQ_FLAG_ADD_IF_NEW. Si la aplicación intenta quitar o reemplazar un encabezado mediante HTTP_ADDREQ_FLAG_REMOVE o HTTP_ADDREQ_FLAG_REPLACE, solo se puede proporcionar un encabezado en *lpszHeaders*.

## <a name="chttpfilechttpfile"></a><a name="chttpfile"></a>CHttpFile::CHttpFile

Esta función miembro se `CHttpFile` llama para construir un objeto.

```
CHttpFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrObject,
    LPCTSTR pstrServer,
    LPCTSTR pstrVerb,
    DWORD_PTR dwContext);

CHttpFile(
    HINTERNET hFile,
    LPCTSTR pstrVerb,
    LPCTSTR pstrObject,
    CHttpConnection* pConnection);
```

### <a name="parameters"></a>Parámetros

*hArchivo*<br/>
Identificador de un archivo de Internet.

*hSesión*<br/>
Un identificador de una sesión de Internet.

*pstrObject*<br/>
Puntero a una cadena `CHttpFile` que contiene el objeto.

*pstrServer*<br/>
Puntero a una cadena que contiene el nombre del servidor.

*pstrVerb*<br/>
Puntero a una cadena que contiene el método que se usará al enviar la solicitud. Puede ser POST, HEAD o GET.

*dwContext*<br/>
Identificador de contexto `CHttpFile` para el objeto. Consulte **Comentarios** para obtener más información sobre este parámetro.

*pConexión*<br/>
Un puntero a un [CHttpConnection](../../mfc/reference/chttpconnection-class.md) objeto.

### <a name="remarks"></a>Observaciones

Nunca se `CHttpFile` construye un objeto directamente; en lugar de llamar a [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) o [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) en su lugar.

MFC envía `dwContext` el valor predeterminado `CHttpFile` a mfc al objeto desde `CHttpFile` el objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) que creó el objeto. Al llamar `CInternetSession::OpenURL` `CHttpConnection` o construir `CHttpFile` un objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve a [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo Primeros pasos de [Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

## <a name="chttpfileendrequest"></a><a name="endrequest"></a>CHttpFile::EndRequest

Llame a esta función miembro para finalizar una solicitud enviada a un servidor HTTP con el [SendRequestEx](#sendrequestex) función miembro.

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Indicadores que describen la operación. Para obtener una lista de los indicadores adecuados, vea [HttpEndRequest](/windows/win32/api/wininet/nf-wininet-httpendrequestw) en el Windows SDK.

*lpBuffIn*<br/>
Puntero a un [INTERNET_BUFFERS](/windows/win32/api/wininet/ns-wininet-internet_buffersw) inicializado que describe el búfer de entrada utilizado para la operación.

*dwContext*<br/>
Identificador de contexto para la operación `CHttpFile`. Consulte Comentarios para obtener más información sobre este parámetro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, determine la causa del error examinando el objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) producido.

### <a name="remarks"></a>Observaciones

MFC envía el `CHttpFile` valor predeterminado de *dwContext* al objeto desde el `CHttpFile` objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) que creó el objeto. Cuando se llama a [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) o `CHttpFile` [CHttpConnection](../../mfc/reference/chttpconnection-class.md) para construir un objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve a [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo Primeros pasos de [Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

## <a name="chttpfilegetfileurl"></a><a name="getfileurl"></a>CHttpFile::GetFileURL

Llame a esta función miembro para obtener el nombre del archivo HTTP como una dirección URL.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene una dirección URL que hace referencia al recurso asociado a este archivo.

### <a name="remarks"></a>Observaciones

Utilice esta función miembro solo después de `CHttpFile` una llamada correcta a [SendRequest](#sendrequest) o en un objeto creado correctamente por [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

## <a name="chttpfilegetobject"></a><a name="getobject"></a>CHttpFile::GetObject

Llame a esta función miembro para obtener `CHttpFile`el nombre del objeto asociado a este .

```
CString GetObject() const;
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el nombre del objeto.

### <a name="remarks"></a>Observaciones

Utilice esta función miembro solo después de `CHttpFile` una llamada correcta a [SendRequest](#sendrequest) o en un objeto creado correctamente por [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

## <a name="chttpfilegetverb"></a><a name="getverb"></a>CHttpFile::GetVerb

Llame a esta función miembro para obtener el `CHttpFile`verbo HTTP (o método) asociado a esto .

```
CString GetVerb() const;
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el nombre del verbo HTTP (o método).

### <a name="remarks"></a>Observaciones

Utilice esta función miembro solo después de `CHttpFile` una llamada correcta a [SendRequest](#sendrequest) o en un objeto creado correctamente por [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

## <a name="chttpfilequeryinfo"></a><a name="queryinfo"></a>CHttpFile::QueryInfo

Llame a esta función miembro para devolver encabezados de respuesta o solicitud de una solicitud HTTP.

```
BOOL QueryInfo(
    DWORD dwInfoLevel,
    LPVOID lpvBuffer,
    LPDWORD lpdwBufferLength,
    LPDWORD lpdwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    CString& str,
    LPDWORD dwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    SYSTEMTIME* pSysTime,
    LPDWORD dwIndex = NULL) const;
```

### <a name="parameters"></a>Parámetros

*dwInfoLevel*<br/>
Una combinación del atributo que se ha de consultar y los siguientes indicadores que especifican el tipo de información solicitada:

- HTTP_QUERY_CUSTOM Encuentra el nombre del encabezado y devuelve este valor en *lpvBuffer* en la salida. HTTP_QUERY_CUSTOM produce una aserción si no se encuentra el encabezado.

- HTTP_QUERY_FLAG_REQUEST_HEADERS normalmente, la aplicación consulta los encabezados de respuesta, pero una aplicación también puede consultar encabezados de solicitud mediante esta marca.

- HTTP_QUERY_FLAG_SYSTEMTIME Para aquellos encabezados cuyo valor es una cadena de fecha y hora, como "Last-Modified-Time", este indicador devuelve el valor de encabezado como una estructura estándar de Win32 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que no requiere que la aplicación analice los datos. Si utiliza esta marca, es posible `SYSTEMTIME` que desee utilizar la invalidación de la función.

- HTTP_QUERY_FLAG_NUMBER Para aquellos encabezados cuyo valor es un número, como el código de estado, esta marca devuelve los datos como un número de 32 bits.

Consulte la sección **Comentarios** para obtener una lista de los valores posibles.

*lpvBuffer*<br/>
Puntero al búfer que recibe la información.

*lpdwBufferLength*<br/>
En la entrada, esto apunta a un valor que contiene la longitud del búfer de datos, en número de caracteres o bytes. Consulte la sección **Comentarios** para obtener información más detallada sobre este parámetro.

*lpdwIndex*<br/>
Puntero a un índice de encabezado de base cero. Puede ser NULL. Utilice esta marca para enumerar varios encabezados con el mismo nombre. En la entrada, *lpdwIndex* indica el índice del encabezado especificado que se va a devolver. En la salida, *lpdwIndex* indica el índice del encabezado siguiente. Si no se encuentra el siguiente índice, se devuelve ERROR_HTTP_HEADER_NOT_FOUND.

*Str*<br/>
Una referencia a la [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que recibe la información devuelta.

*dwIndex*<br/>
Un valor de índice. Consulte *lpdwIndex*.

*pSysTime*<br/>
Puntero a una estructura [SystemTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) de Win32.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

### <a name="remarks"></a>Observaciones

Utilice esta función miembro solo después de `CHttpFile` una llamada correcta a [SendRequest](#sendrequest) o en un objeto creado correctamente por [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Puede recuperar los siguientes tipos `QueryInfo`de datos de:

- cadenas (predeterminado)

- `SYSTEMTIME`(para "Datos:" "Caduca:" etc., encabezados)

- DWORD (para STATUS_CODE, CONTENT_LENGTH, etc.)

Cuando se escribe una cadena en el búfer `lpdwBufferLength` y la función miembro se realiza correctamente, contiene la longitud de la cadena en caracteres menos 1 para el carácter NULL de terminación.

Los posibles valores *dwInfoLevel* incluyen:

- HTTP_QUERY_MIME_VERSION

- HTTP_QUERY_CONTENT_TYPE

- HTTP_QUERY_CONTENT_TRANSFER_ENCODING

- HTTP_QUERY_CONTENT_ID

- HTTP_QUERY_CONTENT_DESCRIPTION

- HTTP_QUERY_CONTENT_LENGTH

- HTTP_QUERY_ALLOWED_METHODS

- HTTP_QUERY_PUBLIC_METHODS

- HTTP_QUERY_DATE

- HTTP_QUERY_EXPIRES

- HTTP_QUERY_LAST_MODIFIED

- HTTP_QUERY_MESSAGE_ID

- HTTP_QUERY_URI

- HTTP_QUERY_DERIVED_FROM

- HTTP_QUERY_LANGUAGE

- HTTP_QUERY_COST

- HTTP_QUERY_WWW_LINK

- HTTP_QUERY_PRAGMA

- HTTP_QUERY_VERSION

- HTTP_QUERY_STATUS_CODE

- HTTP_QUERY_STATUS_TEXT

- HTTP_QUERY_RAW_HEADERS

- HTTP_QUERY_RAW_HEADERS_CRLF

## <a name="chttpfilequeryinfostatuscode"></a><a name="queryinfostatuscode"></a>CHttpFile::QueryInfoStatusCode

Llame a esta función miembro para obtener el código de estado asociado a una solicitud HTTP y colóquelo en el parámetro *dwStatusCode* proporcionado.

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>Parámetros

*dwStatusCode*<br/>
Una referencia a un código de estado. Los códigos de estado indican el éxito o el error del evento solicitado. Consulte **Comentarios** para obtener una selección de descripciones de código sdecuentato.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

### <a name="remarks"></a>Observaciones

Utilice esta función miembro solo después de `CHttpFile` una llamada correcta a [SendRequest](#sendrequest) o en un objeto creado correctamente por [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Los códigos de estado HTTP se dividen en grupos que indican el éxito o el error de la solicitud. En las tablas siguientes se describen los grupos de códigos de estado y los códigos de estado HTTP más comunes.

|Grupo|Significado|
|-----------|-------------|
|200 a 299|Correcto|
|300 a 399|Information|
|400-499|Error de solicitud|
|500-599|Error del servidor|

Códigos de estado HTTP comunes:

|status code|Significado|
|-----------------|-------------|
|200|URL local, la transmisión sigue|
|400|Solicitud ininteligible|
|404|URL solicitada no encontrada|
|405|El servidor no admite el método solicitado|
|500|Error de servidor desconocido|
|503|Capacidad del servidor alcanzada|

## <a name="chttpfilesendrequest"></a><a name="sendrequest"></a>CHttpFile::SendRequest

Llame a esta función miembro para enviar una solicitud a un servidor HTTP.

```
BOOL SendRequest(
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLen = 0,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);

BOOL SendRequest(
    CString& strHeaders,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);
```

### <a name="parameters"></a>Parámetros

*pstrHeaders*<br/>
Puntero a una cadena que contiene el nombre de los encabezados que se va a enviar.

*dwHeadersLen*<br/>
La longitud de los encabezados identificados por *pstrHeaders*.

*lpOpcional*<br/>
Cualquier dato opcional que se envíe inmediatamente después de los encabezados de solicitud. Esto se utiliza generalmente para las operaciones POST y PUT. Esto puede ser NULL si no hay datos opcionales para enviar.

*dwOptionalLen*<br/>
La longitud de *lpOptional*.

*strHeaders*<br/>
Cadena que contiene el nombre de los encabezados de la solicitud que se envía.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, determine la causa del error examinando el objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) producido.

## <a name="chttpfilesendrequestex"></a><a name="sendrequestex"></a>CHttpFile::SendRequestEx

Llame a esta función miembro para enviar una solicitud a un servidor HTTP.

```
BOOL SendRequestEx(
    DWORD dwTotalLen,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);

BOOL SendRequestEx(
    LPINTERNET_BUFFERS lpBuffIn,
    LPINTERNET_BUFFERS lpBuffOut,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*dwTotalLen*<br/>
Número de bytes que se enviarán en la solicitud.

*dwFlags*<br/>
Indicadores que describen la operación. Para obtener una lista de indicadores adecuados, vea [HttpSendRequestEx](/windows/win32/api/wininet/nf-wininet-httpsendrequestexw) en el Windows SDK.

*dwContext*<br/>
Identificador de contexto para la operación `CHttpFile`. Consulte Comentarios para obtener más información sobre este parámetro.

*lpBuffIn*<br/>
Puntero a un [INTERNET_BUFFERS](/windows/win32/api/wininet/ns-wininet-internet_buffersw) inicializado que describe el búfer de entrada utilizado para la operación.

*lpBuffOut*<br/>
Puntero a un INTERNET_BUFFERS inicializado que describe el búfer de salida utilizado para la operación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente. Si se produce un error en la llamada, determine la causa del error examinando el objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) producido.

### <a name="remarks"></a>Observaciones

Esta función permite a la aplicación enviar datos `CInternetFile`mediante los métodos [Write](../../mfc/reference/cinternetfile-class.md#write) y [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) de . Debe conocer la longitud de los datos que se enviarán antes de llamar a cualquiera de las invalidaciones de esta función. La primera invalidación le permite especificar la longitud de los datos que desea enviar. La segunda invalidación acepta punteros a estructuras INTERNET_BUFFERS, que se pueden utilizar para describir el búfer con gran detalle.

Después de escribir el contenido en el archivo, llame a [EndRequest](#endrequest) para finalizar la operación.

MFC envía el `CHttpFile` valor predeterminado de *dwContext* al objeto desde el `CHttpFile` objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) que creó el objeto. Cuando se llama a [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) o `CHttpFile` [CHttpConnection](../../mfc/reference/chttpconnection-class.md) para construir un objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve a [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo Primeros pasos de [Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

### <a name="example"></a>Ejemplo

Este fragmento de código envía el contenido de una cadena a un archivo DLL denominado MFCISAPI. DLL en el servidor LOCALHOST. Aunque este ejemplo utiliza `WriteString`solo una llamada a , el uso de varias llamadas para enviar datos en bloques es aceptable.

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>Consulte también

[Clase CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Clase CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpConnection (clase)](../../mfc/reference/chttpconnection-class.md)
