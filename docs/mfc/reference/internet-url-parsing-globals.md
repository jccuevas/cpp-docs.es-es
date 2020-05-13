---
title: Internet URL Análisis Globales y Ayudantes
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 742b381ecb55c433d0f384174b7612fcc21e9716
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356619"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Internet URL Análisis Globales y Ayudantes

Cuando un cliente envía una consulta al servidor de Internet, puede usar uno de los globales de análisis de direcciones URL para extraer información sobre el cliente. Las funciones auxiliares proporcionan otras funciones de Internet.

## <a name="internet-url-parsing-globals"></a>Variables globales de análisis de direcciones URL de Internet

|||
|-|-|
|[AfxParseURL](#afxparseurl)|Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes.|
|[AfxParseURLEx](#afxparseurlex)|Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes, además de proporcionar el nombre de usuario y la contraseña.|

## <a name="other-internet-helpers"></a>Otros ayudantes de Internet

|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|Produce una excepción relacionada con la conexión a Internet.|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|Determina el tipo de identificador de Internet.|

## <a name="afxparseurl"></a><a name="afxparseurl"></a>AfxParseURL

Este global se utiliza en [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

```
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort);
```

### <a name="parameters"></a>Parámetros

*pstrURL*<br/>
Puntero a una cadena que contiene la dirección URL que se va a analizar.

*dwServiceType*<br/>
Indica el tipo de servicio de Internet. Los valores posibles son los siguientes:

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer*<br/>
El primer segmento de la dirección URL que sigue al tipo de servicio.

*strObject*<br/>
Objeto al que hace referencia la dirección URL (puede estar vacío).

*Nport*<br/>
Determinado a partir de las partes Servidor u Objeto de la dirección URL, si existe cualquiera de ellas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la dirección URL se analizó correctamente; de lo contrario, 0 si está vacío o no contiene un tipo de servicio de Internet conocido.

### <a name="remarks"></a>Observaciones

Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes.

Por ejemplo, `AfxParseURL` analiza las direcciones URL del formulario *service://server/dir/dir/object.ext:port* y devuelve sus componentes almacenados de la siguiente manera:

*strServer* "servidor"

*strObject* "/dir/dir/object/object.ext"

*nPort* #port

*dwServiceType* #service

> [!NOTE]
> Para llamar a esta función, el proyecto debe incluir AFXINET. H.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxinet.h

## <a name="afxparseurlex"></a><a name="afxparseurlex"></a>AfxParseURLEx

Esta función global es la versión extendida de [AfxParseURL](#afxparseurl) y se utiliza en [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

```
BOOL AFXAPI AfxParseURLEx(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort,
    CString& strUsername,
    CString& strPassword,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parámetros

*pstrURL*<br/>
Puntero a una cadena que contiene la dirección URL que se va a analizar.

*dwServiceType*<br/>
Indica el tipo de servicio de Internet. Los valores posibles son los siguientes:

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer*<br/>
El primer segmento de la dirección URL que sigue al tipo de servicio.

*strObject*<br/>
Objeto al que hace referencia la dirección URL (puede estar vacío).

*Nport*<br/>
Determinado a partir de las partes Servidor u Objeto de la dirección URL, si existe cualquiera de ellas.

*strUsername*<br/>
Una referencia `CString` a un objeto que contiene el nombre del usuario.

*strPassword*<br/>
Una referencia `CString` a un objeto que contiene la contraseña del usuario.

*dwFlags*<br/>
Las marcas que controlan cómo analizar la dirección URL. Puede ser una combinación de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|ICU_DECODE|Convierta secuencias de escape %XX en caracteres.|
|ICU_NO_ENCODE|No convierta caracteres no seguros en secuencia de escape.|
|ICU_NO_META|No elimine las metasecuencias (por ejemplo, ". y "..") desde la URL.|
|ICU_ENCODE_SPACES_ONLY|Codifique solo espacios.|
|ICU_BROWSER_MODE|No codifique ni descodificar los caracteres después de '' o '', y no elimine el espacio en blanco final después de ''. Si no se especifica este valor, se codifica toda la dirección URL y se quita el espacio en blanco final.|

Si utiliza el valor predeterminado de MFC, que no es ninguna marca, la \\función convierte todos \\los caracteres no seguros y las secuencias meta (como . , .., y ...) en secuencias de escape.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la dirección URL se analizó correctamente; de lo contrario, 0 si está vacío o no contiene un tipo de servicio de Internet conocido.

### <a name="remarks"></a>Observaciones

Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes, además de proporcionar el nombre y la contraseña del usuario. Las marcas indican cómo se controlan los caracteres no seguros.

> [!NOTE]
> Para llamar a esta función, el proyecto debe incluir AFXINET. H.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxinet.h

## <a name="afxgetinternethandletype"></a><a name="afxgetinternethandletype"></a>AfxGetInternetHandleType

Utilice esta función global para determinar el tipo de identificador de Internet.

### <a name="syntax"></a>Sintaxis

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>Parámetros

*hQuery*<br/>
Identificador de una consulta de Internet.

### <a name="return-value"></a>Valor devuelto

Cualquiera de los tipos de servicio de Internet definidos por WININET. H. Consulte la sección Comentarios para obtener una lista de estos servicios de Internet. Si el identificador es NULL o no se reconoce, la función devuelve AFX_INET_SERVICE_UNK.

### <a name="remarks"></a>Observaciones

La siguiente lista incluye los `AfxGetInternetHandleType`posibles tipos de Internet devueltos por .

- INTERNET_HANDLE_TYPE_INTERNET

- INTERNET_HANDLE_TYPE_CONNECT_FTP

- INTERNET_HANDLE_TYPE_CONNECT_GOPHER

- INTERNET_HANDLE_TYPE_CONNECT_HTTP

- INTERNET_HANDLE_TYPE_FTP_FIND

- INTERNET_HANDLE_TYPE_FTP_FIND_HTML

- INTERNET_HANDLE_TYPE_FTP_FILE

- INTERNET_HANDLE_TYPE_FTP_FILE_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FIND

- INTERNET_HANDLE_TYPE_GOPHER_FIND_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FILE

- INTERNET_HANDLE_TYPE_GOPHER_FILE_HTML

- INTERNET_HANDLE_TYPE_HTTP_REQUEST

> [!NOTE]
> Para llamar a esta función, el proyecto debe incluir AFXINET. H.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="afxthrowinternetexception"></a><a name="afxthrowinternetexception"></a>AfxThrowInternetException

Produce una excepción de Internet.

### <a name="syntax"></a>Sintaxis

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>Parámetros

*dwContext*<br/>
Identificador de contexto para la operación que causó el error. El valor predeterminado de *dwContext* se especifica originalmente en [CInternetSession](cinternetsession-class.md) y se pasa a [CInternetConnection](cinternetconnection-class.md)- y [CInternetFile](cinternetfile-class.md)-clases derivadas. Para operaciones específicas realizadas en una conexión o un archivo, normalmente se reemplaza el valor predeterminado con un *dwContext* propio. Este valor, a continuación, se devuelve a [CInternetSession::OnStatusCallback](cinternetsession-class.md#onstatuscallback) para identificar el estado de la operación específica.

*dwError*<br/>
Error que causó la excepción.

### <a name="remarks"></a>Observaciones

Usted es responsable de determinar la causa en función del código de error del sistema operativo.

> [!NOTE]
> Para llamar a esta función, el proyecto debe incluir AFXINET. H.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](mfc-macros-and-globals.md)<br/>
[CInternetException (clase)](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
