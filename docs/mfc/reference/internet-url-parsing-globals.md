---
title: "Variables globales de análisis de direcciones URL de Internet | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.isapi
dev_langs:
- C++
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
caps.latest.revision: 14
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 3aec259acae2f5e9c9b65ac4e5c898ca57ff3d52
ms.lasthandoff: 02/24/2017

---
# <a name="internet-url-parsing-globals"></a>Variables globales de análisis de direcciones URL de Internet
Cuando un cliente envía una consulta al servidor de Internet, puede utilizar una de la direcciones URL variables globales de análisis para extraer información sobre el cliente.  
  
### <a name="internet-url-parsing-globals"></a>Variables globales de análisis de direcciones URL de Internet  
  
|||  
|-|-|  
|[AfxParseURL](#afxparseurl)|Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes.|  
|[AfxParseURLEx](#afxparseurlex)|Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes, así como proporcionar el nombre de usuario y la contraseña.|  
  
##  <a name="a-nameafxparseurla--afxparseurl"></a><a name="afxparseurl"></a>AfxParseURL  
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
 Un puntero a una cadena que contiene la URL que se va a analizar.  
  
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
 El primer segmento de la dirección URL siguiente el tipo de servicio.  
  
 `strObject`  
 Un objeto que hace referencia la dirección URL (puede estar vacía).  
  
 `nPort`  
 Determinado desde el servidor o el objeto de partes de la dirección URL, si existe alguna.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la dirección URL se analizó correctamente; de lo contrario, 0 si está vacío o no contiene un tipo de servicio conocido de Internet.  
  
### <a name="remarks"></a>Comentarios  
 Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes.  
  
 Por ejemplo, `AfxParseURL` analiza las direcciones URL del formulario **service://server/dir/dir/object.ext:port** y devuelve sus componentes almacenados como sigue:  
  
 `strServer`== "server"  
  
 `strObject`== "/ dir/dir/object/object.ext"  
  
 `nPort`== #port  
  
 `dwServiceType`== #service  
  
> [!NOTE]
>  Para llamar a esta función, el proyecto debe incluir AFXINET. H.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxinet.h  
  
##  <a name="a-nameafxparseurlexa--afxparseurlex"></a><a name="afxparseurlex"></a>AfxParseURLEx  
 Esta es la versión ampliada del [AfxParseURL](#afxparseurl) y se utiliza en [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
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
 Un puntero a una cadena que contiene la URL que se va a analizar.  
  
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
 El primer segmento de la dirección URL siguiente el tipo de servicio.  
  
 `strObject`  
 Un objeto que hace referencia la dirección URL (puede estar vacía).  
  
 `nPort`  
 Determinado desde el servidor o el objeto de partes de la dirección URL, si existe alguna.  
  
 *strUsername*  
 Una referencia a un `CString` objeto que contiene el nombre del usuario.  
  
 `strPassword`  
 Una referencia a un `CString` objeto que contiene la contraseña del usuario.  
  
 `dwFlags`  
 Las marcas de controlar cómo se analiza la dirección URL. Puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|**ICU_DECODE**|Convertir las secuencias de escape XX % a caracteres.|  
|**ICU_NO_ENCODE**|No se convierten los caracteres no seguros para la secuencia de escape.|  
|**ICU_NO_META**|No quite las secuencias de metadatos (por ejemplo, "\". y "\"..) desde la dirección URL.|  
|**ICU_ENCODE_SPACES_ONLY**|Codificar sólo espacios.|  
|**ICU_BROWSER_MODE**|No codificar o descodificar caracteres tras '#' o '' y no quite los espacios en blanco finales después de ''. Si no se especifica este valor, se codifica la dirección URL completa y se quita el espacio en blanco final.|  
  
 Si utiliza el valor predeterminado MFC, que no es ningún indicador, la función convierte todos los caracteres no seguros y las secuencias de metadatos (como \\., \.., y \\...) secuencias de escape.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la dirección URL se analizó correctamente; de lo contrario, 0 si está vacío o no contiene un tipo de servicio conocido de Internet.  
  
### <a name="remarks"></a>Comentarios  
 Analiza una cadena de dirección URL y devuelve el tipo de servicio y sus componentes, así como proporcionar el nombre y la contraseña del usuario. Los marcadores indican caracteres no seguros de cómo se controlan.  
  
> [!NOTE]
>  Para llamar a esta función, el proyecto debe incluir AFXINET. H.  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxinet.h  
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

