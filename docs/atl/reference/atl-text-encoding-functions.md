---
title: Funciones de codificación de texto ATL
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
ms.assetid: 2ae1648b-2b87-4112-92aa-0069fcfd23da
ms.openlocfilehash: 1380d33c485c1ac895558bbcaf86c902c6074cd4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865046"
---
# <a name="atl-text-encoding-functions"></a>Funciones de codificación de texto ATL

Estas funciones admiten la codificación y descodificación de texto.

|||
|-|-|
|[AtlGetHexValue](#atlgethexvalue)|Llame a esta función para obtener el valor numérico de un dígito hexadecimal.|
|[AtlGetVersion](#atlgetversion)|Llame a esta función para obtener la versión de la biblioteca ATL que está utilizando.  |
|[AtlHexDecode](#atlhexdecode)|Descodifica una cadena de datos que se ha codificado como texto hexadecimal, como por una llamada anterior a [AtlHexEncode](#atlhexencode).|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|Llame a esta función para obtener el tamaño en bytes de un búfer que puede contener datos descodificados de una cadena con codificación hexadecimal de la longitud especificada.|
|[AtlHexEncode](#atlhexencode)|Llame a esta función para codificar algunos datos en forma de cadena de texto hexadecimal.|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.|
|[AtlHexValue](#atlhexvalue)|Llame a esta función para obtener el valor numérico de un dígito hexadecimal. |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|Llame a esta función para convertir una cadena Unicode en UTF-8. |
|[BEncode](#bencode)|Llame a esta función para convertir algunos datos utilizando la codificación “B”.|
|[BEncodeGetRequiredLength](#bencodegetrequiredlength)|Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.|
|[EscapeXML](#escapexml)|Llame a esta función para convertir los caracteres que no son seguros para usarlos en XML en sus equivalentes seguros.|
|[GetExtendedChars](#getextendedchars)|Llame a esta función para obtener el número de caracteres extendidos de una cadena.|
|[IsExtendedChar](#isextendedchar)|Llame a esta función para averiguar si un carácter determinado es un carácter extendido (menor que 32, mayor que 126, y no una tabulación, salto de línea o retorno de carro)|
|[QEncode](#qencode)|Llame a esta función para convertir algunos datos utilizando la codificación “Q”.  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.|
|[QPDecode](#qpdecode)|Descodifica una cadena de datos que se ha codificado en formato entrecomillado imprimible, como por una llamada anterior a [QPEncode](#qpencode).|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|Llame a esta función para obtener el tamaño en bytes de un búfer que puede contener datos descodificados de una cadena con codificación entrecomillada imprimible de la longitud especificada.|
|[QPEncode](#qpencode)|Llame a esta función para codificar algunos datos en formato entrecomillado imprimible.|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.|
|[UUDecode](#uudecode)|Descodifica una cadena de datos que ha sido uuencode, como por una llamada anterior a [uuencode](#uuencode).|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|Llame a esta función para obtener el tamaño en bytes de un búfer que puede contener datos descodificados de una cadena con codificación UUEncode de la longitud especificada.|
|[UUEncode](#uuencode)|Llame a esta función para codificar datos con formato UUEncode. |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlenc. h

## <a name="atlgethexvalue"></a>AtlGetHexValue

Llame a esta función para obtener el valor numérico de un dígito hexadecimal.

```
inline char AtlGetHexValue(char chIn) throw();
```

### <a name="parameters"></a>Parámetros

*Emulsiona*<br/>
El carácter hexadecimal ' 0 '-' 9 ', ' contener-'F ' o ' contener-'F '.

### <a name="return-value"></a>Valor devuelto

Valor numérico del carácter de entrada interpretado como un dígito hexadecimal. Por ejemplo, una entrada de ' 0 ' devuelve un valor de 0 y una entrada de ' A ' devuelve un valor de 10. Si el carácter de entrada no es un dígito hexadecimal, esta función devuelve-1.

## <a name="atlgetversion"></a>AtlGetVersion

Llame a esta función para obtener la versión de la biblioteca ATL que está utilizando.

```
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);
```

### <a name="parameters"></a>Parámetros

*Van*<br/>
Puntero reservado.

### <a name="return-value"></a>Valor devuelto

Devuelve un valor entero DWORD de la versión de la biblioteca ATL que se va a compilar o ejecutar.

## <a name="example"></a>Ejemplo

Se debe llamar a la función como se indica a continuación.

[!code-cpp[NVC_ATL_Utilities#95](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="atlhexdecode"></a>AtlHexDecode

Descodifica una cadena de datos que se ha codificado como texto hexadecimal, como por una llamada anterior a [AtlHexEncode](#atlhexencode).

```
inline BOOL AtlHexDecode(
   LPCSTR pSrcData,
   int nSrcLen,
   LPBYTE pbDest,
   int* pnDestLen) throw();
```

### <a name="parameters"></a>Parámetros

*pSrcData*<br/>
Cadena que contiene los datos que se van a descodificar.

*nSrcLen*<br/>
Longitud en caracteres de *pSrcData*.

*pbDest*<br/>
Búfer asignado por el llamador para recibir los datos descodificados.

*pnDestLen*<br/>
Puntero a una variable que contiene la longitud en bytes de *pbDest*. Si la función se ejecuta correctamente, la variable recibe el número de bytes escritos en el búfer. Si se produce un error en la función, la variable recibe la longitud necesaria en bytes del búfer.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="atlhexdecodegetrequiredlength"></a>AtlHexDecodeGetRequiredLength

Llame a esta función para obtener el tamaño en bytes de un búfer que puede contener datos descodificados de una cadena con codificación hexadecimal de la longitud especificada.

```
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Parámetros

*nSrcLen*<br/>
Número de caracteres de la cadena codificada.

### <a name="return-value"></a>Valor devuelto

Número de bytes necesarios para un búfer que puede contener una cadena descodificada de caracteres *nSrcLen* .

## <a name="atlhexencode"></a>AtlHexEncode

Llame a esta función para codificar algunos datos en forma de cadena de texto hexadecimal.

```
inline BOOL AtlHexEncode(
   const BYTE * pbSrcData,
   int nSrcLen,
   LPSTR szDest,
int * pnDestLen) throw();
```

### <a name="parameters"></a>Parámetros

*pbSrcData*<br/>
Búfer que contiene los datos que se van a codificar.

*nSrcLen*<br/>
La longitud en bytes de los datos que se van a codificar.

*szDest*<br/>
Búfer asignado por el llamador para recibir los datos codificados.

*pnDestLen*<br/>
Puntero a una variable que contiene la longitud en caracteres de *szDest*. Si la función se ejecuta correctamente, la variable recibe el número de caracteres que se escriben en el búfer. Si se produce un error en la función, la variable recibe la longitud necesaria en caracteres del búfer.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Cada byte de los datos de origen se codifica como dos caracteres hexadecimales.

## <a name="atlhexencodegetrequiredlength"></a>AtlHexEncodeGetRequiredLength

Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.

```
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Parámetros

*nSrcLen*<br/>
El número de bytes de datos que se van a codificar.

### <a name="return-value"></a>Valor devuelto

Número de caracteres necesarios para un búfer que puede contener datos codificados de *nSrcLen* bytes.

## <a name="atlhexvalue"></a>AtlHexValue

Llame a esta función para obtener el valor numérico de un dígito hexadecimal.

```
inline short AtlHexValue(char chIn) throw();
```

### <a name="parameters"></a>Parámetros

*Emulsiona*<br/>
El carácter hexadecimal ' 0 '-' 9 ', ' contener-'F ' o ' contener-'F '.

### <a name="return-value"></a>Valor devuelto

Valor numérico del carácter de entrada interpretado como un dígito hexadecimal. Por ejemplo, una entrada de ' 0 ' devuelve un valor de 0 y una entrada de ' A ' devuelve un valor de 10. Si el carácter de entrada no es un dígito hexadecimal, esta función devuelve-1.

## <a name="atlunicodetoutf8"></a>AtlUnicodeToUTF8

Llame a esta función para convertir una cadena Unicode en UTF-8.

```
ATL_NOINLINE inline int AtlUnicodeToUTF8(
   LPCWSTR wszSrc,
   int nSrc,
   LPSTR szDest,
   int nDest) throw();
```

### <a name="parameters"></a>Parámetros

*wszSrc*<br/>
Cadena Unicode que se va a convertir.

*nSrc*<br/>
Longitud en caracteres de la cadena Unicode.

*szDest*<br/>
Búfer asignado por el llamador para recibir la cadena convertida.

*nDest*<br/>
La longitud en bytes del búfer.

### <a name="return-value"></a>Valor devuelto

Devuelve el número de caracteres de la cadena convertida.

### <a name="remarks"></a>Observaciones

Para determinar el tamaño del búfer necesario para la cadena convertida, llame a esta función pasando 0 para *szDest* y *nDest*.

## <a name="bencode"></a>BEncode

Llame a esta función para convertir algunos datos utilizando la codificación “B”.

```
inline BOOL BEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet) throw();
```

### <a name="parameters"></a>Parámetros

*pbSrcData*<br/>
Búfer que contiene los datos que se van a codificar.

*nSrcLen*<br/>
La longitud en bytes de los datos que se van a codificar.

*szDest*<br/>
Búfer asignado por el llamador para recibir los datos codificados.

*pnDestLen*<br/>
Puntero a una variable que contiene la longitud en caracteres de *szDest*. Si la función se ejecuta correctamente, la variable recibe el número de caracteres que se escriben en el búfer. Si se produce un error en la función, la variable recibe la longitud necesaria en caracteres del búfer.

*pszCharSet*<br/>
Juego de caracteres que se va a usar para la conversión.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El esquema de codificación "B" se describe en RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)).

## <a name="bencodegetrequiredlength"></a>BEncodeGetRequiredLength

Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.

```
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>Parámetros

*nSrcLen*<br/>
El número de bytes de datos que se van a codificar.

*nCharsetLen*<br/>
Longitud en caracteres del juego de caracteres que se va a usar para la conversión.

### <a name="return-value"></a>Valor devuelto

Número de caracteres necesarios para un búfer que puede contener datos codificados de *nSrcLen* bytes.

### <a name="remarks"></a>Observaciones

El esquema de codificación "B" se describe en RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)).

## <a name="escapexml"></a>EscapeXML

Llame a esta función para convertir los caracteres que no son seguros para usarlos en XML en sus equivalentes seguros.

```
inline int EscapeXML(
   const wchar_t * szIn,
   int nSrcLen,
   wchar_t * szEsc,
   int nDestLen,
   DWORD dwFlags = ATL_ESC_FLAG_NONE) throw();
```

### <a name="parameters"></a>Parámetros

*szIn*<br/>
Cadena que se va a convertir.

*nSrclen*<br/>
Longitud en caracteres de la cadena que se va a convertir.

*szEsc*<br/>
Búfer asignado por el llamador para recibir la cadena convertida.

*nDestLen*<br/>
Longitud en caracteres del búfer asignado por el llamador.

*dwFlags*<br/>
ATL_ESC marcadores que describen cómo se va a realizar la conversión.

- ATL_ESC_FLAG_NONE comportamiento predeterminado. No se convierten las comillas y los apóstrofos.
- ATL_ESC_FLAG_ATTR las marcas de Comillas y los apóstrofos se convierten en `&quot;` y `&apos;` respectivamente.

### <a name="return-value"></a>Valor devuelto

Longitud en caracteres de la cadena convertida.

### <a name="remarks"></a>Observaciones

En la tabla se muestran las posibles conversiones realizadas por esta función:

|Source|Destination|
|------------|-----------------|
|\<|&lt;|
|>|&gt;|
|&|&amp;|
|'|&apos;|
|"|&quot;|

## <a name="getextendedchars"></a>GetExtendedChars

Llame a esta función para obtener el número de caracteres extendidos de una cadena.

```
inline int GetExtendedChars(LPCSTR szSrc, int nSrcLen) throw();
```

### <a name="parameters"></a>Parámetros

*szSrc*<br/>
Cadena que se va a analizar.

*nSrcLen*<br/>
Longitud de la cadena en caracteres.

### <a name="return-value"></a>Valor devuelto

Devuelve el número de caracteres extendidos que se encuentran dentro de la cadena según lo establecido por [IsExtendedChar](#isextendedchar).

## <a name="isextendedchar"></a>IsExtendedChar

Llame a esta función para averiguar si un carácter determinado es un carácter extendido (menor que 32, mayor que 126, y no una tabulación, salto de línea o retorno de carro)

```
inline int IsExtendedChar(char ch) throw();
```

### <a name="parameters"></a>Parámetros

*Cam*<br/>
Carácter que se va a probar.

### <a name="return-value"></a>Valor devuelto

TRUE si el carácter es extendido; en caso contrario, FALSE.

## <a name="qencode"></a>QEncode

Llame a esta función para convertir algunos datos utilizando la codificación “Q”.

```
inline BOOL QEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet,
   int* pnNumEncoded = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*pbSrcData*<br/>
Búfer que contiene los datos que se van a codificar.

*nSrcLen*<br/>
La longitud en bytes de los datos que se van a codificar.

*szDest*<br/>
Búfer asignado por el llamador para recibir los datos codificados.

*pnDestLen*<br/>
Puntero a una variable que contiene la longitud en caracteres de *szDest*. Si la función se ejecuta correctamente, la variable recibe el número de caracteres que se escriben en el búfer. Si se produce un error en la función, la variable recibe la longitud necesaria en caracteres del búfer.

*pszCharSet*<br/>
Juego de caracteres que se va a usar para la conversión.

*pnNumEncoded*<br/>
Un puntero a una variable que en la devolución contiene el número de caracteres no seguros que tuvieron que convertirse.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El esquema de codificación "Q" se describe en RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)).

## <a name="qencodegetrequiredlength"></a>QEncodeGetRequiredLength

Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.

```
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>Parámetros

*nSrcLen*<br/>
El número de bytes de datos que se van a codificar.

*nCharsetLen*<br/>
Longitud en caracteres del juego de caracteres que se va a usar para la conversión.

### <a name="return-value"></a>Valor devuelto

Número de caracteres necesarios para un búfer que puede contener datos codificados de *nSrcLen* bytes.

### <a name="remarks"></a>Observaciones

El esquema de codificación "Q" se describe en RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)).

## <a name="qpdecode"></a>QPDecode

Descodifica una cadena de datos que se ha codificado en formato entrecomillado imprimible, como por una llamada anterior a [QPEncode](#qpencode).

```
inline BOOL QPDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parámetros

*pbSrcData*<br/>
de Búfer que contiene los datos que se van a descodificar.

*nSrcLen*<br/>
de La longitud en bytes de *pbSrcData*.

*szDest*<br/>
enuncia Búfer asignado por el llamador para recibir los datos descodificados.

*pnDestLen*<br/>
enuncia Puntero a una variable que contiene la longitud en bytes de *szDest*. Si la función se ejecuta correctamente, la variable recibe el número de bytes escritos en el búfer. Si se produce un error en la función, la variable recibe la longitud necesaria en bytes del búfer.

*dwFlags*<br/>
de ATLSMTP_QPENCODE marcadores que describen cómo se va a realizar la conversión.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El esquema de codificación entrecomillado imprimible se describe en RFC 2045 ([https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)).

## <a name="qpdecodegetrequiredlength"></a>QPDecodeGetRequiredLength

Llame a esta función para obtener el tamaño en bytes de un búfer que puede contener datos descodificados de una cadena con codificación entrecomillada imprimible de la longitud especificada.

```
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Parámetros

*nSrcLen*<br/>
Número de caracteres de la cadena codificada.

### <a name="return-value"></a>Valor devuelto

Número de bytes necesarios para un búfer que puede contener una cadena descodificada de caracteres *nSrcLen* .

### <a name="remarks"></a>Observaciones

El esquema de codificación entrecomillado imprimible se describe en RFC 2045 ([https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)).

## <a name="qpencode"></a>QPEncode

Llame a esta función para codificar algunos datos en formato entrecomillado imprimible.

```
inline BOOL QPEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>Parámetros

*pbSrcData*<br/>
Búfer que contiene los datos que se van a codificar.

*nSrcLen*<br/>
La longitud en bytes de los datos que se van a codificar.

*szDest*<br/>
Búfer asignado por el llamador para recibir los datos codificados.

*pnDestLen*<br/>
Puntero a una variable que contiene la longitud en caracteres de *szDest*. Si la función se ejecuta correctamente, la variable recibe el número de caracteres que se escriben en el búfer. Si se produce un error en la función, la variable recibe la longitud necesaria en caracteres del búfer.

*dwFlags*<br/>
ATLSMTP_QPENCODE marcadores que describen cómo se va a realizar la conversión.

- ATLSMTP_QPENCODE_DOT si un punto aparece al principio de una línea, se agrega al resultado y se codifica.

- ATLSMTP_QPENCODE_TRAILING_SOFT anexa `=\r\n` a la cadena codificada.

El esquema de codificación entrecomillado imprimible se describe en [RFC 2045](https://www.ietf.org/rfc/rfc2045.txt).

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El esquema de codificación entrecomillado imprimible se describe en RFC 2045 ([https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)).

## <a name="qpencodegetrequiredlength"></a>QPEncodeGetRequiredLength

Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.

```
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Parámetros

*nSrcLen*<br/>
El número de bytes de datos que se van a codificar.

### <a name="return-value"></a>Valor devuelto

Número de caracteres necesarios para un búfer que puede contener datos codificados de *nSrcLen* bytes.

### <a name="remarks"></a>Observaciones

El esquema de codificación entrecomillado imprimible se describe en RFC 2045 ([https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)).

## <a name="uudecode"></a>UUDecode

Descodifica una cadena de datos que ha sido uuencode, como por una llamada anterior a [uuencode](#uuencode).

```
inline BOOL UUDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   BYTE* pbDest,
   int* pnDestLen) throw ();
```

### <a name="parameters"></a>Parámetros

*pbSrcData*<br/>
Cadena que contiene los datos que se van a descodificar.

*nSrcLen*<br/>
La longitud en bytes de *pbSrcData*.

*pbDest*<br/>
Búfer asignado por el llamador para recibir los datos descodificados.

*pnDestLen*<br/>
Puntero a una variable que contiene la longitud en bytes de *pbDest*. Si la función se ejecuta correctamente, la variable recibe el número de bytes escritos en el búfer. Si se produce un error en la función, la variable recibe la longitud necesaria en bytes del búfer.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Esta implementación de uuencoding sigue la especificación POSIX P versión 1003.2 b/D11.

## <a name="uudecodegetrequiredlength"></a>UUDecodeGetRequiredLength

Llame a esta función para obtener el tamaño en bytes de un búfer que puede contener datos descodificados de una cadena con codificación UUEncode de la longitud especificada.

```
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Parámetros

*nSrcLen*<br/>
Número de caracteres de la cadena codificada.

### <a name="return-value"></a>Valor devuelto

Número de bytes necesarios para un búfer que puede contener una cadena descodificada de caracteres *nSrcLen* .

### <a name="remarks"></a>Observaciones

Esta implementación de uuencoding sigue la especificación POSIX P versión 1003.2 b/D11.

## <a name="uuencode"></a>UUEncode

Llame a esta función para codificar datos con formato UUEncode.

```
inline BOOL UUEncode(
   const BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCTSTR lpszFile = _T("file"),
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>Parámetros

*pbSrcData*<br/>
Búfer que contiene los datos que se van a codificar.

*nSrcLen*<br/>
La longitud en bytes de los datos que se van a codificar.

*szDest*<br/>
Búfer asignado por el llamador para recibir los datos codificados.

*pnDestLen*<br/>
Puntero a una variable que contiene la longitud en caracteres de *szDest*. Si la función se ejecuta correctamente, la variable recibe el número de caracteres que se escriben en el búfer. Si se produce un error en la función, la variable recibe la longitud necesaria en caracteres del búfer.

*lpszFile*<br/>
Archivo que se va a agregar al encabezado cuando se especifica ATLSMTP_UUENCODE_HEADER en *dwFlags*.

*dwFlags*<br/>
Marcas que controlan el comportamiento de esta función.

- ATLSMTP_UUENCODE_HEADE el encabezado se codificará.

- ATLSMTP_UUENCODE_END se codificará el extremo.

- ATLSMTP_UUENCODE_DOT se realizará el material de datos.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Esta implementación de uuencoding sigue la especificación POSIX P versión 1003.2 b/D11.

## <a name="uuencodegetrequiredlength"></a>UUEncodeGetRequiredLength

Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.

```
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Parámetros

*nSrcLen*<br/>
El número de bytes de datos que se van a codificar.

### <a name="return-value"></a>Valor devuelto

Número de caracteres necesarios para un búfer que puede contener datos codificados de *nSrcLen* bytes.

### <a name="remarks"></a>Observaciones

Esta implementación de uuencoding sigue la especificación POSIX P versión 1003.2 b/D11.

## <a name="see-also"></a>Consulte también

[Conceptos](../active-template-library-atl-concepts.md)<br/>
[Componentes de escritorio COM de ATL](../atl-com-desktop-components.md)
