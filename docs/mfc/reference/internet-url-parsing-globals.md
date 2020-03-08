---
title: Aplicaciones auxiliares y globales de análisis de direcciones URL de Internet
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 310e4ffb3fc207d874e97ba1fac65f6f8cb41a31
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865813"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Aplicaciones auxiliares y globales de análisis de direcciones URL de Internet

Cuando un cliente envía una consulta al servidor de Internet, puede usar una de las variables globales de análisis de direcciones URL para extraer información sobre el cliente. Las funciones auxiliares proporcionan otras funciones de Internet.

## <a name="internet-url-parsing-globals"></a>Variables globales de análisis de direcciones URL de Internet

|||
|-|-|
|[AfxParseURL](#afxparseurl)|Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes.|
|[AfxParseURLEx](#afxparseurlex)|Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes, así como para proporcionar el nombre de usuario y la contraseña.|

## <a name="other-internet-helpers"></a>Otras aplicaciones auxiliares de Internet

|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|Produce una excepción relacionada con la conexión a Internet.|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|Determina el tipo de un identificador de Internet.|

##  <a name="afxparseurl"></a>AfxParseURL

Este global se usa en [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

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
Primer segmento de la dirección URL que sigue al tipo de servicio.

*strObject*<br/>
Objeto al que hace referencia la dirección URL (puede estar vacío).

*nPort*<br/>
Se determina a partir de las partes del servidor o del objeto de la dirección URL, si existe.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la dirección URL se analizó correctamente; de lo contrario, es 0 si está vacío o no contiene un tipo de servicio de Internet conocido.

### <a name="remarks"></a>Observaciones

Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes.

Por ejemplo, `AfxParseURL` analiza las direcciones URL con el formato *Service://Server/dir/dir/Object.EXT:Port* y devuelve sus componentes almacenados de la siguiente manera:

*strServer* = = "servidor"

*strObject* = = "/dir/dir/Object/Object.ext"

*nPort* = = #port

*dwServiceType* = = #service

> [!NOTE]
>  Para llamar a esta función, el proyecto debe incluir AFXINET. C.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxinet. h

##  <a name="afxparseurlex"></a>AfxParseURLEx

Esta función global es la versión extendida de [AfxParseURL](#afxparseurl) y se usa en [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

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
Primer segmento de la dirección URL que sigue al tipo de servicio.

*strObject*<br/>
Objeto al que hace referencia la dirección URL (puede estar vacío).

*nPort*<br/>
Se determina a partir de las partes del servidor o del objeto de la dirección URL, si existe.

*strUsername*<br/>
Referencia a un objeto `CString` que contiene el nombre del usuario.

*strPassword*<br/>
Referencia a un objeto `CString` que contiene la contraseña del usuario.

*dwFlags*<br/>
Marcas que controlan cómo analizar la dirección URL. Puede ser una combinación de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|ICU_DECODE|Convierta% XX secuencias de escape en caracteres.|
|ICU_NO_ENCODE|No convierta los caracteres no seguros en una secuencia de escape.|
|ICU_NO_META|No quite las secuencias meta (como "\". y "\..") desde la dirección URL.|
|ICU_ENCODE_SPACES_ONLY|Codificar solo los espacios.|
|ICU_BROWSER_MODE|No codifique ni descodifique caracteres después de ' # ' o ' ' y no quite los espacios en blanco finales después de ' '. Si no se especifica este valor, la dirección URL completa se codifica y se quita el espacio en blanco final.|

Si usa el valor predeterminado de MFC, que no es ninguna marca, la función convierte todos los caracteres no seguros y las secuencias meta (como \\., \... y \\...) en secuencias de escape.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la dirección URL se analizó correctamente; de lo contrario, es 0 si está vacío o no contiene un tipo de servicio de Internet conocido.

### <a name="remarks"></a>Observaciones

Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes, así como el nombre y la contraseña del usuario. Las marcas indican cómo se administran los caracteres no seguros.

> [!NOTE]
>  Para llamar a esta función, el proyecto debe incluir AFXINET. C.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxinet. h

## <a name="afxgetinternethandletype"></a>AfxGetInternetHandleType

Use esta función global para determinar el tipo de un identificador de Internet.

### <a name="syntax"></a>Sintaxis

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>Parámetros

*hQuery*<br/>
Identificador de una consulta de Internet.

### <a name="return-value"></a>Valor devuelto

Cualquiera de los tipos de servicio de Internet definidos por WININET. C. Vea la sección Comentarios para obtener una lista de estos servicios de Internet. Si el identificador es NULL o no se reconoce, la función devuelve AFX_INET_SERVICE_UNK.

### <a name="remarks"></a>Observaciones

La lista siguiente incluye los posibles tipos de Internet devueltos por `AfxGetInternetHandleType`.

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
>  Para llamar a esta función, el proyecto debe incluir AFXINET. C.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxinet. h

## <a name="afxthrowinternetexception"></a>AfxThrowInternetException

Produce una excepción de Internet.

### <a name="syntax"></a>Sintaxis

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>Parámetros

*dwContext*<br/>
Identificador de contexto para la operación que produjo el error. El valor predeterminado de *dwContext* se especifica originalmente en [CInternetSession](cinternetsession-class.md) y se pasa a las clases derivadas [CInternetConnection](cinternetconnection-class.md)y [CInternetFile](cinternetfile-class.md). En el caso de las operaciones específicas realizadas en una conexión o un archivo, normalmente se invalida el valor predeterminado con un *dwContext* propio. Este valor se devuelve a [CInternetSession:: OnStatusCallback](cinternetsession-class.md#onstatuscallback) para identificar el estado de la operación específica.

*dwError*<br/>
El error que provocó la excepción.

### <a name="remarks"></a>Observaciones

Usted es responsable de determinar la causa en función del código de error del sistema operativo.

> [!NOTE]
>  Para llamar a esta función, el proyecto debe incluir AFXINET. C.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxinet. h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](mfc-macros-and-globals.md)<br/>
[CInternetException (clase)](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
