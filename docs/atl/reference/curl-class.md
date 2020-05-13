---
title: Clase CUrl
ms.date: 05/06/2019
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
helpviewer_keywords:
- CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
ms.openlocfilehash: 3468e17b031d0a72bc56d915c689fbe4c78859e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330482"
---
# <a name="curl-class"></a>Clase CUrl

Esta clase representa una dirección URL. Le permite manipular cada elemento de la dirección URL independientemente de los demás, ya sea analizando una cadena de URL existente o creando una cadena desde cero.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CUrl
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CUrl::CUrl](#curl)|El constructor.|
|[CUrl::-CUrl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CUrl::Canonicalize](#canonicalize)|Llame a este método para convertir la cadena URL en forma canónica.|
|[CUrl::Clear](#clear)|Llame a este método para borrar todos los campos de dirección URL.|
|[CUrl::CrackUrl](#crackurl)|Llame a este método para descodificar y analizar la dirección URL.|
|[CUrl::CreateUrl](#createurl)|Llame a este método para crear la dirección URL.|
|[CUrl::GetExtraInfo](#getextrainfo)|Llame a este método para obtener información adicional (como *texto* o *texto*) de la dirección URL.|
|[CUrl::GetExtraInfoLength](#getextrainfolength)|Llame a este método para obtener la longitud de la información adicional (por *ejemplo, texto* o *texto*) para recuperar de la dirección URL.|
|[CUrl::GetHostName](#gethostname)|Llame a este método para obtener el nombre de host de la dirección URL.|
|[CUrl::GetHostNameLength](#gethostnamelength)|Llame a este método para obtener la longitud del nombre de host.|
|[CUrl::GetPassword](#getpassword)|Llame a este método para obtener la contraseña de la dirección URL.|
|[CUrl::GetPasswordLength](#getpasswordlength)|Llame a este método para obtener la longitud de la contraseña.|
|[CUrl::GetPortNumber](#getportnumber)|Llame a este método para obtener el número de puerto en términos de ATL_URL_PORT.|
|[CUrl::GetScheme](#getscheme)|Llame a este método para obtener el esquema de dirección URL.|
|[CUrl::GetSchemeName](#getschemename)|Llame a este método para obtener el nombre del esquema de dirección URL.|
|[CUrl::GetSchemeNameLength](#getschemenamelength)|Llame a este método para obtener la longitud del nombre del esquema de dirección URL.|
|[CUrl::GetUrlLength](#geturllength)|Llame a este método para obtener la longitud de la dirección URL.|
|[CUrl::GetUrlPath](#geturlpath)|Llame a este método para obtener la ruta de acceso de dirección URL.|
|[CUrl::GetUrlPathLength](#geturlpathlength)|Llame a este método para obtener la longitud de la ruta de acceso de dirección URL.|
|[CUrl::GetUserName](#getusername)|Llame a este método para obtener el nombre de usuario de la dirección URL.|
|[CUrl::GetUserNameLength](#getusernamelength)|Llame a este método para obtener la longitud del nombre de usuario.|
|[CUrl::SetExtraInfo](#setextrainfo)|Llame a este método para establecer la información adicional (como *texto* o *texto*) de la dirección URL.|
|[CUrl::SetHostName](#sethostname)|Llame a este método para establecer el nombre de host.|
|[CUrl::SetPassword](#setpassword)|Llame a este método para establecer la contraseña.|
|[CUrl::SetPortNumber](#setportnumber)|Llame a este método para establecer el número de puerto en términos de ATL_URL_PORT.|
|[CUrl::SetScheme](#setscheme)|Llame a este método para establecer el esquema de dirección URL.|
|[CUrl::SetSchemeName](#setschemename)|Llame a este método para establecer el nombre del esquema de dirección URL.|
|[CUrl::SetUrlPath](#seturlpath)|Llame a este método para establecer la ruta de acceso de dirección URL.|
|[CUrl::SetUserName](#setusername)|Llame a este método para establecer el nombre de usuario.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CUrl::operador ?](#operator_eq)|Asigna el objeto `CUrl` especificado al `CUrl` objeto actual.|

## <a name="remarks"></a>Observaciones

`CUrl`le permite manipular los campos de una dirección URL, como la ruta de acceso o el número de puerto. `CUrl`entiende las URL del siguiente formulario:

\<Esquema>:// Nombre\<de \@ \<usuario>:\<\<Contraseña>\<NombreHost \<>: PortNumber>/ UrlPath>ExtraInfo>

(Algunos campos son opcionales.) Por ejemplo, considere esta dirección URL:

`http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents`

[CUrl::CrackUrl](#crackurl) lo analiza de la siguiente manera:

- Esquema: "http" o [ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)

- Nombre de usuario: "alguien"

- Contraseña: "secreto"

- HostName:`www.microsoft.com`" "

- PortNumber: 80

- UrlPath: "visualc/stuff.htm"

- ExtraInfo: "#contents"

Para manipular el campo UrlPath (por ejemplo), usaría [GetUrlPath](#geturlpath), [GetUrlPathLength](#geturlpathlength)y [SetUrlPath](#seturlpath). Usaría [CreateUrl](#createurl) para crear la cadena de dirección URL completa.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

## <a name="curlcanonicalize"></a><a name="canonicalize"></a>CUrl::Canonicalize

Llame a este método para convertir la cadena URL en forma canónica.

```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Las banderas que controlan la canonicalización. Si no se especifica ninguna marca (*dwFlags* - 0), el método convierte \\todos los caracteres \\no seguros y meta secuencias (como .,. .., y ...) en secuencias de escape. *dwFlags* puede ser uno de los siguientes valores:

- ATL_URL_BROWSER_MODE: No codifica ni descodifica caracteres después de "" o "" y no elimina el espacio en blanco final después de "". Si no se especifica este valor, se codifica toda la dirección URL y se quita el espacio en blanco final.

- ATL_URL _DECODE: convierte todas las secuencias %XX en caracteres, incluidas las secuencias de escape, antes de analizar la dirección URL.

- ATL_URL _ENCODE_PERCENT: Codifica los signos de porcentaje encontrados. De forma predeterminada, los signos de porcentaje no están codificados.

- ATL_URL _ENCODE_SPACES_ONLY: Codifica solo espacios.

- ATL_URL _NO_ENCODE: no convierte caracteres no seguros en secuencias de escape.

- ATL_URL _NO_META: no elimina las metasecuencias (como "." y "..") de la dirección URL.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

La conversión a forma canónica implica la conversión de caracteres y espacios no seguros en secuencias de escape.

## <a name="curlclear"></a><a name="clear"></a>CUrl::Clear

Llame a este método para borrar todos los campos de dirección URL.

```
inline void Clear() throw();
```

## <a name="curlcrackurl"></a><a name="crackurl"></a>CUrl::CrackUrl

Llame a este método para descodificar y analizar la dirección URL.

```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parámetros

*lpszUrl*<br/>
La dirección URL.

*dwFlags*<br/>
Especifique ATL_URL_DECODE o ATL_URL_ESCAPE para convertir todos los caracteres de escape de *lpszUrl* en sus valores reales después del análisis. (Antes de Visual C++ 2005, ATL_URL_DECODE convertido todos los caracteres de escape antes de analizar.)

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="curlcreateurl"></a><a name="createurl"></a>CUrl::CreateUrl

Este método construye una cadena de dirección URL a partir de los campos de componente de un objeto CUrl.

```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```

### <a name="parameters"></a>Parámetros

*lpszUrl*<br/>
Un búfer de cadena para contener la cadena de dirección URL completa.

*pdwMaxLength*<br/>
La longitud máxima del búfer de cadena *lpszUrl.*

*dwFlags*<br/>
Especifique ATL_URL_ESCAPE convertir todos los caracteres de escape de *lpszUrl* en sus valores reales.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Este método anexa sus campos individuales para construir la cadena url completa con el siguiente formato:

**\<> de\<usuario\< \@ \<>://: pasar\<>\<> \<de dominio: ruta de acceso de>de puerto>>adicional**

Al llamar a este método, el *pdwMaxLength* parámetro debe contener inicialmente la longitud máxima del búfer de cadena al que hace referencia el *lpszUrl* parámetro. El valor del parámetro *pdwMaxLength* se actualizará con la longitud real de la cadena de dirección URL.

### <a name="example"></a>Ejemplo

En este ejemplo se muestra la creación de un cUrl objeto y recuperar su cadena de dirección URL

[!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]

## <a name="curlcurl"></a><a name="curl"></a>CUrl::CUrl

El constructor.

```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Parámetros

*urlThat*<br/>
Objeto `CUrl` que se va a copiar para crear la dirección URL.

## <a name="curlcurl"></a><a name="dtor"></a>CUrl::-CUrl

Destructor.

```
~CUrl() throw();
```

## <a name="curlgetextrainfo"></a><a name="getextrainfo"></a>CUrl::GetExtraInfo

Llame a este método para obtener información adicional (como *texto* o *texto*) de la dirección URL.

```
inline LPCTSTR GetExtraInfo() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una cadena que contiene la información adicional.

## <a name="curlgetextrainfolength"></a><a name="getextrainfolength"></a>CUrl::GetExtraInfoLength

Llame a este método para obtener la longitud de la información adicional (por *ejemplo, texto* o *texto*) para recuperar de la dirección URL.

```
inline DWORD GetExtraInfoLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la longitud de la cadena que contiene la información adicional.

## <a name="curlgethostname"></a><a name="gethostname"></a>CUrl::GetHostName

Llame a este método para obtener el nombre de host de la dirección URL.

```
inline LPCTSTR GetHostName() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el nombre de host.

## <a name="curlgethostnamelength"></a><a name="gethostnamelength"></a>CUrl::GetHostNameLength

Llame a este método para obtener la longitud del nombre de host.

```
inline DWORD GetHostNameLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la longitud del nombre de host.

## <a name="curlgetpassword"></a><a name="getpassword"></a>CUrl::GetPassword

Llame a este método para obtener la contraseña de la dirección URL.

```
inline LPCTSTR GetPassword() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la contraseña.

## <a name="curlgetpasswordlength"></a><a name="getpasswordlength"></a>CUrl::GetPasswordLength

Llame a este método para obtener la longitud de la contraseña.

```
inline DWORD GetPasswordLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la longitud de la contraseña.

## <a name="curlgetportnumber"></a><a name="getportnumber"></a>CUrl::GetPortNumber

Llame a este método para obtener el número de puerto.

```
inline ATL_URL_PORT GetPortNumber() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de puerto.

## <a name="curlgetscheme"></a><a name="getscheme"></a>CUrl::GetScheme

Llame a este método para obtener el esquema de dirección URL.

```
inline ATL_URL_SCHEME GetScheme() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor [ATL_URL_SCHEME](atl-url-scheme-enum.md) que describe el esquema de la dirección URL.

## <a name="curlgetschemename"></a><a name="getschemename"></a>CUrl::GetSchemeName

Llame a este método para obtener el nombre del esquema de dirección URL.

```
inline LPCTSTR GetSchemeName() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el nombre del esquema de DIRECCIÓN URL (como "http" o "ftp").

## <a name="curlgetschemenamelength"></a><a name="getschemenamelength"></a>CUrl::GetSchemeNameLength

Llame a este método para obtener la longitud del nombre del esquema de dirección URL.

```
inline DWORD GetSchemeNameLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la longitud del nombre del esquema de dirección URL.

## <a name="curlgeturllength"></a><a name="geturllength"></a>CUrl::GetUrlLength

Llame a este método para obtener la longitud de la dirección URL.

```
inline DWORD GetUrlLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la longitud de la dirección URL.

## <a name="curlgeturlpath"></a><a name="geturlpath"></a>CUrl::GetUrlPath

Llame a este método para obtener la ruta de acceso de dirección URL.

```
inline LPCTSTR GetUrlPath() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la ruta de acceso de la dirección URL.

## <a name="curlgeturlpathlength"></a><a name="geturlpathlength"></a>CUrl::GetUrlPathLength

Llame a este método para obtener la longitud de la ruta de acceso de dirección URL.

```
inline DWORD GetUrlPathLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la longitud de la ruta de acceso de la dirección URL.

## <a name="curlgetusername"></a><a name="getusername"></a>CUrl::GetUserName

Llame a este método para obtener el nombre de usuario de la dirección URL.

```
inline LPCTSTR GetUserName() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el nombre de usuario.

## <a name="curlgetusernamelength"></a><a name="getusernamelength"></a>CUrl::GetUserNameLength

Llame a este método para obtener la longitud del nombre de usuario.

```
inline DWORD GetUserNameLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la longitud del nombre de usuario.

## <a name="curloperator-"></a><a name="operator_eq"></a>CUrl::operador ?

Asigna el objeto `CUrl` especificado al `CUrl` objeto actual.

```
CUrl& operator= (const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Parámetros

*urlThat*<br/>
Objeto `CUrl` que se va a copiar en el objeto actual.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al objeto actual.

## <a name="curlsetextrainfo"></a><a name="setextrainfo"></a>CUrl::SetExtraInfo

Llame a este método para establecer la información adicional (como *texto* o *texto*) de la dirección URL.

```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```

### <a name="parameters"></a>Parámetros

*lpszInfo*<br/>
Cadena que contiene la información adicional que se va a incluir en la dirección URL.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="curlsethostname"></a><a name="sethostname"></a>CUrl::SetHostName

Llame a este método para establecer el nombre de host.

```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```

### <a name="parameters"></a>Parámetros

*lpszHost*<br/>
El nombre de host.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="curlsetpassword"></a><a name="setpassword"></a>CUrl::SetPassword

Llame a este método para establecer la contraseña.

```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```

### <a name="parameters"></a>Parámetros

*lpszPass*<br/>
La contraseña.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="curlsetportnumber"></a><a name="setportnumber"></a>CUrl::SetPortNumber

Llame a este método para establecer el número de puerto.

```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```

### <a name="parameters"></a>Parámetros

*nPrt*<br/>
Número del puerto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="curlsetscheme"></a><a name="setscheme"></a>CUrl::SetScheme

Llame a este método para establecer el esquema de dirección URL.

```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```

### <a name="parameters"></a>Parámetros

*nScheme*<br/>
Uno de los [valores ATL_URL_SCHEME](atl-url-scheme-enum.md) para el esquema.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

También puede establecer el esquema por nombre (consulte [CUrl::SetSchemeName](#setschemename)).

## <a name="curlsetschemename"></a><a name="setschemename"></a>CUrl::SetSchemeName

Llame a este método para establecer el nombre del esquema de dirección URL.

```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```

### <a name="parameters"></a>Parámetros

*lpszSchm*<br/>
El nombre del esquema de URL.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

También puede establecer el esquema mediante una constante [ATL_URL_SCHEME](atl-url-scheme-enum.md) (consulte [CUrl::SetScheme](#setscheme)).

## <a name="curlseturlpath"></a><a name="seturlpath"></a>CUrl::SetUrlPath

Llame a este método para establecer la ruta de acceso de dirección URL.

```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```

### <a name="parameters"></a>Parámetros

*lpszPath*<br/>
La ruta de acceso URL.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="curlsetusername"></a><a name="setusername"></a>CUrl::SetUserName

Llame a este método para establecer el nombre de usuario.

```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```

### <a name="parameters"></a>Parámetros

*lpszUser*<br/>
Nombre de usuario.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="see-also"></a>Consulte también

[Clases](../../atl/reference/atl-classes.md)
