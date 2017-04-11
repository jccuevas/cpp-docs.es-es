---
title: "Las funciones de codificación de texto que ATL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ae1648b-2b87-4112-92aa-0069fcfd23da
caps.latest.revision: 3
translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: a7d4572f34a88192723c574e1b749947f76d819a
ms.lasthandoff: 03/31/2017

---
# <a name="atl-text-encoding-functions"></a>Las funciones de codificación de texto ATL
Estas funciones admiten texto de codificación y descodificación.

|||  
|-|-|  
|[AtlGetHexValue](#atlgethexvalue)|Llame a esta función para obtener el valor numérico de un dígito hexadecimal.|   
|[AtlGetVersion](#atlgetversion)|Llame a esta función para obtener la versión de la biblioteca ATL que está usando.  |  
|[AtlHexDecode](#atlhexdecode)|Descodifica una cadena de datos que se ha codificado como texto hexadecimal, por ejemplo, mediante una llamada anterior a [AtlHexEncode](#atlhexencode).|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|Llame a esta función para obtener el tamaño en bytes de un búfer que puede contener datos descodificados de una cadena con codificación hexadecimal de la longitud especificada.|
|[AtlHexEncode](#atlhexencode)|Llame a esta función para codificar algunos datos en forma de cadena de texto hexadecimal.|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.|
|[AtlHexValue](#atlhexvalue)|Llame a esta función para obtener el valor numérico de un dígito hexadecimal. |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|Llame a esta función para convertir una cadena Unicode en UTF-8. |
|[BEncode](#bencode)|Llame a esta función para convertir algunos datos utilizando la codificación “B”.|
|[BEncodeGetRequiredLength](#bencodegetrequiredlength)|Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.|
|[EscapeXML](#escapexml)|Llame a esta función para convertir los caracteres que no son seguros para usarlos en XML en sus equivalentes seguros.|
|[GetExtendedChars](#getextendedchars)|Llame a esta función para obtener el número de caracteres extendidos de una cadena.|
|[IsExtendedChar](#isextendedchar)|Llame a esta función para comprobar si un carácter especificado es un carácter extendido (menor de 32, mayor que 126, y no una pestaña, un salto de línea o un retorno de carro).|
|[QEncode](#qencode)|Llame a esta función para convertir algunos datos utilizando la codificación “Q”.  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.|
|[QPDecode](#qpdecode)|Descodifica una cadena de datos que se ha codificado en formato Entrecomillado imprimible, por ejemplo, mediante una llamada anterior a [QPEncode](#qpencode).|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|Llame a esta función para obtener el tamaño en bytes de un búfer que puede contener datos descodificados de una cadena con codificación entrecomillada imprimible de la longitud especificada.|
|[QPEncode](#qpencode)|Llame a esta función para codificar algunos datos en formato entrecomillado imprimible.|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.|
|[UUDecode](#uudecode)|Descodifica una cadena de datos con codificación uuencode, por ejemplo, mediante una llamada anterior a [UUEncode](#uuencode).|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|Llame a esta función para obtener el tamaño en bytes de un búfer que puede contener datos descodificados de una cadena con codificación UUEncode de la longitud especificada.|
|[UUEncode](#uuencode)|Llame a esta función para codificar datos con formato UUEncode. |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.|

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlenc.h  
 
## <a name="atlgethexvalue"></a>AtlGetHexValue
Llame a esta función para obtener el valor numérico de un dígito hexadecimal.  
  
```    
inline char AtlGetHexValue(char chIn) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 `chIn`  
 El carácter hexadecimal '0'-'9', 'A'-'F' o 'a'-'f'.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor numérico del carácter de entrada se interpreta como un dígito hexadecimal. Por ejemplo, una entrada de '0' Devuelve un valor de 0 y una entrada de 'A' Devuelve un valor de 10. Si el carácter de entrada no es un dígito hexadecimal, esta función devuelve -1.  
  
## <a name="atlgetversion"></a>AtlGetVersion
Llame a esta función para obtener la versión de la biblioteca ATL que está usando.  
  
```  
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pReserved`  
 Un puntero reservado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `DWORD` valor entero de la versión de la biblioteca ATL que se compilen o ejecuten.  
  
## <a name="example"></a>Ejemplo  
 Debe llamar a la función como se indica a continuación.  
  
 [!code-cpp[NVC_ATL_Utilities #95](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  

## <a name="atlhexdecode"></a>AtlHexDecode
Descodifica una cadena de datos que se ha codificado como texto hexadecimal, por ejemplo, mediante una llamada anterior a [AtlHexEncode](#atlhexencode).  
  
```    
inline BOOL AtlHexDecode(  
   LPCSTR pSrcData,  
   int nSrcLen,  
   LPBYTE pbDest,  
   int* pnDestLen) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 `pSrcData`  
 Cadena que contiene los datos que se desea descodificar.  
  
 `nSrcLen`  
 La longitud en caracteres de `pSrcData`.  
  
 `pbDest`  
 Búfer asignado por el autor de llamada para recibir los datos descodificados.  
  
 `pnDestLen`  
 Puntero a una variable que contiene la longitud en bytes de `pbDest`. Si la función se realiza correctamente, la variable recibe el número de bytes escritos en el búfer. Si se produce un error en la función, la variable recibe la longitud requerida en bytes del búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
## <a name="atlhexdecodegetrequiredlength"></a>AtlHexDecodeGetRequiredLength
Llame a esta función para obtener el tamaño en bytes de un búfer que puede contener datos descodificados de una cadena con codificación hexadecimal de la longitud especificada.  
  
```  
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 `nSrcLen`  
 El número de caracteres en la cadena codificada.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de bytes necesarios para un búfer que puede contener una cadena descodificada de `nSrcLen` caracteres.  
  
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
 `pbSrcData`  
 El búfer que contiene los datos que se desea codificar.  
  
 `nSrcLen`  
 La longitud en bytes de los datos que se desea codificar.  
  
 `szDest`  
 Búfer asignado por el autor de llamada para recibir los datos codificados.  
  
 `pnDestLen`  
 Puntero a una variable que contiene la longitud en caracteres de `szDest`. Si la función se realiza correctamente, la variable recibe el número de caracteres escritos en el búfer. Si se produce un error en la función, la variable recibe la longitud requerida en caracteres del búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Cada byte de datos de origen se codifica como 2 caracteres hexadecimales.  
  
## <a name="atlhexencodegetrequiredlength"></a>AtlHexEncodeGetRequiredLength
Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.  
  
```  
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 `nSrcLen`  
 El número de bytes de datos que se desea codificar.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de caracteres necesarios para un búfer que podría contener datos codificados de `nSrcLen` bytes.  
  
## <a name="atlhexvalue"></a>AtlHexValue
Llame a esta función para obtener el valor numérico de un dígito hexadecimal.  
  
```  
inline short AtlHexValue(char chIn) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 `chIn`  
 El carácter hexadecimal '0'-'9', 'A'-'F' o 'a'-'f'.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor numérico del carácter de entrada se interpreta como un dígito hexadecimal. Por ejemplo, una entrada de '0' Devuelve un valor de 0 y una entrada de 'A' Devuelve un valor de 10. Si el carácter de entrada no es un dígito hexadecimal, esta función devuelve -1.  
  
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
 *wszSrc*  
 La cadena Unicode que se va a convertir  
  
 `nSrc`  
 La longitud en caracteres de la cadena de Unicode.  
  
 `szDest`  
 Búfer asignado por el autor de llamada para recibir la cadena convertida.  
  
 `nDest`  
 La longitud en bytes del búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de caracteres de la cadena convertida.  
  
### <a name="remarks"></a>Comentarios  
 Para determinar el tamaño del búfer necesario para la cadena convertida, llame a esta función pasar un valor 0 `szDest` y `nDest`.  
  
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
 `pbSrcData`  
 El búfer que contiene los datos que se desea codificar.  
  
 `nSrcLen`  
 La longitud en bytes de los datos que se desea codificar.  
  
 `szDest`  
 Búfer asignado por el autor de llamada para recibir los datos codificados.  
  
 `pnDestLen`  
 Puntero a una variable que contiene la longitud en caracteres de `szDest`. Si la función se realiza correctamente, la variable recibe el número de caracteres escritos en el búfer. Si se produce un error en la función, la variable recibe la longitud requerida en caracteres del búfer.  
  
 `pszCharSet`  
 El conjunto que se usará para la conversión de caracteres.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 El esquema de codificación "B" se describe en RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).  
  
## <a name="bencodegetrequiredlength"></a>BEncodeGetRequiredLength 
Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.  
  
```  
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 `nSrcLen`  
 El número de bytes de datos que se desea codificar.  
  
 `nCharsetLen`  
 La longitud en caracteres del juego que se usará para la conversión de caracteres.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de caracteres necesarios para un búfer que podría contener datos codificados de `nSrcLen` bytes.  
  
### <a name="remarks"></a>Comentarios  
 El esquema de codificación "B" se describe en RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).  
  
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
 `szIn`  
 Cadena que se va a convertir.  
  
 *nSrclen*  
 La longitud en caracteres de la cadena que se va a convertir.  
  
 *szEsc*  
 Búfer asignado por el autor de llamada para recibir la cadena convertida.  
  
 *nDestLen*  
 La longitud en caracteres del búfer asignado por el llamador.  
  
 `dwFlags`  
 Marcas de ATL_ESC que describen cómo es realizar la conversión. 

- `ATL_ESC_FLAG_NONE`Comportamiento predeterminado. Comillas de cierre no se convierten las marcas y apóstrofos.
- `ATL_ESC_FLAG_ATTR`Comillas de cierre marcas y apóstrofos se convierten en `&quot;` y `&apos;` respectivamente.


  
### <a name="return-value"></a>Valor devuelto  
 La longitud en caracteres de la cadena convertida.  
  
### <a name="remarks"></a>Comentarios  
 Posibles conversiones realizadas por esta función se muestran en la tabla:  
  
|Origen|Destino|  
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
 `szSrc`  
 Cadena que se va a analizar.  
  
 `nSrcLen`  
 La longitud de la cadena en caracteres.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de caracteres extendidos que se encuentra dentro de la cadena según lo determinado por [IsExtendedChar](#isextendedchar).  
  
## <a name="isextendedchar"></a>IsExtendedChar
Llame a esta función para comprobar si un carácter especificado es un carácter extendido (menor de 32, mayor que 126, y no una pestaña, un salto de línea o un retorno de carro).  
  
```  
inline int IsExtendedChar(char ch) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 *CH*  
 El carácter que se va a probar  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el carácter se extiende, **FALSE** en caso contrario.  
  
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
 `pbSrcData`  
 El búfer que contiene los datos que se desea codificar.  
  
 `nSrcLen`  
 La longitud en bytes de los datos que se desea codificar.  
  
 `szDest`  
 Búfer asignado por el autor de llamada para recibir los datos codificados.  
  
 `pnDestLen`  
 Puntero a una variable que contiene la longitud en caracteres de `szDest`. Si la función se realiza correctamente, la variable recibe el número de caracteres escritos en el búfer. Si se produce un error en la función, la variable recibe la longitud requerida en caracteres del búfer.  
  
 `pszCharSet`  
 El conjunto que se usará para la conversión de caracteres.  
  
 *pnNumEncoded*  
 Un puntero a una variable que, en la devolución, contiene el número de caracteres no seguros que tenía que se va a convertir.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 El esquema de codificación "Q" se describe en RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).  
  
## <a name="qencodegetrequiredlength"></a>QEncodeGetRequiredLength 
Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.  
  
```  
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 `nSrcLen`  
 El número de bytes de datos que se desea codificar.  
  
 `nCharsetLen`  
 La longitud en caracteres del juego que se usará para la conversión de caracteres.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de caracteres necesarios para un búfer que podría contener datos codificados de `nSrcLen` bytes.  
  
### <a name="remarks"></a>Comentarios  
 El esquema de codificación "Q" se describe en RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).  
  
## <a name="qpdecode"></a>QPDecode
Descodifica una cadena de datos que se ha codificado en formato Entrecomillado imprimible, por ejemplo, mediante una llamada anterior a [QPEncode](#qpencode).  
  
```  
inline BOOL QPDecode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
   int* pnDestLen,  
   DWORD dwFlags = 0) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pbSrcData`  
 El búfer que contiene los datos que se desea descodificar.  
  
 [in] `nSrcLen`  
 La longitud en bytes de `pbSrcData`.  
  
 [out] `szDest`  
 Búfer asignado por el autor de llamada para recibir los datos descodificados.  
  
 [out] `pnDestLen`  
 Puntero a una variable que contiene la longitud en bytes de `szDest`. Si la función se realiza correctamente, la variable recibe el número de bytes escritos en el búfer. Si se produce un error en la función, la variable recibe la longitud requerida en bytes del búfer.  
  
 [in] `dwFlags`  
 Marcas que describen cómo es realizar la conversión. Vea [ATLSMTP_QPENCODE marcas](http://msdn.microsoft.com/library/6b15a3ab-8e57-49e4-8104-09b26ebb96c4).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si la operación se realiza correctamente; de lo contrario, devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El esquema de codificación Entrecomillado imprimible se describe en RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).  
  
## <a name="qpdecodegetrequiredlength"></a>QPDecodeGetRequiredLength
Llame a esta función para obtener el tamaño en bytes de un búfer que puede contener datos descodificados de una cadena con codificación entrecomillada imprimible de la longitud especificada.  
  
```  
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 `nSrcLen`  
 El número de caracteres en la cadena codificada.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de bytes necesarios para un búfer que puede contener una cadena descodificada de `nSrcLen` caracteres.  
  
### <a name="remarks"></a>Comentarios  
 El esquema de codificación Entrecomillado imprimible se describe en RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).  
  
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
 `pbSrcData`  
 El búfer que contiene los datos que se desea codificar.  
  
 `nSrcLen`  
 La longitud en bytes de los datos que se desea codificar.  
  
 `szDest`  
 Búfer asignado por el autor de llamada para recibir los datos codificados.  
  
 `pnDestLen`  
 Puntero a una variable que contiene la longitud en caracteres de `szDest`. Si la función se realiza correctamente, la variable recibe el número de caracteres escritos en el búfer. Si se produce un error en la función, la variable recibe la longitud requerida en caracteres del búfer.  
  
 `dwFlags`  
 Marcas ATLSMTP_QPENCODE que describen cómo es realizar la conversión. 
- `ATLSMTP_QPENCODE_DOT`Si un período aparece al principio de una línea, se se agregan a la salida como codificado.
- `ATLSMTP_QPENCODE_TRAILING_SOFT`Anexa `=\r\n` a la cadena codificada.

Se describe el esquema de codificación Entrecomillado imprimible en [RFC 2045](http://www.ietf.org/rfc/rfc2045.txt).
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 El esquema de codificación Entrecomillado imprimible se describe en RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).  
  
## <a name="qpencodegetrequiredlength"></a>QPEncodeGetRequiredLength
Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.  
  
```  
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>Parámetros  
 `nSrcLen`  
 El número de bytes de datos que se desea codificar.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de caracteres necesarios para un búfer que podría contener datos codificados de `nSrcLen` bytes.  
  
### <a name="remarks"></a>Comentarios  
 El esquema de codificación Entrecomillado imprimible se describe en RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).  
  
## <a name="uudecode"></a>UUDecode
Descodifica una cadena de datos con codificación uuencode, por ejemplo, mediante una llamada anterior a [UUEncode](#uuencode).  
  
```  
inline BOOL UUDecode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   BYTE* pbDest,  
   int* pnDestLen) throw ();  
```  
  
### <a name="parameters"></a>Parámetros  
 `pbSrcData`  
 Cadena que contiene los datos que se desea descodificar.  
  
 `nSrcLen`  
 La longitud en bytes de `pbSrcData`.  
  
 `pbDest`  
 Búfer asignado por el autor de llamada para recibir los datos descodificados.  
  
 `pnDestLen`  
 Puntero a una variable que contiene la longitud en bytes de `pbDest`. Si la función se realiza correctamente, la variable recibe el número de bytes escritos en el búfer. Si se produce un error en la función, la variable recibe la longitud requerida en bytes del búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta implementación de forma sigue la especificación de POSIX P1003.2b/D11.  
  
## <a name="uudecodegetrequiredlength"></a>UUDecodeGetRequiredLength
Llame a esta función para obtener el tamaño en bytes de un búfer que puede contener datos descodificados de una cadena con codificación UUEncode de la longitud especificada.  
  
```  
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>Parámetros  
 `nSrcLen`  
 El número de caracteres en la cadena codificada.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de bytes necesarios para un búfer que puede contener una cadena descodificada de `nSrcLen` caracteres.  
  
### <a name="remarks"></a>Comentarios  
 Esta implementación de forma sigue la especificación de POSIX P1003.2b/D11.  
  
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
 `pbSrcData`  
 El búfer que contiene los datos que se desea codificar.  
  
 `nSrcLen`  
 La longitud en bytes de los datos que se desea codificar.  
  
 `szDest`  
 Búfer asignado por el autor de llamada para recibir los datos codificados.  
  
 `pnDestLen`  
 Puntero a una variable que contiene la longitud en caracteres de `szDest`. Si la función se realiza correctamente, la variable recibe el número de caracteres escritos en el búfer. Si se produce un error en la función, la variable recibe la longitud requerida en caracteres del búfer.  
  
 *lpszFile*  
 El archivo que se agregará al encabezado si se especifica ATLSMTP_UUENCODE_HEADER en `dwFlags`.  
  
 `dwFlags`  
 Indicadores que controlan el comportamiento de esta función. 
- `ATLSMTP_UUENCODE_HEADE`El encabezado que se va a codificar.
- `ATLSMTP_UUENCODE_END`El extremo que se va a codificar.
- `ATLSMTP_UUENCODE_DOT`Se realizará el llenado de datos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta implementación de forma sigue la especificación de POSIX P1003.2b/D11.  
  
## <a name="uuencodegetrequiredlength"></a>UUEncodeGetRequiredLength
Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.  
  
```  
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>Parámetros  
 `nSrcLen`  
 El número de bytes de datos que se desea codificar.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de caracteres necesarios para un búfer que podría contener datos codificados de `nSrcLen` bytes.  
  
### <a name="remarks"></a>Comentarios  
 Esta implementación de forma sigue la especificación de POSIX P1003.2b/D11.  
  
### <a name="see-also"></a>Vea también  
 [Conceptos](../../atl/active-template-library-atl-concepts.md)   
 [Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)   
