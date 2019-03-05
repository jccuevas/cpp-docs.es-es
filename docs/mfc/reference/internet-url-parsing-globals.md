---
title: Las aplicaciones auxiliares y variables globales de análisis de direcciones URL de Internet
ms.date: 04/03/2017
f1_keywords:
- vc.mfc.macros.isapi
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 0831d94f1a6f0293d3605a5e2e9ebde0564baf24
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293477"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Las aplicaciones auxiliares y variables globales de análisis de direcciones URL de Internet

Cuando un cliente envía una consulta al servidor de Internet, puede usar uno de la dirección URL de funciones globales de análisis para extraer información sobre el cliente. Las funciones auxiliares proporcionan otras funcionalidades de internet.

## <a name="internet-url-parsing-globals"></a>Variables globales de análisis de direcciones URL de Internet

|||
|-|-|
|[AfxParseURL](#afxparseurl)|Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes.|
|[AfxParseURLEx](#afxparseurlex)|Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes, así como proporcionar el nombre de usuario y la contraseña.|

## <a name="other-internet-helpers"></a>Otras aplicaciones auxiliares de Internet

|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|Inicia una excepción relacionada con la conexión a internet.|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|Determina el tipo de un identificador de Internet.|

##  <a name="afxparseurl"></a>  AfxParseURL

Se usa este global en [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

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
Un puntero a una cadena que contiene la dirección URL que se puede analizar.

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
El primer segmento de la dirección URL siguiendo el tipo de servicio.

*strObject*<br/>
Un objeto que hace referencia la dirección URL (puede estar vacía).

*nPort*<br/>
Puede determinar desde el servidor o el objeto de partes de la dirección URL, si existe alguna.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la dirección URL se analizó correctamente; en caso contrario, 0 si no está vacío o no contiene un tipo de servicio conocido de Internet.

### <a name="remarks"></a>Comentarios

Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes.

Por ejemplo, `AfxParseURL` analiza las direcciones URL del formulario *service://server/dir/dir/object.ext:port* y devuelve sus componentes almacenados como sigue:

*strServer* == "server"

*strObject* == "/dir/dir/object/object.ext"

*nPort* == #port

*dwServiceType* == #service

> [!NOTE]
>  Para llamar a esta función, el proyecto debe incluir AFXINET. H.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxinet.h

##  <a name="afxparseurlex"></a>  AfxParseURLEx

Esta función global es la versión extendida de [AfxParseURL](#afxparseurl) y se utiliza en [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

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
Un puntero a una cadena que contiene la dirección URL que se puede analizar.

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
El primer segmento de la dirección URL siguiendo el tipo de servicio.

*strObject*<br/>
Un objeto que hace referencia la dirección URL (puede estar vacía).

*nPort*<br/>
Puede determinar desde el servidor o el objeto de partes de la dirección URL, si existe alguna.

*strUsername*<br/>
Una referencia a un `CString` objeto que contiene el nombre del usuario.

*strPassword*<br/>
Una referencia a un `CString` objeto que contiene la contraseña del usuario.

*dwFlags*<br/>
Las marcas de controlar cómo analizar la dirección URL. Puede ser una combinación de los siguientes valores:

|Valor|Significado|
|-----------|-------------|
|ICU_DECODE|Secuencias de escape % XX se convierten en caracteres.|
|ICU_NO_ENCODE|No se convierten los caracteres no seguros para la secuencia de escape.|
|ICU_NO_META|No quite las secuencias de metadatos (por ejemplo, "\". y "\..") desde la dirección URL.|
|ICU_ENCODE_SPACES_ONLY|Codificar solo espacios.|
|ICU_BROWSER_MODE|No se codifican o descodifican caracteres tras '#' o '', sin quitar los espacios en blanco finales después ''. Si no se especifica este valor, se codifica la dirección URL completa y se quita el espacio en blanco final.|

Si usa el valor predeterminado MFC, que se encuentra ninguna marca, la función convierte todos los caracteres no seguros y las secuencias de metadatos (como \\., \.., y \\...) secuencias de escape.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la dirección URL se analizó correctamente; en caso contrario, 0 si no está vacío o no contiene un tipo de servicio conocido de Internet.

### <a name="remarks"></a>Comentarios

Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes, así como proporcionar el nombre y la contraseña del usuario. Los marcadores indican caracteres no seguros de cómo se controlan.

> [!NOTE]
>  Para llamar a esta función, el proyecto debe incluir AFXINET. H.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxinet.h

## <a name="afxgetinternethandletype"></a>  AfxGetInternetHandleType

Utilice esta función global para determinar el tipo de un identificador de Internet.

### <a name="syntax"></a>Sintaxis

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>Parámetros

*hQuery*<br/>
Identificador de una consulta de Internet.

### <a name="return-value"></a>Valor devuelto

Cualquiera de los tipos de servicio de Internet definidos por WININET. H. Consulte la sección Comentarios para obtener una lista de estos servicios de Internet. Si el identificador es NULL o no reconoce, la función devuelve AFX_INET_SERVICE_UNK.

### <a name="remarks"></a>Comentarios

La lista siguiente incluye los tipos posibles de Internet devueltos por `AfxGetInternetHandleType`.

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
>  Para poder llamar a esta función, el proyecto debe incluir AFXINET. H.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="afxthrowinternetexception"></a>  AfxThrowInternetException

Se produce una excepción de Internet.

### <a name="syntax"></a>Sintaxis

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>Parámetros

*dwContext*<br/>
El identificador de contexto para la operación que produjo el error. El valor predeterminado de *dwContext* especificado originalmente en [CInternetSession](cinternetsession-class.md) y se pasa a [CInternetConnection](cinternetconnection-class.md)- y [CInternetFile](cinternetfile-class.md)-las clases derivadas. Para operaciones específicas que puede realizadas en un archivo o una conexión, se suele reemplazar el valor predeterminado con un *dwContext* de su elección. Este valor, a continuación, se devuelve al [CInternetSession:: OnStatusCallback](cinternetsession-class.md#onstatuscallback) para identificar el estado de la operación específica.

*dwError*<br/>
El error que provocó la excepción.

### <a name="remarks"></a>Comentarios

Usted es responsable de determinar la causa según el código de error del sistema operativo.

> [!NOTE]
>  Para llamar a esta función, el proyecto debe incluir AFXINET. H.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](mfc-macros-and-globals.md)<br/>
[CInternetException (clase)](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
