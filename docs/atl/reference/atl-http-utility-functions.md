---
title: Funciones de la utilidad HTTP de ATL
ms.date: 11/04/2016
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
ms.openlocfilehash: ca6dfdfb02f5ef629c6eb523744260f177a3309b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865045"
---
# <a name="atl-http-utility-functions"></a>Funciones de la utilidad HTTP de ATL

Estas funciones admiten la manipulación de direcciones URL.

|||
|-|-|
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalizes una dirección URL, que incluye la conversión de caracteres y espacios no seguros en secuencias de escape.|
|[AtlCombineUrl](#atlcombineurl)|Combina una dirección URL base y una dirección URL relativa en una sola dirección URL canónica.|
|[AtlEscapeUrl](#atlescapeurl)|Convierte todos los caracteres no seguros en secuencias de escape.|
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|Obtiene el número de puerto predeterminado asociado a un esquema o protocolo de Internet determinado.|
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|Determina si un carácter es seguro para su uso en una dirección URL.|
|[AtlUnescapeUrl](#atlunescapeurl)|Vuelve a convertir los caracteres de escape en sus valores originales.|
|[RGBToHtml](#rgbtohtml)|Convierte un valor [COLORREF](/windows/win32/gdi/colorref) en el texto html correspondiente a ese valor de color.|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|Llame a esta función para convertir una hora del sistema en una cadena con un formato adecuado para usarla en encabezados HTTP.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil. h

## <a name="atlcanonicalizeurl"></a>AtlCanonicalizeUrl

Llame a esta función para canonizar una dirección URL, que incluye la conversión de espacios y caracteres no seguros en secuencias de escape.

```cpp
inline BOOL AtlCanonicalizeUrl(
   LPCTSTR szUrl,
   LPTSTR szCanonicalized,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parámetros

*szUrl*<br/>
Dirección URL que se va a canonizar.

*szCanonicalized*<br/>
Búfer asignado por el llamador para recibir la dirección URL con formato canónico.

*pdwMaxLength*<br/>
Puntero a una variable que contiene la longitud en caracteres de *szCanonicalized*. Si la función se ejecuta correctamente, la variable recibe el número de caracteres escritos en el búfer, incluido el carácter nulo de terminación. Si se produce un error en la función, la variable recibe la longitud necesaria en bytes del búfer, incluido el espacio para el carácter nulo de terminación.

*dwFlags*<br/>
ATL_URL marcas que controlan el comportamiento de esta función.

- ATL_URL_BROWSER_MODE no codifica ni descodifica caracteres después de "#" o "?", y no quita los espacios en blanco finales después de "?". Si no se especifica este valor, la dirección URL completa se codifica y se quita el espacio en blanco final.

- ATL_URL_DECODE convierte todas las secuencias de% XX en caracteres, incluidas las secuencias de escape, antes de analizar la dirección URL.

- ATL_URL_ENCODE_PERCENT codifica cualquier signo de porcentaje encontrado. De forma predeterminada, los signos de porcentaje no se codifican.

- ATL_URL_ENCODE_SPACES_ONLY codifica solo los espacios.

- ATL_URL_ESCAPE convierte todas las secuencias de escape (% XX) en sus caracteres correspondientes.

- ATL_URL_NO_ENCODE no convierte los caracteres no seguros en secuencias de escape.

- ATL_URL_NO_META no quita las secuencias meta (como "." y "..") de la dirección URL.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Se comporta como la versión actual de [InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw) pero no requiere que se instale WinInet o Internet Explorer.

## <a name="atlcombineurl"></a>AtlCombineUrl

Llame a esta función para combinar una dirección URL base y una dirección URL relativa en una única dirección URL canónica.

```cpp
inline BOOL AtlCombineUrl(
   LPCTSTR szBaseUrl,
   LPCTSTR szRelativeUrl,
   LPTSTR szBuffer,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parámetros

*szBaseUrl*<br/>
Dirección URL base.

*szRelativeUrl*<br/>
Dirección URL relativa a la dirección URL base.

*szBuffer*<br/>
Búfer asignado por el llamador para recibir la dirección URL con formato canónico.

*pdwMaxLength*<br/>
Puntero a una variable que contiene la longitud en caracteres de *szBuffer*. Si la función se ejecuta correctamente, la variable recibe el número de caracteres escritos en el búfer, incluido el carácter nulo de terminación. Si se produce un error en la función, la variable recibe la longitud necesaria en bytes del búfer, incluido el espacio para el carácter nulo de terminación.

*dwFlags*<br/>
Marcas que controlan el comportamiento de esta función. Vea [AtlCanonicalizeUrl](#atlcanonicalizeurl).

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Se comporta como la versión actual de [InternetCombineUrl](/windows/win32/api/wininet/nf-wininet-internetcombineurlw) pero no requiere que se instale WinInet o Internet Explorer.

## <a name="atlescapeurl"></a>AtlEscapeUrl

Llame a esta función para convertir todos los caracteres no seguros en secuencias de escape.

```cpp
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

*lpszStringIn*<br/>
Dirección URL que se va a convertir.

*lpszStringOut*<br/>
Búfer asignado por el llamador en el que se escribirá la dirección URL convertida.

*pdwStrLen*<br/>
Puntero a una variable DWORD. Si la función se ejecuta correctamente, *pdwStrLen* recibe el número de caracteres que se escriben en el búfer, incluido el carácter nulo de terminación. Si se produce un error en la función, la variable recibe la longitud necesaria en bytes del búfer, incluido el espacio para el carácter nulo de terminación. Cuando se usa la versión de caracteres anchos de este método, *pdwStrLen* recibe el número de caracteres necesarios, no el número de bytes.

*dwMaxLength*<br/>
Tamaño del búfer *lpszStringOut*.

*dwFlags*<br/>
ATL_URL marcas que controlan el comportamiento de esta función. Consulte [ATLCanonicalizeUrl](#atlcanonicalizeurl) para ver los valores posibles.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="atlgetdefaulturlport"></a>AtlGetDefaultUrlPort

Llame a esta función para obtener el número de puerto predeterminado asociado a un protocolo de Internet o un esquema específicos.

```
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();
```

### <a name="parameters"></a>Parámetros

*m_nScheme*<br/>
El valor [ATL_URL_SCHEME](atl-url-scheme-enum.md) que identifica el esquema para el que desea obtener el número de puerto.

### <a name="return-value"></a>Valor devuelto

[ATL_URL_PORT](atl-typedefs.md#atl_url_port) asociado al esquema especificado o ATL_URL_INVALID_PORT_NUMBER si no se reconoce el esquema.

## <a name="atlisunsafeurlchar"></a>AtlIsUnsafeUrlChar

Llame a esta función para comprobar si un carácter es seguro para usarlo en una dirección URL.

```
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();
```

### <a name="parameters"></a>Parámetros

*Emulsiona*<br/>
Carácter que se va a probar para la seguridad.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el carácter de entrada no es seguro, de lo contrario, es FALSE.

### <a name="remarks"></a>Observaciones

Los caracteres que no deben usarse en las direcciones URL se pueden probar mediante esta función y convertirse mediante [AtlCanonicalizeUrl](#atlcanonicalizeurl).

## <a name="atlunescapeurl"></a>AtlUnescapeUrl

Llame a esta función para convertir de nuevo los caracteres de escape en sus valores originales.

```cpp
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

*lpszStringIn*<br/>
Dirección URL que se va a convertir.

*lpszStringOut*<br/>
Búfer asignado por el llamador en el que se escribirá la dirección URL convertida.

*pdwStrLen*<br/>
Puntero a una variable DWORD. Si la función se ejecuta correctamente, la variable recibe el número de caracteres escritos en el búfer, incluido el carácter nulo de terminación. Si se produce un error en la función, la variable recibe la longitud necesaria en bytes del búfer, incluido el espacio para el carácter nulo de terminación.

*dwMaxLength*<br/>
Tamaño del búfer *lpszStringOut*.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Invierte el proceso de conversión aplicado por [AtlEscapeUrl](#atlescapeurl).

## <a name="rgbtohtml"></a>RGBToHtml

Convierte un valor [COLORREF](/windows/win32/gdi/colorref) en el texto html correspondiente a ese valor de color.

```cpp
bool inline RGBToHtml(
   COLORREF color,
   LPTSTR pbOut,
   long nBuffer);
```

### <a name="parameters"></a>Parámetros

*Color*<br/>
Valor de color RGB.

*pbOut*<br/>
Búfer asignado por el llamador para recibir el texto del valor de color HTML. El búfer debe tener espacio para al menos 8 caracteres, incluido el espacio para el terminador null.

*nBuffer*<br/>
Tamaño en bytes del búfer (incluido el espacio para el terminador nulo).

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Un valor de color HTML es un signo de almohadilla seguido de un valor hexadecimal de 6 dígitos que usa 2 dígitos para cada uno de los componentes rojo, verde y azul del color (por ejemplo, #FFFFFF es blanco).

## <a name="systemtimetohttpdate"></a>SystemTimeToHttpDate

Llame a esta función para convertir una hora del sistema en una cadena con un formato adecuado para usarla en encabezados HTTP.

```cpp
inline void SystemTimeToHttpDate(
   const SYSTEMTIME& st,
   CStringA& strTime);
```

### <a name="parameters"></a>Parámetros

*primer*<br/>
La hora del sistema que se va a obtener como una cadena de formato HTTP.

*strTime*<br/>
Referencia a una variable de cadena para recibir la fecha y hora HTTP tal como se define en RFC 2616 ([https://www.ietf.org/rfc/rfc2616.txt](https://www.ietf.org/rfc/rfc2616.txt)) y RFC 1123 ([https://www.ietf.org/rfc/rfc1123.txt](https://www.ietf.org/rfc/rfc1123.txt)).

## <a name="see-also"></a>Consulte también

[Conceptos](../active-template-library-atl-concepts.md)<br/>
[Componentes de escritorio COM de ATL](../atl-com-desktop-components.md)<br/>
[InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw)
