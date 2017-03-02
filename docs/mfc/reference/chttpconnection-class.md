---
title: Clase de objeto CHttpConnection | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHttpConnection
dev_langs:
- C++
helpviewer_keywords:
- servers, connecting to
- protocols, HTTP
- connecting to servers, HTTP servers
- Internet protocols, HTTP
- HTTP connections
- Internet protocols
- CHttpConnection class
- HTTP servers, connecting to
- connecting to servers
- Internet connections, HTTP
- connections [C++], HTTP
- Internet server, HTTP
ms.assetid: a402b662-c445-4988-800d-c8278551babe
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 1b02a79cebbd73a05478887115646f0544f0a92d
ms.lasthandoff: 02/24/2017

---
# <a name="chttpconnection-class"></a>Clase de objeto CHttpConnection
Administra la conexión a un servidor HTTP.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CHttpConnection : public CInternetConnection  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CHttpConnection::CHttpConnection](#chttpconnection)|Crea un objeto `CHttpConnection`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CHttpConnection:: OpenRequest](#openrequest)|Se abre una solicitud HTTP.|  
  
## <a name="remarks"></a>Comentarios  
 HTTP es uno de los tres protocolos de servidor de Internet implementados por las clases WinInet de MFC.  
  
 La clase `CHttpConnection` contiene un constructor y una función de un miembro, [OpenRequest](#openrequest), que administra las conexiones a un servidor con un protocolo HTTP.  
  
 Para comunicarse con un servidor HTTP, primero debe crear una instancia de [CInternetSession](../../mfc/reference/cinternetsession-class.md)y, a continuación, cree una [objeto CHttpConnection](#_mfc_chttpconnection) objeto. No cree nunca un `CHttpConnection` objeto directamente; en su lugar, llame a [CInternetSession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection), que crea el `CHttpConnection` de objetos y devuelve un puntero a ella.  
  
 Para obtener más información acerca de cómo `CHttpConnection` funciona con otras clases de Internet de MFC, vea el artículo [programación para Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md). Para obtener más información sobre cómo conectarse a servidores con los otros dos admite protocolos de Internet, gopher y FTP, vea las clases [objeto CGopherConnection](../../mfc/reference/cgopherconnection-class.md) y [CFtpConnection](../../mfc/reference/cftpconnection-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CHttpConnection`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
  
##  <a name="a-namechttpconnectiona--chttpconnectionchttpconnection"></a><a name="chttpconnection"></a>CHttpConnection::CHttpConnection  
 Llama a esta función miembro para construir un `CHttpConnection` objeto.  
  
```  
CHttpConnection(
    CInternetSession* pSession,  
    HINTERNET hConnected,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext);

 
CHttpConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 1);

 
CHttpConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    DWORD dwFlags,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSession`  
 Un puntero a un [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto.  
  
 `hConnected`  
 Identificador de una conexión a Internet.  
  
 `pstrServer`  
 Puntero a una cadena que contiene el nombre del servidor.  
  
 `dwContext`  
 El identificador de contexto para la `CInternetConnection` objeto. Consulte **comentarios** para obtener más información acerca de `dwContext`.  
  
 `nPort`  
 El número que identifica el puerto de Internet para esta conexión.  
  
 `pstrUserName`  
 Puntero a una cadena terminada en null que especifica el nombre del usuario para iniciar sesión. Si **NULL**, el valor predeterminado es anónimo.  
  
 `pstrPassword`  
 Un puntero a una cadena terminada en null que especifica la contraseña que use para iniciar sesión. Si ambos `pstrPassword` y `pstrUserName` son **NULL**, la contraseña anónima predeterminada es el nombre de correo electrónico del usuario. Si `pstrPassword` es **NULL** (o una cadena vacía) pero `pstrUserName` no **NULL**, se utiliza una contraseña en blanco. En la tabla siguiente describe el comportamiento de las cuatro configuraciones posibles de `pstrUserName` y `pstrPassword`:  
  
|`pstrUserName`|`pstrPassword`|Nombre de usuario que se envía al servidor FTP|Contraseña que se envían al servidor FTP|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**NULL** o ""|**NULL** o ""|"anónimo"|Nombre de correo electrónico del usuario|  
|No- **NULL** cadena|**NULL** o ""|`pstrUserName`|" "|  
|**NULL** no **NULL** cadena|**ERROR**|**ERROR**||  
|No- **NULL** cadena|No- **NULL** cadena|`pstrUserName`|`pstrPassword`|  
  
 `dwFlags`  
 Cualquier combinación de los **INTERNET_ FLAG_\* ** marcas. Consulte la tabla en la **comentarios** sección de [CHttpConnection:: OpenRequest](#openrequest) para obtener una descripción de `dwFlags` valores.  
  
### <a name="remarks"></a>Comentarios  
 No cree nunca un `CHttpConnection` directamente. En su lugar, se crea un objeto mediante una llamada a [CInternetSession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection).  
  
##  <a name="a-nameopenrequesta--chttpconnectionopenrequest"></a><a name="openrequest"></a>CHttpConnection:: OpenRequest  
 Llame a esta función miembro para abrir una conexión HTTP.  
  
```  
CHttpFile* OpenRequest(
    LPCTSTR pstrVerb,  
    LPCTSTR pstrObjectName,  
    LPCTSTR pstrReferer = NULL,  
    DWORD_PTR dwContext = 1,  
    LPCTSTR* ppstrAcceptTypes = NULL,  
    LPCTSTR pstrVersion = NULL,  
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);

 
CHttpFile* OpenRequest(
    int nVerb,  
    LPCTSTR pstrObjectName,  
    LPCTSTR pstrReferer = NULL,  
    DWORD_PTR dwContext = 1,  
    LPCTSTR* ppstrAcceptTypes = NULL,  
    LPCTSTR pstrVersion = NULL,  
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);
```  
  
### <a name="parameters"></a>Parámetros  
 `pstrVerb`  
 Puntero a una cadena que contiene el verbo que se va a utilizar en la solicitud. Si es `NULL`, se utiliza "GET".  
  
 `pstrObjectName`  
 Puntero a una cadena que contiene el objeto de destino del verbo especificado. Suele ser un nombre de archivo, un módulo ejecutable o un especificador de búsqueda.  
  
 `pstrReferer`  
 Un puntero a una cadena que especifica la dirección (URL) del documento desde el que la dirección URL de la solicitud ( `pstrObjectName`) se ha obtenido. Si es `NULL`, no se especifica ningún encabezado HTTP.  
  
 `dwContext`  
 Identificador de contexto para la operación `OpenRequest`. Vea la sección Comentarios para obtener más información sobre `dwContext`.  
  
 `ppstrAcceptTypes`  
 Puntero a una matriz terminada en null de punteros `LPCTSTR` a cadenas que indican los tipos de contenido que acepta el cliente. Si `ppstrAcceptTypes` es `NULL`, los servidores interpretan que el cliente solo acepta documentos de tipo “text/*” (es decir, solo documentos de texto y no imágenes u otros archivos binarios). El tipo de contenido es equivalente a la variable CONTENT_TYPE de CGI, que identifica el tipo de datos para las consultas que tienen información adjunta, como HTTP POST y PUT.  
  
 `pstrVersion`  
 Puntero a una cadena que define la versión de HTTP. Si es `NULL`, se utiliza "HTTP/1.0".  
  
 `dwFlags`  
 Cualquier combinación de las marcas INTERNET_ FLAG_*. Vea la sección Comentarios para obtener una descripción de los valores posibles de `dwFlags`.  
  
 `nVerb`  
 Número asociado al tipo de solicitud HTTP. Puede ser uno de los siguientes:  
  
|Tipo de solicitud HTTP|Valor de `nVerb`|  
|-----------------------|-------------------|  
|`HTTP_VERB_POST`|0|  
|`HTTP_VERB_GET`|1|  
|`HTTP_VERB_HEAD`|2|  
|`HTTP_VERB_PUT`|3|  
|`HTTP_VERB_LINK`|4|  
|`HTTP_VERB_DELETE`|5|  
|`HTTP_VERB_UNLINK`|6|  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [CHttpFile](../../mfc/reference/chttpfile-class.md) objeto solicitado.  
  
### <a name="remarks"></a>Comentarios  
 `dwFlags` puede ser una de las siguientes:  
  
|Marca de Internet|Descripción|  
|-------------------|-----------------|  
|`INTERNET_FLAG_RELOAD`|Fuerza una descarga del archivo, el objeto o el listado de directorio solicitado del servidor de origen, no de la memoria caché.|  
|`INTERNET_FLAG_DONT_CACHE`|No agrega la entidad devuelta a la memoria caché.|  
|`INTERNET_FLAG_MAKE_PERSISTENT`|Agrega la entidad devuelta a la memoria caché como una entidad persistente. Esto significa que las operaciones estándar de limpieza de caché, comprobación de coherencia o recolección de elementos no utilizados no pueden quitar este elemento de la memoria caché.|  
|`INTERNET_FLAG_SECURE`|Usa semántica de transacción segura. Esto se traduce en utilizar SSL/PCT y solo es significativo en solicitudes HTTP|  
|`INTERNET_FLAG_NO_AUTO_REDIRECT`|Sólo se utiliza con HTTP, especifica que redirecciones no se deben controlar automáticamente en [CHttpFile:: SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|  
  
 Reemplace el valor predeterminado de `dwContext` para establecer el identificador de contexto en un valor que desee. El identificador de contexto está asociado a esta operación específica de la `CHttpConnection` objeto creado por su [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto. El valor se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con el que se identifica. Consulte el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.  
  
 Se pueden producir excepciones con esta función.  
  
## <a name="see-also"></a>Vea también  
 [CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)   
 [Clase CHttpFile](../../mfc/reference/chttpfile-class.md)

