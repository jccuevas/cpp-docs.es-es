---
title: Clase CHttpFile | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e9af23bb74ba8e96f29a5b7cc4139d2932df8c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="chttpfile-class"></a>Clase CHttpFile
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
|[QueryInfoStatusCode](#queryinfostatuscode)|Recupera el código de estado asociado a una solicitud HTTP y lo coloca en el proporcionado `dwStatusCode` parámetro.|  
|[CHttpFile:: SendRequest](#sendrequest)|Envía una solicitud a un servidor HTTP.|  
|[CHttpFile::SendRequestEx](#sendrequestex)|Envía una solicitud a un servidor HTTP mediante el [escribir](../../mfc/reference/cinternetfile-class.md#write) o [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) métodos de `CInternetFile`.|  
  
## <a name="remarks"></a>Comentarios  
 Si la sesión de Internet lee los datos de un servidor HTTP, debe crear una instancia de `CHttpFile`.  
  
 Para obtener más información sobre cómo `CHttpFile` funciona con las demás clases de Internet de MFC, vea el artículo [programación para Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CHttpFile`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
  
##  <a name="addrequestheaders"></a>CHttpFile:: AddRequestHeaders  
 Llame a esta función miembro para agregar uno o más encabezados de solicitud HTTP para la solicitud HTTP controlen.  
  
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
 `pstrHeaders`  
 Un puntero a una cadena que contiene el encabezado o encabezados para anexar a la solicitud. Cada encabezado debe terminar con un par de caracteres CR/LF.  
  
 `dwFlags`  
 Modifica la semántica de los encabezados de nuevo. Puede ser uno de los siguientes:  
  
- `HTTP_ADDREQ_FLAG_COALESCE`Combina los encabezados del mismo nombre, con la marca para agregar el primer encabezado detectado que el encabezado posterior. Por ejemplo, "Accept: texto / *" seguido de "Accept: audio /\*" da como resultado la formación de solo encabezado "Accept: texto /\*, audio /\*". Depende de la aplicación que realiza la llamada para garantizar un esquema coherente con respecto a los datos que recibe las solicitudes enviadas con encabezados combinados o en otra diferentes.  
  
- `HTTP_ADDREQ_FLAG_REPLACE`Realiza una eliminación y agregar para reemplazar el encabezado actual. El nombre del encabezado que se usará para quitar el encabezado actual y el valor completo se usará para agregar el nuevo encabezado. Si el valor de encabezado está vacío y se encuentra el encabezado, se quita. Si no está vacío, se reemplaza el valor del encabezado.  
  
- `HTTP_ADDREQ_FLAG_ADD_IF_NEW`Solo agrega el encabezado si aún no existe. Si existe, se devuelve un error.  
  
- `HTTP_ADDREQ_FLAG_ADD`Se utiliza con reemplazo. Agrega el encabezado si no existe.  
  
 `dwHeadersLen`  
 La longitud, en caracteres, de `pstrHeaders`. Si se trata a continuación, en-1 L `pstrHeaders` se supone que termina en cero y se calcula la longitud.  
  
 `str`  
 Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el encabezado de solicitud o agregar los encabezados.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 `AddRequestHeaders`anexa encabezados adicionales y formato libre para el controlador de la solicitud HTTP. Está diseñado para su uso por los clientes sofisticados que necesitan un control detallado sobre la solicitud exacta enviada al servidor HTTP.  
  
> [!NOTE]
>  La aplicación puede pasar varios encabezados en `pstrHeaders` o `str` para un `AddRequestHeaders` llama mediante `HTTP_ADDREQ_FLAG_ADD` o `HTTP_ADDREQ_FLAG_ADD_IF_NEW`. Si la aplicación intenta quitar o reemplazar un encabezado mediante **HTTP_ADDREQ_FLAG_REMOVE** o `HTTP_ADDREQ_FLAG_REPLACE`, se puede proporcionar un único encabezado en `lpszHeaders`.  
  
##  <a name="chttpfile"></a>CHttpFile::CHttpFile  
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
 `hFile`  
 Un identificador a un archivo de Internet.  
  
 `hSession`  
 Un identificador para una sesión de Internet.  
  
 *pstrObject*  
 Un puntero a una cadena que contiene el `CHttpFile` objeto.  
  
 `pstrServer`  
 Un puntero a una cadena que contiene el nombre del servidor.  
  
 `pstrVerb`  
 Un puntero a una cadena que contiene el método que se utilizará al enviar la solicitud. Puede ser **POST**, **HEAD**, o `GET`.  
  
 dwContext  
 El identificador de contexto para la `CHttpFile` objeto. Vea **comentarios** para obtener más información acerca de este parámetro.  
  
 `pConnection`  
 Un puntero a un [CHttpConnection](../../mfc/reference/chttpconnection-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Nunca de construir un `CHttpFile` objeto directamente; en su lugar llame a [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) o [CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) en su lugar.  
  
 El valor predeterminado de `dwContext` se envía por MFC para la `CHttpFile` objeto desde el [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto que creó el `CHttpFile` objeto. Cuando se llama a `CInternetSession::OpenURL` o `CHttpConnection` para construir un `CHttpFile` de objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve al [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Vea el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.  
  
##  <a name="endrequest"></a>CHttpFile::EndRequest  
 Llame a esta función miembro para finalizar una solicitud enviada a un servidor HTTP con el [SendRequestEx](#sendrequestex) función miembro.  
  
```  
BOOL EndRequest(
    DWORD dwFlags = 0,  
    LPINTERNET_BUFFERS lpBuffIn = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwFlags`  
 Marcas que describen la operación. Para obtener una lista de las marcas adecuadas, vea [HttpEndRequest](http://msdn.microsoft.com/library/windows/desktop/aa384230) en el SDK de Windows.  
  
 `lpBuffIn`  
 Puntero a un inicializado [INTERNET_BUFFERS](http://msdn.microsoft.com/library/windows/desktop/aa385132) que describe el búfer de entrada que se utiliza para la operación.  
  
 `dwContext`  
 Identificador de contexto para la operación `CHttpFile`. Vea la sección Comentarios para obtener más información acerca de este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, determinar la causa del error examinando el produce [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 El valor predeterminado de `dwContext` se envía por MFC para la `CHttpFile` objeto desde el [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto que creó el `CHttpFile` objeto. Cuando se llama a [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) o [CHttpConnection](../../mfc/reference/chttpconnection-class.md) para construir un `CHttpFile` de objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve al [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Vea el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.  
  
##  <a name="getfileurl"></a>CHttpFile::GetFileURL  
 Llame a esta función miembro para obtener el nombre del archivo como una dirección URL HTTP.  
  
```  
virtual CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene una dirección URL que hacen referencia a los recursos asociados a este archivo.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función miembro sólo después de una llamada correcta a [SendRequest](#sendrequest) o en un `CHttpFile` objeto creado correctamente haciendo [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
##  <a name="getobject"></a>CHttpFile::GetObject  
 Llame a esta función miembro para obtener el nombre del objeto asociado a este `CHttpFile`.  
  
```  
CString GetObject() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el nombre del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función miembro sólo después de una llamada correcta a [SendRequest](#sendrequest) o en un `CHttpFile` objeto creado correctamente haciendo [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
##  <a name="getverb"></a>CHttpFile::GetVerb  
 Llame a esta función miembro para obtener el verbo HTTP (o método) asociado a este `CHttpFile`.  
  
```  
CString GetVerb() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el nombre del verbo HTTP (o método).  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función miembro sólo después de una llamada correcta a [SendRequest](#sendrequest) o en un `CHttpFile` objeto creado correctamente haciendo [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
##  <a name="queryinfo"></a>QueryInfo  
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
 `dwInfoLevel`  
 Una combinación del atributo en la consulta y las marcas siguientes que especifican el tipo de información solicitada:  
  
- **HTTP_QUERY_CUSTOM** busca el nombre de encabezado y devuelve este valor en `lpvBuffer` en la salida. **HTTP_QUERY_CUSTOM** produce una aserción si no se encuentra el encabezado.  
  
- **HTTP_QUERY_FLAG_REQUEST_HEADERS** por lo general, la aplicación consulta los encabezados de respuesta, pero una aplicación también puede consultar los encabezados de solicitud mediante el uso de esta marca.  
  
- **HTTP_QUERY_FLAG_SYSTEMTIME** para esos encabezados cuyo valor es una cadena de fecha y hora, como "Last-Modified-Time," esta marca devuelve el valor del encabezado como Win32 estándar [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que no requiere el aplicación para analizar los datos. Si utiliza esta marca, puede que desee usar el `SYSTEMTIME` la invalidación de la función.  
  
- **HTTP_QUERY_FLAG_NUMBER** para esos encabezados cuyo valor es un número, por ejemplo, el código de estado, este indicador devuelve los datos como un número de 32 bits.  
  
 Consulte la **comentarios** sección para obtener una lista de los valores posibles.  
  
 `lpvBuffer`  
 Un puntero al búfer que recibe la información.  
  
 `lpdwBufferLength`  
 En la entrada, esto apunta a un valor que contiene la longitud del búfer de datos, en número de caracteres o bytes. Consulte la **comentarios** sección para obtener más información acerca de este parámetro.  
  
 `lpdwIndex`  
 Un puntero a un índice de base cero del encabezado. Puede ser **NULL**. Use esta marca para enumerar varios encabezados con el mismo nombre. En la entrada, `lpdwIndex` indica el índice del encabezado especificado para devolver. En la salida, `lpdwIndex` indica el índice del siguiente encabezado. Si no se encuentra el siguiente índice, **ERROR_HTTP_HEADER_NOT_FOUND** se devuelve.  
  
 `str`  
 Una referencia a la [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que recibe la información devuelta.  
  
 `dwIndex`  
 Un valor de índice. Vea `lpdwIndex`.  
  
 *pSysTime*  
 Un puntero a Win32 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función miembro sólo después de una llamada correcta a [SendRequest](#sendrequest) o en un `CHttpFile` objeto creado correctamente haciendo [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
 Puede recuperar los siguientes tipos de datos de `QueryInfo`:  
  
-   cadenas (valor predeterminado)  
  
- `SYSTEMTIME`(para "datos:" "Expires:" encabezados etcetera,)  
  
- `DWORD`(para **STATUS_CODE**, **CONTENT_LENGTH**, etcetera.)  
  
 Cuando se escribe una cadena en el búfer y la función miembro se realiza correctamente, `lpdwBufferLength` contiene la longitud de la cadena en caracteres menos 1 para la terminación **NULL** caracteres.  
  
 Los posibles `dwInfoLevel` valores incluyen:  
  
- **HTTP_QUERY_MIME_VERSION**  
  
- **HTTP_QUERY_CONTENT_TYPE**  
  
- **HTTP_QUERY_CONTENT_TRANSFER_ENCODING**  
  
- **HTTP_QUERY_CONTENT_ID**  
  
- **HTTP_QUERY_CONTENT_DESCRIPTION**  
  
- **HTTP_QUERY_CONTENT_LENGTH**  
  
- **HTTP_QUERY_ALLOWED_METHODS**  
  
- **HTTP_QUERY_PUBLIC_METHODS**  
  
- **HTTP_QUERY_DATE**  
  
- **HTTP_QUERY_EXPIRES**  
  
- **HTTP_QUERY_LAST_MODIFIED**  
  
- **HTTP_QUERY_MESSAGE_ID**  
  
- **HTTP_QUERY_URI**  
  
- **HTTP_QUERY_DERIVED_FROM**  
  
- **HTTP_QUERY_LANGUAGE**  
  
- **HTTP_QUERY_COST**  
  
- **HTTP_QUERY_WWW_LINK**  
  
- **HTTP_QUERY_PRAGMA**  
  
- **HTTP_QUERY_VERSION**  
  
- **HTTP_QUERY_STATUS_CODE**  
  
- **HTTP_QUERY_STATUS_TEXT**  
  
- **HTTP_QUERY_RAW_HEADERS**  
  
- **HTTP_QUERY_RAW_HEADERS_CRLF**  
  
##  <a name="queryinfostatuscode"></a>QueryInfoStatusCode  
 Llame a esta función miembro para obtener el código de estado asociado a una solicitud HTTP y colocarlo en proporcionado `dwStatusCode` parámetro.  
  
```  
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStatusCode`  
 Una referencia a un código de estado. Códigos de estado indican el éxito o fracaso del evento solicitado. Vea **comentarios** para una selección de las descripciones de código de estado.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función miembro sólo después de una llamada correcta a [SendRequest](#sendrequest) o en un `CHttpFile` objeto creado correctamente haciendo [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
 Códigos de estado HTTP se dividen en grupos que indica el éxito o fracaso de la solicitud. En las tablas siguientes se describen los grupos de código de estado y los códigos de estado HTTP más comunes.  
  
|Agrupar|Significado|  
|-----------|-------------|  
|200-299|Correcto|  
|300-399|Información|  
|400-499|Error de solicitud|  
|500-599|Error del servidor|  
  
 Códigos de estado HTTP comunes:  
  
|Código de estado|Significado|  
|-----------------|-------------|  
|200|Después de la transmisión en la dirección URL que se encuentra,|  
|400|Solicitud ininteligible|  
|404|Solicitado no se encontró la dirección URL|  
|405|Servidor no admite el método solicitado|  
|500|Error desconocido del servidor|  
|503|Se alcanzó la capacidad de servidor|  
  
##  <a name="sendrequest"></a>CHttpFile:: SendRequest  
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
 `pstrHeaders`  
 Un puntero a una cadena que contiene el nombre de los encabezados para enviar.  
  
 `dwHeadersLen`  
 La longitud de los encabezados que se identifica mediante `pstrHeaders`.  
  
 `lpOptional`  
 Los datos opcionales para enviar inmediatamente después de los encabezados de solicitud. Esto se suele utilizar para **POST** y **colocar** operaciones. Esto puede ser **NULL** si no hay ningún dato opcional para enviar.  
  
 *dwOptionalLen*  
 Longitud de `lpOptional`.  
  
 `strHeaders`  
 Una cadena que contiene el nombre de los encabezados de la solicitud que se envían.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, determinar la causa del error examinando el produce [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto.  
  
##  <a name="sendrequestex"></a>CHttpFile::SendRequestEx  
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
 *dwTotalLen*  
 Número de bytes que se envían en la solicitud.  
  
 `dwFlags`  
 Marcas que describen la operación. Para obtener una lista de las marcas apropiadas, consulte [HttpSendRequestEx](http://msdn.microsoft.com/library/windows/desktop/aa384318) en el SDK de Windows.  
  
 `dwContext`  
 Identificador de contexto para la operación `CHttpFile`. Vea la sección Comentarios para obtener más información acerca de este parámetro.  
  
 `lpBuffIn`  
 Puntero a un inicializado [INTERNET_BUFFERS](http://msdn.microsoft.com/library/windows/desktop/aa385132) que describe el búfer de entrada que se utiliza para la operación.  
  
 *lpBuffOut*  
 Puntero a un inicializado **INTERNET_BUFFERS** que describe el búfer de salida que se utiliza para la operación.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente. Si se produce un error en la llamada, determinar la causa del error examinando el produce [CInternetException](../../mfc/reference/cinternetexception-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función permite a la aplicación enviar datos mediante el [escribir](../../mfc/reference/cinternetfile-class.md#write) y [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) métodos de `CInternetFile`. Debe conocer la longitud de los datos que se va a enviar antes de llamar a cualquier invalidación de esta función. La invalidación de la primera permite especificar la longitud de datos que le gustaría enviar. La invalidación de la segunda acepta punteros a **INTERNET_BUFFERS** estructuras, lo que pueden utilizarse para describir el búfer con gran detalle.  
  
 Después de contenido se escribe en el archivo, llame a [EndRequest](#endrequest) para finalizar la operación.  
  
 El valor predeterminado de `dwContext` se envía por MFC para la `CHttpFile` objeto desde el [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto que creó el `CHttpFile` objeto. Cuando se llama a [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) o [CHttpConnection](../../mfc/reference/chttpconnection-class.md) para construir un `CHttpFile` de objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve al [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Vea el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.  
  
### <a name="example"></a>Ejemplo  
 Este fragmento de código, envía el contenido de una cadena a un archivo DLL denominado MFCISAPI. DLL en el servidor de host local. Aunque este ejemplo utiliza sólo una llamada a `WriteString`, el uso de varias llamadas para enviar datos en bloques es aceptable.  
  
 [!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile (clase)](../../mfc/reference/cgopherfile-class.md)   
 [CHttpConnection (clase)](../../mfc/reference/chttpconnection-class.md)
