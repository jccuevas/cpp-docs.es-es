---
title: Variables globales de análisis de direcciones URL de Internet y aplicaciones auxiliares | Documentos de Microsoft
ms.custom: ''
ms.date: 04/03/2017
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.isapi
dev_langs:
- C++
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02b7ea1a6d22d3e16230acafa25c53f8748a825a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374807"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Los ayudantes y variables globales de análisis de direcciones URL de Internet
Cuando un cliente envía una consulta al servidor de Internet, puede utilizar una de la direcciones URL variables globales de análisis para extraer información sobre el cliente. Las funciones auxiliares proporcionan otras funciones de internet.
  
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
 Se utiliza este global en [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
```   
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,  
    DWORD& dwServiceType,  
    CString& strServer,  
    CString& strObject,  
    INTERNET_PORT& nPort); 
```  
  
### <a name="parameters"></a>Parámetros  
 *pstrURL*  
 Un puntero a una cadena que contiene la dirección URL para analizarse.  
  
 `dwServiceType`  
 Indica el tipo de servicio de Internet. Los valores posibles son los siguientes:  
  
-   AFX_INET_SERVICE_FTP  
  
-   AFX_INET_SERVICE_HTTP  
  
-   AFX_INET_SERVICE_HTTPS  
  
-   AFX_INET_SERVICE_GOPHER  
  
-   AFX_INET_SERVICE_FILE  
  
-   AFX_INET_SERVICE_MAILTO  
  
-   AFX_INET_SERVICE_NEWS  
  
-   AFX_INET_SERVICE_NNTP  
  
-   AFX_INET_SERVICE_TELNET  
  
-   AFX_INET_SERVICE_WAIS  
  
-   AFX_INET_SERVICE_MID  
  
-   AFX_INET_SERVICE_CID  
  
-   AFX_INET_SERVICE_PROSPERO  
  
-   AFX_INET_SERVICE_AFS  
  
-   AFX_INET_SERVICE_UNK  
  
 `strServer`  
 El primer segmento de la dirección URL siguiendo el tipo de servicio.  
  
 `strObject`  
 Un objeto que hace referencia la dirección URL (puede estar vacía).  
  
 `nPort`  
 Determina de partes del servidor o el objeto de la dirección URL, si existe alguna.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la dirección URL se analizó correctamente; en caso contrario, 0 si no está vacío o no contiene un tipo de servicio conocido de Internet.  
  
### <a name="remarks"></a>Comentarios  
 Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes.  
  
 Por ejemplo, `AfxParseURL` analiza las direcciones URL del formulario **service://server/dir/dir/object.ext:port** y devuelve sus componentes que se almacenan como sigue:  
  
 `strServer` == "server"  
  
 `strObject` == "/ dir/dir/object/object.ext"  
  
 `nPort` == #port  
  
 `dwServiceType` == #service  
  
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
 *pstrURL*  
 Un puntero a una cadena que contiene la dirección URL para analizarse.  
  
 `dwServiceType`  
 Indica el tipo de servicio de Internet. Los valores posibles son los siguientes:  
  
-   AFX_INET_SERVICE_FTP  
  
-   AFX_INET_SERVICE_HTTP  
  
-   AFX_INET_SERVICE_HTTPS  
  
-   AFX_INET_SERVICE_GOPHER  
  
-   AFX_INET_SERVICE_FILE  
  
-   AFX_INET_SERVICE_MAILTO  
  
-   AFX_INET_SERVICE_NEWS  
  
-   AFX_INET_SERVICE_NNTP  
  
-   AFX_INET_SERVICE_TELNET  
  
-   AFX_INET_SERVICE_WAIS  
  
-   AFX_INET_SERVICE_MID  
  
-   AFX_INET_SERVICE_CID  
  
-   AFX_INET_SERVICE_PROSPERO  
  
-   AFX_INET_SERVICE_AFS  
  
-   AFX_INET_SERVICE_UNK  
  
 `strServer`  
 El primer segmento de la dirección URL siguiendo el tipo de servicio.  
  
 `strObject`  
 Un objeto que hace referencia la dirección URL (puede estar vacía).  
  
 `nPort`  
 Determina de partes del servidor o el objeto de la dirección URL, si existe alguna.  
  
 *strUsername*  
 Una referencia a un `CString` objeto que contiene el nombre del usuario.  
  
 `strPassword`  
 Una referencia a un `CString` objeto que contiene la contraseña del usuario.  
  
 `dwFlags`  
 Las marcas de controlar cómo analizar la dirección URL. Puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|**ICU_DECODE**|Convertir las secuencias de escape de % XX en caracteres.|  
|**ICU_NO_ENCODE**|No se convierten los caracteres no seguros para la secuencia de escape.|  
|**ICU_NO_META**|No quite las secuencias de metadatos (por ejemplo, "\". y "\"..) desde la dirección URL.|  
|**ICU_ENCODE_SPACES_ONLY**|Codificar solo espacios.|  
|**ICU_BROWSER_MODE**|No se codifican o descodifican caracteres tras '#' o '', sin quitar los espacios en blanco finales después ''. Si no se especifica este valor, se codifica la dirección URL completa y se quita el espacio en blanco final.|  
  
 Si utiliza el valor predeterminado MFC, que es no existen marcadores, la función convierte todos los caracteres no seguros y las secuencias de metadatos (como \\., \.., y \\...) como escape secuencias.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la dirección URL se analizó correctamente; en caso contrario, 0 si no está vacío o no contiene un tipo de servicio conocido de Internet.  
  
### <a name="remarks"></a>Comentarios  
 Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes, así como proporcionar el nombre y la contraseña del usuario. Los marcadores indican caracteres no seguros de cómo se administran.  
  
> [!NOTE]
>  Para llamar a esta función, el proyecto debe incluir AFXINET. H.  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxinet.h  
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
 
## <a name="afxgetinternethandletype"></a>  AfxGetInternetHandleType
Utilice esta función global para determinar el tipo de un identificador de Internet.  
   
### <a name="syntax"></a>Sintaxis  
  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );  
```
### <a name="parameters"></a>Parámetros  
 `hQuery`  
 Un identificador para una consulta de Internet.  
   
### <a name="return-value"></a>Valor devuelto  
 Cualquiera de los tipos de servicio de Internet definidos por WININET. H. Vea la sección Comentarios para obtener una lista de estos servicios de Internet. Si el identificador es NULL o no reconoce, la función devuelve AFX_INET_SERVICE_UNK.  
   
### <a name="remarks"></a>Comentarios  
 En la lista siguiente incluye los posibles tipos de Internet devueltos por `AfxGetInternetHandleType`.  
  
-   INTERNET_HANDLE_TYPE_INTERNET  
  
-   INTERNET_HANDLE_TYPE_CONNECT_FTP  
  
-   INTERNET_HANDLE_TYPE_CONNECT_GOPHER  
  
-   INTERNET_HANDLE_TYPE_CONNECT_HTTP  
  
-   INTERNET_HANDLE_TYPE_FTP_FIND  
  
-   INTERNET_HANDLE_TYPE_FTP_FIND_HTML  
  
-   INTERNET_HANDLE_TYPE_FTP_FILE  
  
-   INTERNET_HANDLE_TYPE_FTP_FILE_HTML  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FIND  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FIND_HTML  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FILE  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FILE_HTML  
  
-   INTERNET_HANDLE_TYPE_HTTP_REQUEST  
  
> [!NOTE]
>  Para poder llamar a esta función, el proyecto debe incluir AFXINET. H.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
 
## <a name="afxthrowinternetexception"></a>  AfxThrowInternetException
Produce una excepción de Internet.  
   
### <a name="syntax"></a>Sintaxis    
```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );  
```
### <a name="parameters"></a>Parámetros  
 `dwContext`  
 El identificador de contexto de la operación que produjo el error. El valor predeterminado de `dwContext` se especificó originalmente en [CInternetSession](cinternetsession-class.md) y se pasa a [CInternetConnection](cinternetconnection-class.md)- y [CInternetFile](cinternetfile-class.md)-las clases derivadas. Para operaciones específicas que se realiza en una conexión o un archivo, normalmente se invalida el valor predeterminado con un `dwContext` de su elección. Este valor, a continuación, se devuelve al [CInternetSession:: OnStatusCallback](cinternetsession-class.md#onstatuscallback) para identificar el estado de la operación específica. 
  
 `dwError`  
 El error que provocó la excepción.  
   
### <a name="remarks"></a>Comentarios  
 Usted es responsable de determinar la causa en función del código de error del sistema operativo.  
  
> [!NOTE]
>  Para llamar a esta función, el proyecto debe incluir AFXINET. H.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [Clase CInternetException](cinternetexception-class.md)   
 [THROW](#throw)
 

