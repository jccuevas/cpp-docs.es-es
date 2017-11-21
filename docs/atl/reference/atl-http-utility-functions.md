---
title: Funciones de la utilidad de ATL HTTP | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 9cdb12373d93c17258fb615f667d7321e06f6728
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="atl-http-utility-functions"></a>Funciones de utilidad de HTTP de ATL

Estas funciones admiten la manipulación de direcciones URL.

|||  
|-|-|  
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Convierte una dirección URL, que incluye la conversión de espacios y caracteres no seguros en secuencias de escape en formato canónico.|  
|[AtlCombineUrl](#atlcombineurl)|Combina una dirección URL base y una dirección URL relativa en una única dirección de URL canónica.|  
|[AtlEscapeUrl](#atlescapeurl)|Convierte todos los caracteres no seguros en secuencias de escape.|  
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|Obtiene el número de puerto predeterminado asociado a un determinado protocolo de Internet o un esquema.|  
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|Determina si un carácter es seguro para su uso en una dirección URL.|  
|[AtlUnescapeUrl](#atlunescapeurl)|Convierte los caracteres de escape a sus valores originales.|  
|[RGBToHtml](#rgbtohtml)|Convierte un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor para el texto HTLM correspondiente a ese valor de color.|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|Llame a esta función para convertir una hora del sistema en una cadena con un formato adecuado para usarla en encabezados HTTP.|

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  

## <a name="atlcanonicalizeurl"></a>AtlCanonicalizeUrl
Llame a esta función para canonizar una dirección URL, que incluye la conversión de espacios y caracteres no seguros en secuencias de escape.  
  
```    
inline BOOL AtlCanonicalizeUrl(  
   LPCTSTR szUrl,  
   LPTSTR szCanonicalized,  
   DWORD* pdwMaxLength,  
   DWORD dwFlags = 0) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 `szUrl`  
 La dirección URL que puede dar formato canónico.  
  
 `szCanonicalized`  
 Búfer asignado por el autor de llamada para recibir la dirección URL con formato canónico.  
  
 `pdwMaxLength`  
 Puntero a una variable que contiene la longitud en caracteres de `szCanonicalized`. Si la función se realiza correctamente, la variable recibe el número de caracteres escritos en el búfer incluido el carácter nulo final. Si se produce un error en la función, la variable recibe la longitud requerida en bytes del búfer, incluido el espacio para el carácter nulo de terminación.  
  
 `dwFlags`  
 Indicadores ATL_URL que controlan el comportamiento de esta función. 

- `ATL_URL_BROWSER_MODE`No se codifican o descodifican caracteres después de "#" o "?" y no quita los espacios en blanco finales después de "?". Si no se especifica este valor, se codifica la dirección URL completa y se quita el espacio en blanco final.
- `ATL_URL_DECODE`Convierte todas las secuencias XX % a caracteres, incluidas las secuencias de escape, antes de que se analiza la dirección URL.
- `ATL_URL_ENCODE_PERCENT`Codifica los signos de porcentaje encontrados. De forma predeterminada, no se codifican los signos de porcentaje.
- `ATL_URL_ENCODE_SPACES_ONLY`Codifica solo espacios.
- `ATL_URL_ESCAPE`Convierte todas las secuencias de escape (% XX) en sus caracteres correspondientes.
- `ATL_URL_NO_ENCODE`No convierte los caracteres no seguros en secuencias de escape.
- `ATL_URL_NO_META`No se quitan las secuencias de metadatos (como "."y"..") de la dirección URL. 
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Se comporta como la versión actual de [InternetCanonicalizeUrl](http://msdn.microsoft.com/library/windows/desktop/aa384342) , pero no requiere WinInet o Internet Explorer para instalarse.  
  
### <a name="see-also"></a>Vea también  
 [InternetCanonicalizeUrl](http://msdn.microsoft.com/library/windows/desktop/aa384342)

 ## <a name="atlcombineurl"></a>AtlCombineUrl
 Llame a esta función para combinar una dirección URL base y una dirección URL relativa en una única dirección URL canónica.  
  
```    
inline BOOL AtlCombineUrl(  
   LPCTSTR szBaseUrl,  
   LPCTSTR szRelativeUrl,  
   LPTSTR szBuffer,  
   DWORD* pdwMaxLength,  
   DWORD dwFlags = 0) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 *szBaseUrl*  
 La dirección URL base.  
  
 *szRelativeUrl*  
 La dirección URL relativa a la dirección URL base.  
  
 `szBuffer`  
 Búfer asignado por el autor de llamada para recibir la dirección URL con formato canónico.  
  
 `pdwMaxLength`  
 Puntero a una variable que contiene la longitud en caracteres de `szBuffer`. Si la función se realiza correctamente, la variable recibe el número de caracteres escritos en el búfer incluido el carácter nulo final. Si se produce un error en la función, la variable recibe la longitud requerida en bytes del búfer, incluido el espacio para el carácter nulo de terminación.  
  
 `dwFlags`  
 Indicadores que controlan el comportamiento de esta función. Vea [AtlCanonicalizeUrl](#atlcanonicalizeurl).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Se comporta como la versión actual de [InternetCombineUrl](http://msdn.microsoft.com/library/windows/desktop/aa384355) , pero no requiere WinInet o Internet Explorer para instalarse.  
  
## <a name="atlescapeurl"></a>AtlEscapeUrl
 Llame a esta función para convertir todos los caracteres no seguros en secuencias de escape.  
  
```    
inline BOOL AtlEscapeUrl(  
   LPCSTR szStringIn,  
   LPSTR szStringOut,  
   DWORD* pdwStrLen,  
   DWORD dwMaxLength,  
   DWORD dwFlags = 0) throw();  
   
inline BOOL AtlEscapeUrl(  
   LPCWSTR szStringIn,  
   LPWSTR szStringOut,  
   DWORD* pdwStrLen,  
   DWORD dwMaxLength,  
   DWORD dwFlags = 0) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszStringIn`  
 La dirección URL que se va a convertir.  
  
 `lpszStringOut`  
 Búfer asignado por el autor de la llamada a la que se escribirá la URL convertida.  
  
 `pdwStrLen`  
 Puntero a una variable DWORD. Si la función se realiza correctamente, `pdwStrLen` recibe el número de caracteres escritos en el búfer incluido el carácter nulo final. Si se produce un error en la función, la variable recibe la longitud requerida en bytes del búfer, incluido el espacio para el carácter nulo de terminación. Cuando se usa la versión de caracteres anchos de este método, `pdwStrLen` recibe el número de caracteres necesarios, no el número de bytes.  
  
 `dwMaxLength`  
 El tamaño del búfer `lpszStringOut`.  
  
 `dwFlags`  
 Indicadores ATL_URL que controlan el comportamiento de esta función. Vea [ATLCanonicalizeUrl](#atlcanonicalizeurl) para los valores posibles.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
## <a name="atlgetdefaulturlport"></a> 
 Llame a esta función para obtener el número de puerto predeterminado asociado a un protocolo de Internet o un esquema específicos.  
  
```  
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 *m_nScheme*  
 El [ATL_URL_SCHEME](atl-url-scheme-enum.md) valor que identifica el esquema para el que desea obtener el número de puerto.  
  
### <a name="return-value"></a>Valor devuelto  
 El [ATL_URL_PORT](atl-typedefs.md#atl_url_port) asociado con el esquema especificado o ATL_URL_INVALID_PORT_NUMBER si no se reconoce el esquema.  

## <a name="atlisunsafeurlchar"></a>AtlIsUnsafeUrlChar
 Llame a esta función para comprobar si un carácter es seguro para usarlo en una dirección URL.  
  
```  
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 `chIn`  
 El carácter que se va a realizar una comprobación de seguridad.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** si el carácter de entrada no es seguro, **FALSE** en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Caracteres que no deben usarse en las direcciones URL se pueda comprobar mediante esta función y para convertir mediante [AtlCanonicalizeUrl](#atlcanonicalizeurl).  
  
## <a name="atlunescapeurl"></a>AtlUnescapeUrl
 Llame a esta función para convertir de nuevo los caracteres de escape en sus valores originales.  
  
```    
inline BOOL AtlUnescapeUrl(  
   LPCSTR szStringIn,  
   LPSTR szStringOut,  
   LPDWORD pdwStrLen,  
   DWORD dwMaxLength) throw();  

inline BOOL AtlUnescapeUrl(  
   LPCWSTR szStringIn,  
   LPWSTR szStringOut,  
   LPDWORD pdwStrLen,  
   DWORD dwMaxLength) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszStringIn`  
 La dirección URL que se va a convertir.  
  
 `lpszStringOut`  
 Búfer asignado por el autor de la llamada a la que se escribirá la URL convertida.  
  
 `pdwStrLen`  
 Puntero a una variable DWORD. Si la función se realiza correctamente, la variable recibe el número de caracteres escritos en el búfer incluido el carácter nulo final. Si se produce un error en la función, la variable recibe la longitud requerida en bytes del búfer, incluido el espacio para el carácter nulo de terminación.  
  
 `dwMaxLength`  
 El tamaño del búfer `lpszStringOut`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Invierte el proceso de conversión aplicado [AtlEscapeUrl](#atlescapeurl).  
  
## <a name="rgbtohtml"></a>RGBToHtml
Convierte un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor para el texto HTLM correspondiente a ese valor de color.  
  
```  
bool inline RGBToHtml(  
   COLORREF color,  
   LPTSTR pbOut,  
   long nBuffer);  
```  
  
### <a name="parameters"></a>Parámetros  
 `color`  
 Un valor de color RGB.  
  
 `pbOut`  
 Búfer asignado por el llamador que recibe el texto para el valor de color HTML. El búfer debe tener espacio para al menos 8 caracteres, incluido el espacio para el terminador nulo).  
  
 *nBuffer*  
 El tamaño en bytes del búfer (incluido el espacio para el terminador nulo).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Un valor de color HTML es un signo de almohadilla seguido por un valor de 6 dígitos hexadecimal con 2 dígitos para cada uno de los componentes rojos, verde y azules del color (por ejemplo, es blanco #FFFFFF).  
  
## <a name="systemtimetohttpdate"></a>SystemTimeToHttpDate
Llame a esta función para convertir una hora del sistema en una cadena con un formato adecuado para usarla en encabezados HTTP.  
  
```  
inline void SystemTimeToHttpDate( 
   const SYSTEMTIME& st,  
   CStringA& strTime);  
```  
  
### <a name="parameters"></a>Parámetros  
 `st`  
 La hora del sistema a obtenerse como una cadena de formato HTTP.  
  
 *strTime*  
 Una referencia a una variable de cadena que recibirá el HTTP fecha y hora como se define en RFC 2616 ([http://www.ietf.org/rfc/rfc2616.txt](http://www.ietf.org/rfc/rfc2616.txt)) y RFC 1123 ([http://www.ietf.org/rfc/rfc1123.txt](http://www.ietf.org/rfc/rfc1123.txt)).  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../../atl/active-template-library-atl-concepts.md)   
 [Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)   

