---
title: CUrl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CUrl
- ATLUTIL/ATL::CUrl
- ATLUTIL/ATL::CUrl::CUrl
- ATLUTIL/ATL::CUrl::Canonicalize
- ATLUTIL/ATL::CUrl::Clear
- ATLUTIL/ATL::CUrl::CrackUrl
- ATLUTIL/ATL::CUrl::CreateUrl
- ATLUTIL/ATL::CUrl::GetExtraInfo
- ATLUTIL/ATL::CUrl::GetExtraInfoLength
- ATLUTIL/ATL::CUrl::GetHostName
- ATLUTIL/ATL::CUrl::GetHostNameLength
- ATLUTIL/ATL::CUrl::GetPassword
- ATLUTIL/ATL::CUrl::GetPasswordLength
- ATLUTIL/ATL::CUrl::GetPortNumber
- ATLUTIL/ATL::CUrl::GetScheme
- ATLUTIL/ATL::CUrl::GetSchemeName
- ATLUTIL/ATL::CUrl::GetSchemeNameLength
- ATLUTIL/ATL::CUrl::GetUrlLength
- ATLUTIL/ATL::CUrl::GetUrlPath
- ATLUTIL/ATL::CUrl::GetUrlPathLength
- ATLUTIL/ATL::CUrl::GetUserName
- ATLUTIL/ATL::CUrl::GetUserNameLength
- ATLUTIL/ATL::CUrl::SetExtraInfo
- ATLUTIL/ATL::CUrl::SetHostName
- ATLUTIL/ATL::CUrl::SetPassword
- ATLUTIL/ATL::CUrl::SetPortNumber
- ATLUTIL/ATL::CUrl::SetScheme
- ATLUTIL/ATL::CUrl::SetSchemeName
- ATLUTIL/ATL::CUrl::SetUrlPath
- ATLUTIL/ATL::CUrl::SetUserName
dev_langs:
- C++
helpviewer_keywords:
- CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 323645a0949ddf6797f36ad9b530920ca24ffe44
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885694"
---
# <a name="curl-class"></a>CUrl (clase)
Esta clase representa una dirección URL. Permite manipular cada elemento de la dirección URL independientemente de los demás si una dirección URL existente de análisis de cadena o creación de una cadena desde el principio.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CUrl
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CUrl::CUrl](#curl)|El constructor.|  
|[CUrl:: ~ CUrl](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CUrl::Canonicalize](#canonicalize)|Llame a este método para convertir la cadena de dirección URL en forma canónica.|  
|[CUrl::Clear](#clear)|Llame a este método para borrar todos los campos de dirección URL.|  
|[CUrl::CrackUrl](#crackurl)|Llame a este método para descodificar y analizar la dirección URL.|  
|[CUrl::CreateUrl](#createurl)|Llame a este método para crear la dirección URL.|  
|[CUrl::GetExtraInfo](#getextrainfo)|Llame a este método para obtener información adicional (como *texto* o # *texto*) de la dirección URL.|  
|[CUrl::GetExtraInfoLength](#getextrainfolength)|Llame a este método para obtener la longitud de la información adicional (como *texto* o # *texto*) para recuperar de la dirección URL.|  
|[CUrl::GetHostName](#gethostname)|Llame a este método para obtener el nombre de host de la dirección URL.|  
|[CUrl::GetHostNameLength](#gethostnamelength)|Llame a este método para obtener la longitud del nombre de host.|  
|[CUrl::GetPassword](#getpassword)|Llame a este método para obtener la contraseña de la dirección URL.|  
|[CUrl::GetPasswordLength](#getpasswordlength)|Llame a este método para obtener la longitud de la contraseña.|  
|[CUrl::GetPortNumber](#getportnumber)|Llame a este método para obtener el número de puerto en cuanto a ATL_URL_PORT.|  
|[CUrl::GetScheme](#getscheme)|Llame a este método para obtener el esquema de dirección URL.|  
|[CUrl::GetSchemeName](#getschemename)|Llame a este método para obtener el nombre de esquema de dirección URL.|  
|[CUrl::GetSchemeNameLength](#getschemenamelength)|Llame a este método para obtener la longitud del nombre del esquema de dirección URL.|  
|[CUrl::GetUrlLength](#geturllength)|Llame a este método para obtener la longitud de la dirección URL.|  
|[CUrl::GetUrlPath](#geturlpath)|Llame a este método para obtener la ruta de acceso de dirección URL.|  
|[CUrl::GetUrlPathLength](#geturlpathlength)|Llame a este método para obtener la longitud de ruta de acceso de dirección URL.|  
|[CUrl::GetUserName](#getusername)|Llame a este método para obtener el nombre de usuario de la dirección URL.|  
|[CUrl::GetUserNameLength](#getusernamelength)|Llame a este método para obtener la longitud del nombre de usuario.|  
|[CUrl::SetExtraInfo](#setextrainfo)|Llame a este método para establecer la información adicional (como *texto* o # *texto*) de la dirección URL.|  
|[CUrl::SetHostName](#sethostname)|Llame a este método para establecer el nombre de host.|  
|[CUrl::SetPassword](#setpassword)|Llame a este método para establecer la contraseña.|  
|[CUrl::SetPortNumber](#setportnumber)|Llame a este método para establecer el número de puerto en cuanto a ATL_URL_PORT.|  
|[CUrl::SetScheme](#setscheme)|Llame a este método para establecer el esquema de dirección URL.|  
|[CUrl::SetSchemeName](#setschemename)|Llame a este método para establecer el nombre de esquema de dirección URL.|  
|[CUrl::SetUrlPath](#seturlpath)|Llame a este método para establecer la ruta de acceso de dirección URL.|  
|[CUrl::SetUserName](#setusername)|Llame a este método para establecer el nombre de usuario.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CUrl::operator =](#operator_eq)|Asigna especificado `CUrl` el objeto actual `CUrl` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CUrl` permite manipular los campos de una dirección URL, como el número de puerto o ruta de acceso. `CUrl` comprende las direcciones URL de la forma siguiente:  
  
 \<Esquema > ://\<UserName >:\<contraseña > @\<nombre de host >:\<PortNumber > /\<UrlPath >\<ExtraInfo >  
  
 (Algunos campos son opcionales). Por ejemplo, considere esta dirección URL:  
  
 http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents  
  
 [CUrl::CrackUrl](#crackurl) lo analiza como sigue:  
  
-   Esquema: "http" o [ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)  
  
-   Nombre de usuario: "someone"  
  
-   Contraseña: "secreto"  
  
-   Nombre de host: "www.microsoft.com"  
  
-   Número de puerto: 80  
  
-   UrlPath: "visualc/stuff.htm"  
  
-   ExtraInfo: "#contents"  
  
 Para manipular el campo UrlPath (por ejemplo), se usaría [GetUrlPath](#geturlpath), [GetUrlPathLength](#geturlpathlength), y [SetUrlPath](#seturlpath). Usaría [CreateUrl](#createurl) para crear la cadena de dirección URL completa.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
##  <a name="canonicalize"></a>  CUrl::Canonicalize  
 Llame a este método para convertir la cadena de dirección URL en forma canónica.  
  
```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *dwFlags*  
 Las marcas que controlan la canonización. Si no se especifica ninguna marca (*dwFlags* = 0), el método convierte todos los caracteres no seguros y las secuencias de metadatos (como \\., \.., y \\...) secuencias de escape. *dwFlags* puede ser uno de los siguientes valores:  
  
-   ATL_URL_BROWSER_MODE: No codificar o descodificar caracteres tras "#" o "" y no quita los espacios en blanco finales después de "". Si no se especifica este valor, se codifica la dirección URL completa y se quita el espacio en blanco final.  
  
-   ATL_URL _DECODE: convierte todas las secuencias XX % a caracteres, incluidas las secuencias de escape, antes de analizar la dirección URL.  
  
-   ATL_URL _ENCODE_PERCENT: codifica los signos de porcentaje detectados. De forma predeterminada, no se codifican los signos de porcentaje.  
  
-   ATL_URL _ENCODE_SPACES_ONLY: codifica solo espacios.  
  
-   ATL_URL _NO_ENCODE: no convierte los caracteres no seguros en secuencias de escape.  
  
-   ATL_URL _NO_META: no se quitan las secuencias de metadatos (como "."y"..") de la dirección URL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Convertir en forma canónica implica la conversión de caracteres no seguros y espacios para las secuencias de escape.  
  
##  <a name="clear"></a>  CUrl::Clear  
 Llame a este método para borrar todos los campos de dirección URL.  
  
```
inline void Clear() throw();
```  
  
##  <a name="crackurl"></a>  CUrl::CrackUrl  
 Llame a este método para descodificar y analizar la dirección URL.  
  
```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszUrl*  
 La dirección URL.  
  
 *dwFlags*  
 Especificar ATL_URL_DECODE o ATL_URL_ESCAPE para convertir todos los caracteres de escape en *lpszUrl* a sus valores reales después del análisis. (Antes de Visual C++ 2005, ATL_URL_DECODE convertir todos los caracteres de escape antes del análisis.)  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
##  <a name="createurl"></a>  CUrl::CreateUrl  
 Este método construye una cadena de dirección URL de los campos de componente de un objeto de CUrl.  
  
```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszUrl*  
 Un búfer de cadena para contener la cadena de dirección URL completa.  
  
 *pdwMaxLength*  
 La longitud máxima de la *lpszUrl* búfer de cadena.  
  
 *dwFlags*  
 Especificar ATL_URL_ESCAPE para convertir todos los caracteres de escape en *lpszUrl* a sus valores reales.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método anexa sus campos individuales para construir la cadena de dirección URL completa con el formato siguiente:  
  
 **\<esquema > ://\<usuario >:\<pasar > @\<dominio >:\<puerto >\<ruta de acceso >\<adicional >**  
  
 Cuando se llama a este método, el *pdwMaxLength* parámetro debe contener inicialmente la longitud máxima del búfer de cadena al que hace referencia el *lpszUrl* parámetro. El valor de la *pdwMaxLength* parámetro, se actualizará con la longitud real de la cadena de dirección URL.  
  
### <a name="example"></a>Ejemplo  
 En este ejemplo se muestra la creación de un objeto de CUrl y recuperar su cadena de dirección URL  
  
 [!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]  
  
##  <a name="curl"></a>  CUrl::CUrl  
 El constructor.  
  
```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *dirección URL que*  
 La `CUrl` objeto que se va a copiar para crear la dirección URL.  
  
##  <a name="dtor"></a>  CUrl:: ~ CUrl  
 Destructor.  
  
```
~CUrl() throw();
```  
  
##  <a name="getextrainfo"></a>  CUrl::GetExtraInfo  
 Llame a este método para obtener información adicional (como *texto* o # *texto*) de la dirección URL.  
  
```
inline LPCTSTR GetExtraInfo() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una cadena que contiene la información adicional.  
  
##  <a name="getextrainfolength"></a>  CUrl::GetExtraInfoLength  
 Llame a este método para obtener la longitud de la información adicional (como *texto* o # *texto*) para recuperar de la dirección URL.  
  
```
inline DWORD GetExtraInfoLength() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la longitud de la cadena que contiene la información adicional.  
  
##  <a name="gethostname"></a>  CUrl::GetHostName  
 Llame a este método para obtener el nombre de host de la dirección URL.  
  
```
inline LPCTSTR GetHostName() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el nombre de host.  
  
##  <a name="gethostnamelength"></a>  CUrl::GetHostNameLength  
 Llame a este método para obtener la longitud del nombre de host.  
  
```
inline DWORD GetHostNameLength() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el host de la longitud del nombre.  
  
##  <a name="getpassword"></a>  CUrl::GetPassword  
 Llame a este método para obtener la contraseña de la dirección URL.  
  
```
inline LPCTSTR GetPassword() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la contraseña.  
  
##  <a name="getpasswordlength"></a>  CUrl::GetPasswordLength  
 Llame a este método para obtener la longitud de la contraseña.  
  
```
inline DWORD GetPasswordLength() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la longitud de contraseña.  
  
##  <a name="getportnumber"></a>  CUrl::GetPortNumber  
 Llame a este método para obtener el número de puerto.  
  
```
inline ATL_URL_PORT GetPortNumber() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de puerto.  
  
##  <a name="getscheme"></a>  CUrl::GetScheme  
 Llame a este método para obtener el esquema de dirección URL.  
  
```
inline ATL_URL_SCHEME GetScheme() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el [ATL_URL_SCHEME](atl-url-scheme-enum.md) valor que describe el esquema de la dirección URL.  
  
##  <a name="getschemename"></a>  CUrl::GetSchemeName  
 Llame a este método para obtener el nombre de esquema de dirección URL.  
  
```
inline LPCTSTR GetSchemeName() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el nombre de esquema de dirección URL (por ejemplo, "http" o "ftp").  
  
##  <a name="getschemenamelength"></a>  CUrl::GetSchemeNameLength  
 Llame a este método para obtener la longitud del nombre del esquema de dirección URL.  
  
```
inline DWORD GetSchemeNameLength() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la longitud del nombre de esquema de dirección URL.  
  
##  <a name="geturllength"></a>  CUrl::GetUrlLength  
 Llame a este método para obtener la longitud de la dirección URL.  
  
```
inline DWORD GetUrlLength() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la longitud de la dirección URL.  
  
##  <a name="geturlpath"></a>  CUrl::GetUrlPath  
 Llame a este método para obtener la ruta de acceso de dirección URL.  
  
```
inline LPCTSTR GetUrlPath() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la ruta de acceso de dirección URL.  
  
##  <a name="geturlpathlength"></a>  CUrl::GetUrlPathLength  
 Llame a este método para obtener la longitud de ruta de acceso de dirección URL.  
  
```
inline DWORD GetUrlPathLength() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la longitud de ruta de acceso de dirección URL.  
  
##  <a name="getusername"></a>  CUrl::GetUserName  
 Llame a este método para obtener el nombre de usuario de la dirección URL.  
  
```
inline LPCTSTR GetUserName() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el nombre de usuario.  
  
##  <a name="getusernamelength"></a>  CUrl::GetUserNameLength  
 Llame a este método para obtener la longitud del nombre de usuario.  
  
```
inline DWORD GetUserNameLength() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la longitud del nombre de usuario.  
  
##  <a name="operator_eq"></a>  CUrl::operator =  
 Asigna especificado `CUrl` el objeto actual `CUrl` objeto.  
  
```
CUrl& operator= (const CUrl& urlThat) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *dirección URL que*  
 La `CUrl` objeto que se va a copiar en el objeto actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia al objeto actual.  
  
##  <a name="setextrainfo"></a>  CUrl::SetExtraInfo  
 Llame a este método para establecer la información adicional (como *texto* o # *texto*) de la dirección URL.  
  
```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszInfo*  
 Cadena que contiene la información adicional para incluir en la dirección URL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
##  <a name="sethostname"></a>  CUrl::SetHostName  
 Llame a este método para establecer el nombre de host.  
  
```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszHost*  
 El nombre de host.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
##  <a name="setpassword"></a>  CUrl::SetPassword  
 Llame a este método para establecer la contraseña.  
  
```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszPass*  
 Contraseña.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
##  <a name="setportnumber"></a>  CUrl::SetPortNumber  
 Llame a este método para establecer el número de puerto.  
  
```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *nPrt*  
 El número de puerto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
##  <a name="setscheme"></a>  CUrl::SetScheme  
 Llame a este método para establecer el esquema de dirección URL.  
  
```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *nScheme*  
 Uno de los [ATL_URL_SCHEME](atl-url-scheme-enum.md) valores para el esquema.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 También puede establecer el esquema por su nombre (consulte [CUrl::SetSchemeName](#setschemename)).  
  
##  <a name="setschemename"></a>  CUrl::SetSchemeName  
 Llame a este método para establecer el nombre de esquema de dirección URL.  
  
```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszSchm*  
 El nombre de esquema de dirección URL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 También puede establecer el esquema mediante el uso de un [ATL_URL_SCHEME](atl-url-scheme-enum.md) constante (consulte [CUrl::SetScheme](#setscheme)).  
  
##  <a name="seturlpath"></a>  CUrl::SetUrlPath  
 Llame a este método para establecer la ruta de acceso de dirección URL.  
  
```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszPath*  
 La ruta de acceso de dirección URL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
##  <a name="setusername"></a>  CUrl::SetUserName  
 Llame a este método para establecer el nombre de usuario.  
  
```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszUser*  
 Nombre de usuario.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../atl/reference/atl-classes.md)
