---
title: Funciones de utilidad HTTP ATL
ms.date: 11/04/2016
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
ms.openlocfilehash: 8f26a23190f9358ff8913e35f5ed7274c8b274ea
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449966"
---
# <a name="atl-http-utility-functions"></a>Funciones de utilidad HTTP ATL

Estas funciones admiten la manipulación de direcciones URL.

|||
|-|-|
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Convierte una dirección URL, que incluye la conversión de caracteres no seguros y los espacios en las secuencias de escape en formato canónico.|
|[AtlCombineUrl](#atlcombineurl)|Combina una dirección URL base y una dirección URL relativa en una única dirección de URL canónica.|
|[AtlEscapeUrl](#atlescapeurl)|Convierte todos los caracteres no seguros en secuencias de escape.|
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|Obtiene el número de puerto predeterminado asociado con un determinado protocolo de Internet o un esquema.|
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|Determina si un carácter es seguro para su uso en una dirección URL.|
|[AtlUnescapeUrl](#atlunescapeurl)|Convierte los caracteres de escape a sus valores originales.|
|[RGBToHtml](#rgbtohtml)|Convierte un [COLORREF](/windows/desktop/gdi/colorref) valor para el texto HTLM correspondiente a ese valor de color.|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|Llame a esta función para convertir una hora del sistema en una cadena con un formato adecuado para usarla en encabezados HTTP.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

## <a name="atlcanonicalizeurl"></a> AtlCanonicalizeUrl

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
La dirección URL se puede dar formato canónico.

*szCanonicalized*<br/>
Búfer asignado por el autor de llamada para recibir la dirección URL con formato canónico.

*pdwMaxLength*<br/>
Puntero a una variable que contiene la longitud en caracteres de *szCanonicalized*. Si la función se realiza correctamente, la variable recibe el número de caracteres escritos en el búfer incluido el carácter nulo final. Si se produce un error en la función, la variable recibe la longitud requerida en bytes del búfer, incluido el espacio para el carácter nulo de terminación.

*dwFlags*<br/>
Marcas ATL_URL que controlan el comportamiento de esta función.

- ATL_URL_BROWSER_MODE no codificar o descodificar caracteres tras "#" o "?" y no quita los espacios en blanco finales después de "?". Si no se especifica este valor, se codifica la dirección URL completa y se quita el espacio en blanco final.

- ATL_URL_DECODE convierte todas las secuencias XX % a caracteres, incluidas las secuencias de escape, antes de analizar la dirección URL.

- Codifica ATL_URL_ENCODE_PERCENT ha encontrado ningún signo de porcentaje. De forma predeterminada, no se codifican los signos de porcentaje.

- Solo los espacios ATL_URL_ENCODE_SPACES_ONLY codifica.

- ATL_URL_ESCAPE convierte todos los (% XX) de las secuencias de escape en sus caracteres correspondientes.

- ATL_URL_NO_ENCODE no convierte los caracteres no seguros en secuencias de escape.

- ATL_URL_NO_META no quita las secuencias de metadatos (como "."y"..") de la dirección URL.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Se comporta como la versión actual de [InternetCanonicalizeUrl](/windows/desktop/api/wininet/nf-wininet-internetcanonicalizeurla) pero no requiere WinInet o Internet Explorer para instalarse.

## <a name="atlcombineurl"></a> AtlCombineUrl

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
La dirección URL base.

*szRelativeUrl*<br/>
La dirección URL relativa a la dirección URL base.

*szBuffer*<br/>
Búfer asignado por el autor de llamada para recibir la dirección URL con formato canónico.

*pdwMaxLength*<br/>
Puntero a una variable que contiene la longitud en caracteres de *szBuffer*. Si la función se realiza correctamente, la variable recibe el número de caracteres escritos en el búfer incluido el carácter nulo final. Si se produce un error en la función, la variable recibe la longitud requerida en bytes del búfer, incluido el espacio para el carácter nulo de terminación.

*dwFlags*<br/>
Marcas que controlan el comportamiento de esta función. Consulte [AtlCanonicalizeUrl](#atlcanonicalizeurl).

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Se comporta como la versión actual de [InternetCombineUrl](/windows/desktop/api/wininet/nf-wininet-internetcombineurla) pero no requiere WinInet o Internet Explorer para instalarse.

## <a name="atlescapeurl"></a> AtlEscapeUrl

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
La dirección URL que se va a convertir.

*lpszStringOut*<br/>
Búfer asignado por el autor de la llamada a la que se escribirá la dirección URL convertida.

*pdwStrLen*<br/>
Puntero a una variable DWORD. Si la función se realiza correctamente, *pdwStrLen* recibe el número de caracteres escritos en el búfer incluido el carácter nulo final. Si se produce un error en la función, la variable recibe la longitud requerida en bytes del búfer, incluido el espacio para el carácter nulo de terminación. Cuando se usa la versión de caracteres anchos de este método, *pdwStrLen* recibe el número de caracteres necesarios, no el número de bytes.

*dwMaxLength*<br/>
El tamaño del búfer *lpszStringOut*.

*dwFlags*<br/>
Marcas ATL_URL que controlan el comportamiento de esta función. Consulte [ATLCanonicalizeUrl](#atlcanonicalizeurl) para los valores posibles.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

## <a name="atlgetdefaulturlport"></a> AtlGetDefaultUrlPort

Llame a esta función para obtener el número de puerto predeterminado asociado a un protocolo de Internet o un esquema específicos.

```
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();
```

### <a name="parameters"></a>Parámetros

*m_nScheme*<br/>
El [ATL_URL_SCHEME](atl-url-scheme-enum.md) valor que identifica el esquema para el que desea obtener el número de puerto.

### <a name="return-value"></a>Valor devuelto

El [ATL_URL_PORT](atl-typedefs.md#atl_url_port) asociado con el esquema especificado o ATL_URL_INVALID_PORT_NUMBER si no se reconoce el esquema.

## <a name="atlisunsafeurlchar"></a> AtlIsUnsafeUrlChar

Llame a esta función para comprobar si un carácter es seguro para usarlo en una dirección URL.

```
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();
```

### <a name="parameters"></a>Parámetros

*chIn*<br/>
El carácter que se va a probarse por motivos de seguridad.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el carácter de entrada es unsafe, FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Caracteres que no deben usarse en las direcciones URL se pueden probar con esta función y se convierte usando [AtlCanonicalizeUrl](#atlcanonicalizeurl).

## <a name="atlunescapeurl"></a> AtlUnescapeUrl

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
La dirección URL que se va a convertir.

*lpszStringOut*<br/>
Búfer asignado por el autor de la llamada a la que se escribirá la dirección URL convertida.

*pdwStrLen*<br/>
Puntero a una variable DWORD. Si la función se realiza correctamente, la variable recibe el número de caracteres escritos en el búfer incluido el carácter nulo final. Si se produce un error en la función, la variable recibe la longitud requerida en bytes del búfer, incluido el espacio para el carácter nulo de terminación.

*dwMaxLength*<br/>
El tamaño del búfer *lpszStringOut*.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Invierte el proceso de conversión aplicado por [AtlEscapeUrl](#atlescapeurl).

## <a name="rgbtohtml"></a> RGBToHtml

Convierte un [COLORREF](/windows/desktop/gdi/colorref) valor para el texto HTLM correspondiente a ese valor de color.

```cpp
bool inline RGBToHtml(
   COLORREF color,
   LPTSTR pbOut,
   long nBuffer);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
Un valor de color RGB.

*pbOut*<br/>
Búfer asignado por el autor de llamada para recibir el texto para el valor de color HTML. El búfer debe tener espacio para al menos 8 caracteres, incluido el espacio para el terminador nulo).

*nBuffer*<br/>
El tamaño en bytes del búfer (incluido el espacio para el terminador nulo).

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Un valor de color HTML es un signo de almohadilla seguido por un valor hexadecimal de 6 dígitos con 2 dígitos para cada uno de los componentes rojos, verde y azules del color (por ejemplo, es blanco #FFFFFF).

## <a name="systemtimetohttpdate"></a> SystemTimeToHttpDate

Llame a esta función para convertir una hora del sistema en una cadena con un formato adecuado para usarla en encabezados HTTP.

```cpp
inline void SystemTimeToHttpDate(
   const SYSTEMTIME& st,
   CStringA& strTime);
```

### <a name="parameters"></a>Parámetros

*st*<br/>
La hora del sistema se obtendrán como una cadena de formato HTTP.

*strTime*<br/>
Una referencia a una variable de cadena para recibir el HTTP de fecha y hora como se define en RFC 2616 ([https://www.ietf.org/rfc/rfc2616.txt](https://www.ietf.org/rfc/rfc2616.txt)) y RFC 1123 ([https://www.ietf.org/rfc/rfc1123.txt](https://www.ietf.org/rfc/rfc1123.txt)).

## <a name="see-also"></a>Vea también

[Conceptos](../active-template-library-atl-concepts.md)<br/>
[Componentes de escritorio COM de ATL](../atl-com-desktop-components.md)<br/>
[InternetCanonicalizeUrl](/windows/desktop/api/wininet/nf-wininet-internetcanonicalizeurla)
