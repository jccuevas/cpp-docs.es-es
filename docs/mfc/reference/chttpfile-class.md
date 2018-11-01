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
ms.openlocfilehash: 1fa1b63ed045c176841565473476185bb15999e3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564468"
---
# <a name="chttpfile-class"></a>CHttpFile (clase)

Proporciona la funcionalidad para solicitar y leer archivos en un servidor HTTP.

## <a name="syntax"></a>Sintaxis

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Name|Descripción|
|----------|-----------------|
|[CHttpFile::CHttpFile](#chttpfile)|Crea un objeto `CHttpFile`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CHttpFile:: AddRequestHeaders](#addrequestheaders)|Agrega encabezados a la solicitud enviada a un servidor HTTP.|
|[CHttpFile::EndRequest](#endrequest)|Finaliza una solicitud enviada a un servidor HTTP con el [SendRequestEx](#sendrequestex) función miembro.|
|[CHttpFile::GetFileURL](#getfileurl)|Obtiene la dirección URL para el archivo especificado.|
|[CHttpFile::GetObject](#getobject)|Obtiene el objeto de destino del verbo en una solicitud a un servidor HTTP.|
|[CHttpFile::GetVerb](#getverb)|Obtiene el verbo que se usó en una solicitud a un servidor HTTP.|
|[QueryInfo](#queryinfo)|Devuelve los encabezados de solicitud o respuesta desde el servidor HTTP.|
|[QueryInfoStatusCode](#queryinfostatuscode)|Recupera el código de estado asociado a una solicitud HTTP y lo coloca en proporcionado `dwStatusCode` parámetro.|
|[CHttpFile:: SendRequest](#sendrequest)|Envía una solicitud a un servidor HTTP.|
|[CHttpFile::SendRequestEx](#sendrequestex)|Envía una solicitud a un servidor HTTP mediante el [escribir](../../mfc/reference/cinternetfile-class.md#write) o [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) métodos de `CInternetFile`.|

## <a name="remarks"></a>Comentarios

Si la sesión de Internet lee datos desde un servidor HTTP, debe crear una instancia de `CHttpFile`.

Para obtener más información sobre cómo `CHttpFile` funciona con las clases de Internet de MFC, vea el artículo [Internet programar con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

##  <a name="addrequestheaders"></a>  CHttpFile:: AddRequestHeaders

Llame a esta función miembro para agregar uno o más encabezados de solicitud HTTP a la solicitud HTTP controlen.

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
Un puntero a una cadena que contiene los encabezados que se anexará a la solicitud o el encabezado. Cada encabezado debe terminar con un par de CR/LF.

*dwFlags*<br/>
Modifica la semántica de los encabezados de nuevo. Puede ser uno de los siguientes:

- Encabezados HTTP_ADDREQ_FLAG_COALESCE combina el mismo nombre, con la marca para agregar el primer encabezado que se encuentra en el encabezado posteriores. Por ejemplo, "Accept: texto /\*" seguido de "aceptación: audio /\*" da como resultado la formación de solo el encabezado "Accept: texto /\*, audio /\*". Es responsabilidad de la aplicación que realiza la llamada para garantizar un esquema coherente con respecto a los datos que recibe las solicitudes enviadas con encabezados combinados o independientes.

- HTTP_ADDREQ_FLAG_REPLACE realiza una eliminación y agregue para reemplazar el encabezado actual. El nombre del encabezado que se usará para quitar el encabezado actual y el valor completo se usará para agregar el nuevo encabezado. Si el valor del encabezado está vacío y se encuentra el encabezado, se quita. Si no está vacío, se reemplaza el valor del encabezado.

- HTTP_ADDREQ_FLAG_ADD_IF_NEW solo agrega el encabezado si aún no existe. Si existe, se devuelve un error.

- HTTP_ADDREQ_FLAG_ADD utilizado con reemplazar. Agrega el encabezado si no existe.

*dwHeadersLen*<br/>
La longitud en caracteres, de *pstrHeaders*. Si es-1 L, a continuación, *pstrHeaders* se supone que debe terminar en cero y se calcula la longitud.

*str*<br/>
Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el encabezado de solicitud o agregar los encabezados.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.

### <a name="remarks"></a>Comentarios

`AddRequestHeaders` anexa los encabezados adicionales, sin formato para el identificador de solicitud HTTP. Se está pensado para su uso por los clientes sofisticados que necesitan un control detallado sobre la solicitud exacta que se envían al servidor HTTP.

> [!NOTE]
>  La aplicación puede pasar varios encabezados en *pstrHeaders* o *str* para un `AddRequestHeaders` llamar mediante HTTP_ADDREQ_FLAG_ADD o HTTP_ADDREQ_FLAG_ADD_IF_NEW. Si la aplicación intenta quitar o reemplazar un encabezado con HTTP_ADDREQ_FLAG_REMOVE o HTTP_ADDREQ_FLAG_REPLACE, se puede proporcionar solo un encabezado en *lpszHeaders*.

##  <a name="chttpfile"></a>  CHttpFile::CHttpFile

Se llama a esta función miembro para construir un `CHttpFile` objeto.

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
Identificador de sesión de Internet.

*pstrObject*<br/>
Un puntero a una cadena que contiene el `CHttpFile` objeto.

*pstrServer*<br/>
Un puntero a una cadena que contiene el nombre del servidor.

*pstrVerb*<br/>
Un puntero a una cadena que contiene el método que se utilizará al enviar la solicitud. Puede ser POST, HEAD, u obtener.

*dwContext*<br/>
El identificador de contexto para el `CHttpFile` objeto. Consulte **comentarios** para obtener más información acerca de este parámetro.

*pConnection*<br/>
Un puntero a un [CHttpConnection](../../mfc/reference/chttpconnection-class.md) objeto.

### <a name="remarks"></a>Comentarios

Nunca de construir un `CHttpFile` objeto directamente; más bien llamar a [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) o [CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) en su lugar.

El valor predeterminado de `dwContext` se envía por MFC para la `CHttpFile` objeto desde el [CInternetSession](../../mfc/reference/cinternetsession-class.md) de objeto que creó el `CHttpFile` objeto. Cuando se llama a `CInternetSession::OpenURL` o `CHttpConnection` para construir un `CHttpFile` de objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve al [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

##  <a name="endrequest"></a>  CHttpFile::EndRequest

Llame a esta función miembro para finalizar una solicitud enviada a un servidor HTTP con el [SendRequestEx](#sendrequestex) función miembro.

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Marcas que describen la operación. Para obtener una lista de las marcas apropiadas, consulte [HttpEndRequest](/windows/desktop/api/wininet/nf-wininet-httpendrequesta) en el SDK de Windows.

*lpBuffIn*<br/>
Puntero a un inicializado [INTERNET_BUFFERS](/windows/desktop/api/wininet/ns-wininet-_internet_buffersa) que describe el búfer de entrada utilizado para la operación.

*dwContext*<br/>
Identificador de contexto para la operación `CHttpFile`. Vea la sección Comentarios para obtener más información acerca de este parámetro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, determinar la causa del error examinando el producida [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto.

### <a name="remarks"></a>Comentarios

El valor predeterminado de *dwContext* se envía por MFC para la `CHttpFile` objeto desde el [CInternetSession](../../mfc/reference/cinternetsession-class.md) de objeto que creó el `CHttpFile` objeto. Cuando se llama a [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) o [CHttpConnection](../../mfc/reference/chttpconnection-class.md) para construir un `CHttpFile` de objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve al [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

##  <a name="getfileurl"></a>  CHttpFile::GetFileURL

Llame a esta función miembro para obtener el nombre del archivo como una dirección URL HTTP.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene una dirección URL que hacen referencia a los recursos asociados con este archivo.

### <a name="remarks"></a>Comentarios

Utilice esta función miembro solo después de una llamada correcta al [SendRequest](#sendrequest) o en un `CHttpFile` objeto correctamente creado por [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

##  <a name="getobject"></a>  CHttpFile::GetObject

Llame a esta función miembro para obtener el nombre del objeto asociado a este `CHttpFile`.

```
CString GetObject() const;
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el nombre del objeto.

### <a name="remarks"></a>Comentarios

Utilice esta función miembro solo después de una llamada correcta al [SendRequest](#sendrequest) o en un `CHttpFile` objeto correctamente creado por [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

##  <a name="getverb"></a>  CHttpFile::GetVerb

Llame a esta función miembro para obtener el verbo HTTP (o método) asociado a este `CHttpFile`.

```
CString GetVerb() const;
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el nombre del verbo HTTP (o método).

### <a name="remarks"></a>Comentarios

Utilice esta función miembro solo después de una llamada correcta al [SendRequest](#sendrequest) o en un `CHttpFile` objeto correctamente creado por [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

##  <a name="queryinfo"></a>  QueryInfo

Llame a esta función miembro para devolver la respuesta o encabezados de solicitud de una solicitud HTTP.

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
Una combinación del atributo a las consultas y las marcas siguientes que especifican el tipo de información solicitada:

- HTTP_QUERY_CUSTOM busca el nombre de encabezado y devuelve este valor en *lpvBuffer* en la salida. HTTP_QUERY_CUSTOM produce una aserción si no se encuentra el encabezado.

- HTTP_QUERY_FLAG_REQUEST_HEADERS normalmente, la aplicación consulta los encabezados de respuesta, pero una aplicación también puede consultar los encabezados de solicitud mediante el uso de esta marca.

- HTTP_QUERY_FLAG_SYSTEMTIME para aquellos encabezados cuyo valor es una cadena de fecha y hora, por ejemplo, "Last-Modified-Time," esta marca devuelve el valor del encabezado como un estándar de Win32 [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que no requiere la aplicación analizar los datos. Si usa esta marca, puede usar el `SYSTEMTIME` la invalidación de la función.

- HTTP_QUERY_FLAG_NUMBER para aquellos encabezados cuyo valor es un número, como el código de estado, esta marca devuelve los datos como un número de 32 bits.

Consulte la **comentarios** sección para obtener una lista de los valores posibles.

*lpvBuffer*<br/>
Un puntero al búfer que recibe la información.

*lpdwBufferLength*<br/>
En la entrada, señala a un valor que contiene la longitud del búfer de datos, en el número de caracteres o bytes. Consulte la **comentarios** sección para obtener más información acerca de este parámetro.

*lpdwIndex*<br/>
Un puntero a un índice de base cero del encabezado. Puede ser NULL. Utilice este marcador para enumerar varios encabezados con el mismo nombre. En la entrada, *lpdwIndex* indica el índice del encabezado especificado para devolver. En la salida, *lpdwIndex* indica el índice del encabezado siguiente. Si no se encuentra el siguiente índice, se devuelve ERROR_HTTP_HEADER_NOT_FOUND.

*str*<br/>
Una referencia a la [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que recibe la información devuelta.

*dwIndex*<br/>
Un valor de índice. Consulte *lpdwIndex*.

*pSysTime*<br/>
Un puntero a Win32 [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) estructura.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.

### <a name="remarks"></a>Comentarios

Utilice esta función miembro solo después de una llamada correcta al [SendRequest](#sendrequest) o en un `CHttpFile` objeto correctamente creado por [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Puede recuperar los siguientes tipos de datos de `QueryInfo`:

- cadenas (valor predeterminado)

- `SYSTEMTIME` (para "datos:" "Expires:" encabezados etcetera,)

- DWORD (para STATUS_CODE, CONTENT_LENGTH, etcetera.)

Cuando se escribe una cadena en el búfer y la función miembro se realiza correctamente, `lpdwBufferLength` contiene la longitud de la cadena en caracteres menos 1 para el carácter nulo de terminación.

Los posibles *dwInfoLevel* los valores incluyen:

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

##  <a name="queryinfostatuscode"></a>  QueryInfoStatusCode

Llame a esta función miembro para obtener el código de estado asociado a una solicitud HTTP y colocarlo en proporcionado *dwStatusCode* parámetro.

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>Parámetros

*dwStatusCode*<br/>
Una referencia a un código de estado. Códigos de estado indican el éxito o fracaso del evento solicitado. Consulte **comentarios** para una selección de las descripciones del código de estado.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.

### <a name="remarks"></a>Comentarios

Utilice esta función miembro solo después de una llamada correcta al [SendRequest](#sendrequest) o en un `CHttpFile` objeto correctamente creado por [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Códigos de estado HTTP se dividen en grupos que indica el éxito o fracaso de la solicitud. Las tablas siguientes describen los grupos de código de estado y los códigos de estado HTTP más comunes.

|Agrupar|Significado|
|-----------|-------------|
|200-299|Correcto|
|300-399|Información|
|400-499|Error de solicitud|
|500-599|Error del servidor|

Códigos de estado HTTP comunes:

|Código de estado|Significado|
|-----------------|-------------|
|200|Dirección URL que encuentra, se indica a continuación de transmisión|
|400|Solicitud ininteligible|
|404|Solicitado no se encontró la dirección URL|
|405|Servidor no admite el método solicitado|
|500|Error desconocido del servidor|
|503|Se alcanzó la capacidad de servidor|

##  <a name="sendrequest"></a>  CHttpFile:: SendRequest

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
Un puntero a una cadena que contiene el nombre de los encabezados que se va a enviar.

*dwHeadersLen*<br/>
La longitud de los encabezados identificado por *pstrHeaders*.

*lpOptional*<br/>
Los datos opcionales al enviar inmediatamente después de los encabezados de solicitud. Esto generalmente se usa para las operaciones POST y PUT. Esto puede ser NULL si no hay ningún dato opcional para enviar.

*dwOptionalLen*<br/>
La longitud de *lpOptional*.

*strHeaders*<br/>
Una cadena que contiene el nombre de los encabezados de la solicitud que se envían.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, determinar la causa del error examinando el producida [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto.

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
Número de bytes que se enviarán en la solicitud.

*dwFlags*<br/>
Marcas que describen la operación. Para obtener una lista de marcas adecuadas, consulte [HttpSendRequestEx](/windows/desktop/api/wininet/nf-wininet-httpsendrequestexa) en el SDK de Windows.

*dwContext*<br/>
Identificador de contexto para la operación `CHttpFile`. Vea la sección Comentarios para obtener más información acerca de este parámetro.

*lpBuffIn*<br/>
Puntero a un inicializado [INTERNET_BUFFERS](/windows/desktop/api/wininet/ns-wininet-_internet_buffersa) que describe el búfer de entrada utilizado para la operación.

*lpBuffOut*<br/>
Puntero a un INTERNET_BUFFERS inicializada que describe el búfer de salida utilizado para la operación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente. Si se produce un error en la llamada, determinar la causa del error examinando el producida [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto.

### <a name="remarks"></a>Comentarios

Esta función permite que la aplicación enviar datos mediante el [escribir](../../mfc/reference/cinternetfile-class.md#write) y [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) métodos de `CInternetFile`. Debe conocer la longitud de los datos que se va a enviar antes de llamar a cualquier invalidación de esta función. El primer reemplazo le permite especificar la longitud de datos que le gustaría enviar. El segundo reemplazo acepta punteros a estructuras INTERNET_BUFFERS, que se pueden usar para describir el búfer con gran detalle.

Después de contenido se escribe en el archivo, llame a [EndRequest](#endrequest) para finalizar la operación.

El valor predeterminado de *dwContext* se envía por MFC para la `CHttpFile` objeto desde el [CInternetSession](../../mfc/reference/cinternetsession-class.md) de objeto que creó el `CHttpFile` objeto. Cuando se llama a [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) o [CHttpConnection](../../mfc/reference/chttpconnection-class.md) para construir un `CHttpFile` de objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve al [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

### <a name="example"></a>Ejemplo

Este fragmento de código envía el contenido de una cadena a un archivo DLL denominado MFCISAPI. Archivo DLL en el servidor LOCALHOST. Aunque este ejemplo utiliza sólo una llamada a `WriteString`, utilizando varias llamadas para enviar datos en bloques es aceptable.

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>Vea también

[CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile (clase)](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpConnection (clase)](../../mfc/reference/chttpconnection-class.md)
