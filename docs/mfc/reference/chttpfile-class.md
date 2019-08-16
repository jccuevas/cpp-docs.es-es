---
title: CHttpFile (clase)
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
ms.openlocfilehash: 0c8c401b43361a5e1472e3470f5ea452c91b957f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505960"
---
# <a name="chttpfile-class"></a>CHttpFile (clase)

Proporciona la funcionalidad para solicitar y leer archivos en un servidor HTTP.

## <a name="syntax"></a>Sintaxis

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CHttpFile::CHttpFile](#chttpfile)|Crea un objeto `CHttpFile`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|Agrega encabezados a la solicitud enviada a un servidor HTTP.|
|[CHttpFile::EndRequest](#endrequest)|Finaliza una solicitud enviada a un servidor HTTP con la función miembro [SendRequestEx](#sendrequestex) .|
|[CHttpFile::GetFileURL](#getfileurl)|Obtiene la dirección URL del archivo especificado.|
|[CHttpFile::GetObject](#getobject)|Obtiene el objeto de destino del verbo en una solicitud a un servidor HTTP.|
|[CHttpFile::GetVerb](#getverb)|Obtiene el verbo que se usó en una solicitud a un servidor HTTP.|
|[CHttpFile::QueryInfo](#queryinfo)|Devuelve los encabezados de solicitud o respuesta del servidor HTTP.|
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|Recupera el código de estado asociado a una solicitud HTTP y lo coloca en el parámetro `dwStatusCode` proporcionado.|
|[CHttpFile::SendRequest](#sendrequest)|Envía una solicitud a un servidor HTTP.|
|[CHttpFile::SendRequestEx](#sendrequestex)|Envía una solicitud a un servidor HTTP mediante los métodos [Write](../../mfc/reference/cinternetfile-class.md#write) o [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) de `CInternetFile`.|

## <a name="remarks"></a>Comentarios

Si la sesión de Internet lee datos de un servidor HTTP, debe crear una instancia de `CHttpFile`.

Para obtener más información sobre `CHttpFile` cómo funciona con las otras clases de Internet de MFC, vea el artículo [programación en Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet. h

##  <a name="addrequestheaders"></a>  CHttpFile::AddRequestHeaders

Llame a esta función miembro para agregar uno o más encabezados de solicitud HTTP al identificador de la solicitud HTTP.

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
Puntero a una cadena que contiene el encabezado o los encabezados que se van a anexar a la solicitud. Cada encabezado debe terminar con un par de CR/LF.

*dwFlags*<br/>
Modifica la semántica de los nuevos encabezados. Puede ser uno de los siguientes:

- HTTP_ADDREQ_FLAG_COALESCE combina los encabezados del mismo nombre, mediante la marca para agregar el primer encabezado que se encuentra en el encabezado subsiguiente. Por ejemplo, "Accept: Text/\*" seguido de "Accept: audio/\*" da como resultado la formación del encabezado único "Accept: Text/\*, audio/\*". Depende de la aplicación que realiza la llamada garantizar un esquema coherente con respecto a los datos recibidos por las solicitudes enviadas con encabezados combinados o independientes.

- HTTP_ADDREQ_FLAG_REPLACE realiza una eliminación y agrega para reemplazar el encabezado actual. El nombre del encabezado se usará para quitar el encabezado actual y se usará el valor completo para agregar el nuevo encabezado. Si el encabezado-valor está vacío y se encuentra el encabezado, se quita. Si no está vacío, se reemplaza el valor del encabezado.

- HTTP_ADDREQ_FLAG_ADD_IF_NEW solo agrega el encabezado si aún no existe. Si existe una, se devuelve un error.

- HTTP_ADDREQ_FLAG_ADD se usa con Replace. Agrega el encabezado si no existe.

*dwHeadersLen*<br/>
La longitud, en caracteres, de *pstrHeaders*. Si es-1L, se supone que se termina en cero y se calcula la longitud de *pstrHeaders* .

*str*<br/>
Referencia a un objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el encabezado o encabezados de solicitud que se van a agregar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

### <a name="remarks"></a>Comentarios

`AddRequestHeaders`anexa encabezados adicionales y de formato libre al identificador de la solicitud HTTP. Está pensado para que lo usen clientes sofisticados que necesitan un control detallado sobre la solicitud exacta enviada al servidor HTTP.

> [!NOTE]
>  La aplicación puede pasar varios encabezados en *pstrHeaders* o *Str* para una `AddRequestHeaders` llamada mediante HTTP_ADDREQ_FLAG_ADD o HTTP_ADDREQ_FLAG_ADD_IF_NEW. Si la aplicación intenta quitar o reemplazar un encabezado mediante HTTP_ADDREQ_FLAG_REMOVE o HTTP_ADDREQ_FLAG_REPLACE, solo se puede proporcionar un encabezado en *lpszHeaders*.

##  <a name="chttpfile"></a>  CHttpFile::CHttpFile

Se llama a esta función miembro para construir `CHttpFile` un objeto.

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

*hFile*<br/>
Identificador de un archivo de Internet.

*hSession*<br/>
Identificador de una sesión de Internet.

*pstrObject*<br/>
Puntero a una cadena que contiene el `CHttpFile` objeto.

*pstrServer*<br/>
Puntero a una cadena que contiene el nombre del servidor.

*pstrVerb*<br/>
Puntero a una cadena que contiene el método que se va a usar al enviar la solicitud. Puede ser POST, HEAD o GET.

*dwContext*<br/>
Identificador de contexto para el `CHttpFile` objeto. Vea la **sección Comentarios** para obtener más información sobre este parámetro.

*pConnection*<br/>
Un puntero a un objeto [CHttpConnection (](../../mfc/reference/chttpconnection-class.md) .

### <a name="remarks"></a>Comentarios

Nunca se construye un `CHttpFile` objeto directamente, sino que se llama a [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) o [CHttpConnection (:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) en su lugar.

MFC envía el valor `dwContext` predeterminado para `CHttpFile` al objeto desde el objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) que creó el `CHttpFile` objeto. Cuando llame `CInternetSession::OpenURL` a o `CHttpConnection` para construir un `CHttpFile` objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo [Internet First Steps: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

##  <a name="endrequest"></a>  CHttpFile::EndRequest

Llame a esta función miembro para finalizar una solicitud enviada a un servidor HTTP con la función miembro [SendRequestEx](#sendrequestex) .

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Marcas que describen la operación. Para obtener una lista de las marcas adecuadas, vea [HttpEndRequest](/windows/win32/api/wininet/nf-wininet-httpendrequestw) en el Windows SDK.

*lpBuffIn*<br/>
Puntero a un [INTERNET_BUFFERS](/windows/win32/api/wininet/ns-wininet-internet_buffersw) inicializado que describe el búfer de entrada utilizado para la operación.

*dwContext*<br/>
Identificador de contexto para la operación `CHttpFile`. Vea la sección Comentarios para obtener más información sobre este parámetro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, determine la causa del error examinando el objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) generado.

### <a name="remarks"></a>Comentarios

MFC envía el valor predeterminado de *dwContext* `CHttpFile` al objeto desde el objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) que creó el `CHttpFile` objeto. Cuando llame a [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) o [CHttpConnection (](../../mfc/reference/chttpconnection-class.md) para construir un `CHttpFile` objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Vea el [artículo sobre los primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

##  <a name="getfileurl"></a>  CHttpFile::GetFileURL

Llame a esta función miembro para obtener el nombre del archivo HTTP como una dirección URL.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene una dirección URL que hace referencia al recurso asociado a este archivo.

### <a name="remarks"></a>Comentarios

Utilice esta función miembro solo después de una llamada correcta a [SendRequest](#sendrequest) o en `CHttpFile` un objeto creado correctamente por [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

##  <a name="getobject"></a>  CHttpFile::GetObject

Llame a esta función miembro para obtener el nombre del objeto asociado a este `CHttpFile`.

```
CString GetObject() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el nombre del objeto.

### <a name="remarks"></a>Comentarios

Utilice esta función miembro solo después de una llamada correcta a [SendRequest](#sendrequest) o en `CHttpFile` un objeto creado correctamente por [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

##  <a name="getverb"></a>  CHttpFile::GetVerb

Llame a esta función miembro para obtener el verbo HTTP (o el método) asociado `CHttpFile`a este.

```
CString GetVerb() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el nombre del verbo http (o del método).

### <a name="remarks"></a>Comentarios

Utilice esta función miembro solo después de una llamada correcta a [SendRequest](#sendrequest) o en `CHttpFile` un objeto creado correctamente por [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

##  <a name="queryinfo"></a>  CHttpFile::QueryInfo

Llame a esta función miembro para devolver los encabezados de solicitud o respuesta de una solicitud HTTP.

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
Combinación del atributo que se va a consultar y de las marcas siguientes que especifican el tipo de información solicitada:

- HTTP_QUERY_CUSTOM busca el nombre del encabezado y devuelve este valor en *lpvBuffer* en la salida. HTTP_QUERY_CUSTOM produce una aserción si no se encuentra el encabezado.

- HTTP_QUERY_FLAG_REQUEST_HEADERS normalmente, la aplicación consulta los encabezados de respuesta, pero una aplicación también puede consultar los encabezados de solicitud mediante el uso de esta marca.

- HTTP_QUERY_FLAG_SYSTEMTIME para los encabezados cuyo valor es una cadena de fecha y hora, como "Last-Modified-Time", esta marca devuelve el valor de encabezado como una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) de Win32 estándar que no requiere que la aplicación analice los datos. Si usa esta marca, puede que desee usar la `SYSTEMTIME` invalidación de la función.

- HTTP_QUERY_FLAG_NUMBER para los encabezados cuyo valor es un número, como el código de estado, esta marca devuelve los datos como un número de 32 bits.

Vea la sección **comentarios** para obtener una lista de los valores posibles.

*lpvBuffer*<br/>
Puntero al búfer que recibe la información.

*lpdwBufferLength*<br/>
En la entrada, apunta a un valor que contiene la longitud del búfer de datos, en número de caracteres o bytes. Vea la sección **comentarios** para obtener información más detallada sobre este parámetro.

*lpdwIndex*<br/>
Un puntero a un índice de encabezado de base cero. Puede ser NULL. Utilice esta marca para enumerar varios encabezados con el mismo nombre. En la entrada, *lpdwIndex* indica el índice del encabezado especificado que se va a devolver. En la salida, *lpdwIndex* indica el índice del siguiente encabezado. Si no se encuentra el índice siguiente, se devuelve ERROR_HTTP_HEADER_NOT_FOUND.

*str*<br/>
Referencia al objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que recibe la información devuelta.

*dwIndex*<br/>
Valor de índice. Vea *lpdwIndex*.

*pSysTime*<br/>
Puntero a una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) de Win32.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

### <a name="remarks"></a>Comentarios

Utilice esta función miembro solo después de una llamada correcta a [SendRequest](#sendrequest) o en `CHttpFile` un objeto creado correctamente por [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Puede recuperar los siguientes tipos de datos de `QueryInfo`:

- cadenas (valor predeterminado)

- `SYSTEMTIME`(para "Data:" "Expires:" etc., encabezados)

- DWORD (para STATUS_CODE, CONTENT_LENGTH, etc.)

Cuando se escribe una cadena en el búfer y la función miembro se ejecuta correctamente, `lpdwBufferLength` contiene la longitud de la cadena en caracteres menos 1 para el carácter nulo de terminación.

Los valores posibles de *dwInfoLevel* incluyen:

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

##  <a name="queryinfostatuscode"></a>  CHttpFile::QueryInfoStatusCode

Llame a esta función miembro para obtener el código de estado asociado a una solicitud HTTP y colóquelo en el parámetro *dwStatusCode* proporcionado.

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>Parámetros

*dwStatusCode*<br/>
Referencia a un código de estado. Los códigos de estado indican si el evento solicitado se ha realizado correctamente o no. Vea la **sección Comentarios** para obtener una selección de descripciones de códigos de estado.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

### <a name="remarks"></a>Comentarios

Utilice esta función miembro solo después de una llamada correcta a [SendRequest](#sendrequest) o en `CHttpFile` un objeto creado correctamente por [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Los códigos de Estado HTTP se dividen en grupos que indican si la solicitud se ha realizado correctamente o no. En las tablas siguientes se describen los grupos de códigos de estado y los códigos de Estado HTTP más comunes.

|Grupo|Significado|
|-----------|-------------|
|200-299|Correcto|
|300-399|Información|
|400-499|Error de solicitud|
|500-599|Error de servidor|

Códigos de Estado HTTP comunes:

|Código de estado|Significado|
|-----------------|-------------|
|200|Dirección URL encontrada, después de la transmisión|
|400|Solicitud ininteligible|
|404|No se encontró la dirección URL solicitada|
|405|El servidor no admite el método solicitado|
|500|Error desconocido del servidor|
|503|Se alcanzó la capacidad del servidor|

##  <a name="sendrequest"></a>  CHttpFile::SendRequest

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
Puntero a una cadena que contiene el nombre de los encabezados que se van a enviar.

*dwHeadersLen*<br/>
La longitud de los encabezados identificados por *pstrHeaders*.

*lpOptional*<br/>
Los datos opcionales que se enviarán inmediatamente después de los encabezados de solicitud. Normalmente se usa para las operaciones POST y PUT. Puede ser NULL si no hay ningún dato opcional para enviar.

*dwOptionalLen*<br/>
Longitud de *lpOptional*.

*strHeaders*<br/>
Cadena que contiene el nombre de los encabezados de la solicitud que se está enviando.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, determine la causa del error examinando el objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) generado.

##  <a name="sendrequestex"></a>  CHttpFile::SendRequestEx

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
Número de bytes que se van a enviar en la solicitud.

*dwFlags*<br/>
Marcas que describen la operación. Para obtener una lista de las marcas adecuadas, consulte [HttpSendRequestEx](/windows/win32/api/wininet/nf-wininet-httpsendrequestexw) en el Windows SDK.

*dwContext*<br/>
Identificador de contexto para la operación `CHttpFile`. Vea la sección Comentarios para obtener más información sobre este parámetro.

*lpBuffIn*<br/>
Puntero a un [INTERNET_BUFFERS](/windows/win32/api/wininet/ns-wininet-internet_buffersw) inicializado que describe el búfer de entrada utilizado para la operación.

*lpBuffOut*<br/>
Puntero a un INTERNET_BUFFERS inicializado que describe el búfer de salida que se usa para la operación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente. Si se produce un error en la llamada, determine la causa del error examinando el objeto [CInternetException](../../mfc/reference/cinternetexception-class.md) generado.

### <a name="remarks"></a>Comentarios

Esta función permite que la aplicación envíe datos mediante los métodos [Write](../../mfc/reference/cinternetfile-class.md#write) y [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) de `CInternetFile`. Debe conocer la longitud de los datos que se van a enviar antes de llamar a cualquier invalidación de esta función. La primera invalidación le permite especificar la longitud de los datos que desea enviar. La segunda invalidación acepta punteros a estructuras INTERNET_BUFFERS, que se pueden usar para describir el búfer con gran detalle.

Después de escribir el contenido en el archivo, llame a [EndRequest](#endrequest) para finalizar la operación.

MFC envía el valor predeterminado de *dwContext* `CHttpFile` al objeto desde el objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) que creó el `CHttpFile` objeto. Cuando llame a [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) o [CHttpConnection (](../../mfc/reference/chttpconnection-class.md) para construir un `CHttpFile` objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo [Internet First Steps: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

### <a name="example"></a>Ejemplo

Este fragmento de código envía el contenido de una cadena a un archivo DLL denominado MFCISAPI. DLL en el servidor LOCALHOST. Aunque en este ejemplo se usa solo una `WriteString`llamada a, se acepta el uso de varias llamadas para enviar datos en bloques.

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>Vea también

[CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile (clase)](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpConnection (clase)](../../mfc/reference/chttpconnection-class.md)
