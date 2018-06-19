---
title: Referencia de codificación de ATL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- encoding
- encoding, functions
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d8cbb23c390a47b1bbfb7b1a78b327f07b06869
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358633"
---
# <a name="atl-encoding-reference"></a>Referencia de codificación en ATL
Codificación en un intervalo común de estándares de Internet, como uuencode, hexadecimal y UTF8 es compatible con el código que se encuentra en atlenc.h.  
  
### <a name="functions"></a>Funciones  
  
|||  
|-|-|  
|[AtlGetHexValue](reference/atl-text-encoding-functions.md#atlgethexvalue)|Llame a esta función para obtener el valor numérico de un dígito hexadecimal.|  
|[AtlHexDecode](reference/atl-text-encoding-functions.md#atlhexdecode)|Descodifica una cadena de datos que se ha codificado como texto hexadecimal, por ejemplo, mediante una llamada anterior a [AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode).|  
|[AtlHexDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexdecodegetrequiredlength)|Llame a esta función para obtener el tamaño en bytes de un búfer que puede contener datos descodificados de una cadena con codificación hexadecimal de la longitud especificada.|  
|[AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)|Llame a esta función para codificar algunos datos en forma de cadena de texto hexadecimal.|  
|[AtlHexEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexencodegetrequiredlength)|Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.|  
|[AtlUnicodeToUTF8](reference/atl-text-encoding-functions.md#atlunicodetoutf8)|Llame a esta función para convertir una cadena Unicode en UTF-8.|  
|[BEncode](reference/atl-text-encoding-functions.md#bencode)|Llame a esta función para convertir algunos datos utilizando la codificación “B”.|  
|[BEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#bencodegetrequiredlength)|Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.|  
|[EscapeXML](reference/atl-text-encoding-functions.md#escapexml)|Llame a esta función para convertir los caracteres que no son seguros para usarlos en XML en sus equivalentes seguros.|  
|[GetExtendedChars](reference/atl-text-encoding-functions.md#getextendedchars)|Llame a esta función para obtener el número de caracteres extendidos de una cadena.|  
|[IsExtendedChar](reference/atl-text-encoding-functions.md#isextendedchar)|Llame a esta función para comprobar si un carácter especificado es un carácter extendido (menor de 32, mayor que 126, y no una pestaña, un salto de línea o un retorno de carro).|  
|[QEncode](reference/atl-text-encoding-functions.md#qencode)|Llame a esta función para convertir algunos datos utilizando la codificación “Q”.|  
|[QEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qencodegetrequiredlength)|Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.|  
|[QPDecode](reference/atl-text-encoding-functions.md#qpdecode)|Descodifica una cadena de datos que se ha codificado en formato Entrecomillado imprimible, por ejemplo, mediante una llamada anterior a [QPEncode](reference/atl-text-encoding-functions.md#qpencode).|  
|[QPDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpdecodegetrequiredlength)|Llame a esta función para obtener el tamaño en bytes de un búfer que puede contener datos descodificados de una cadena con codificación entrecomillada imprimible de la longitud especificada.|  
|[QPEncode](reference/atl-text-encoding-functions.md#qpencode)|Llame a esta función para codificar algunos datos en formato entrecomillado imprimible.|  
|[QPEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpencodegetrequiredlength)|Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.|  
|[UUDecode](reference/atl-text-encoding-functions.md#uudecode)|Descodifica una cadena de datos con codificación uuencode, por ejemplo, mediante una llamada anterior a [UUEncode](reference/atl-text-encoding-functions.md#uuencode).|  
|[UUDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#uudecodegetrequiredlength)|Llame a esta función para obtener el tamaño en bytes de un búfer que puede contener datos descodificados de una cadena con codificación UUEncode de la longitud especificada.|  
|[UUEncode](reference/atl-text-encoding-functions.md#uuencode)|Llame a esta función para codificar datos con formato UUEncode.|  
|[UUEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#uuencodegetrequiredlength)|Llame a esta función para obtener el tamaño en caracteres de un búfer que puede contener una cadena codificada a partir de los datos con el tamaño especificado.|  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)   
 [Componentes de escritorio COM de ATL](../atl/atl-com-desktop-components.md)

