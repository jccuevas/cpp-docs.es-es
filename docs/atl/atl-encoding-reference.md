---
title: "Referencia de codificaci&#243;n en ATL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codificar"
  - "codificar, funciones"
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
caps.latest.revision: 8
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Referencia de codificaci&#243;n en ATL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La codificación en un intervalo de estándares de internet comunes como uuencode, hexadecimal, y UTF8 admitida por el código encontrado en atlenc.h.  
  
### Funciones  
  
|||  
|-|-|  
|[AtlGetHexValue](../Topic/AtlGetHexValue.md)|Llame a esta función para obtener el valor numérico de un dígito hexadecimal.|  
|[AtlHexDecode](../Topic/AtlHexDecode.md)|Descodifica una cadena de datos que se ha codificado como texto hexadecimal como por una llamada anterior a [AtlHexEncode](../Topic/AtlHexEncode.md).|  
|[AtlHexDecodeGetRequiredLength](../Topic/AtlHexDecodeGetRequiredLength.md)|Llame a esta función para obtener el tamaño en bytes de un búfer que podría contener datos descodificados de una cadena hex. \- codificada de la longitud especificada.|  
|[AtlHexEncode](../Topic/AtlHexEncode.md)|Llame a esta función para codificar algunos datos como una cadena de texto hexadecimal.|  
|[AtlHexEncodeGetRequiredLength](../Topic/AtlHexEncodeGetRequiredLength.md)|Llame a esta función para obtener el tamaño en caracteres de un búfer que podría contener una cadena codificada de datos del tamaño especificado.|  
|[AtlUnicodeToUTF8](../Topic/AtlUnicodeToUTF8.md)|Llame a esta función para convertir una cadena Unicode en UTF\-8.|  
|[BEncode](../Topic/BEncode.md)|Llame a esta función para convertir algunos datos mediante la codificación de “b”.|  
|[BEncodeGetRequiredLength](../Topic/BEncodeGetRequiredLength.md)|Llame a esta función para obtener el tamaño en caracteres de un búfer que podría contener una cadena codificada de datos del tamaño especificado.|  
|[EscapeXML](../Topic/EscapeXML.md)|Llame a esta función para convertir los caracteres que no es seguro para el uso en XML a sus equivalentes seguros.|  
|[GetExtendedChars](../Topic/GetExtendedChars.md)|Llame a esta función para obtener el número de caracteres extendidos en una cadena.|  
|[IsExtendedChar](../Topic/IsExtendedChar.md)|Llame a esta función para comprobar si un carácter especificado es un carácter extendido \(menos de 32, mayor que 126, y no una pestaña, un avance de línea o un retorno de carro\)|  
|[QEncode](../Topic/QEncode.md)|Llame a esta función para convertir algunos datos mediante la codificación de “q”.|  
|[QEncodeGetRequiredLength](../Topic/QEncodeGetRequiredLength.md)|Llame a esta función para obtener el tamaño en caracteres de un búfer que podría contener una cadena codificada de datos del tamaño especificado.|  
|[QPDecode](../Topic/QPDecode.md)|Descodifica una cadena de datos codificado en formato citar\-imprimible como por una llamada anterior a [QPEncode](../Topic/QPEncode.md).|  
|[QPDecodeGetRequiredLength](../Topic/QPDecodeGetRequiredLength.md)|Llame a esta función para obtener el tamaño en bytes de un búfer que podría contener datos descodificados de la cadena citar\-imprimible\-codificada de la longitud especificada.|  
|[QPEncode](../Topic/QPEncode.md)|Llame a esta función para codificar algunos datos en formato citar\-imprimible.|  
|[QPEncodeGetRequiredLength](../Topic/QPEncodeGetRequiredLength.md)|Llame a esta función para obtener el tamaño en caracteres de un búfer que podría contener una cadena codificada de datos del tamaño especificado.|  
|[uudecode](../Topic/UUDecode.md)|Descodifica una cadena de datos que uuencoded por ejemplo por una llamada anterior a [uuencode](../Topic/UUEncode.md).|  
|[UUDecodeGetRequiredLength](../Topic/UUDecodeGetRequiredLength.md)|Llame a esta función para obtener el tamaño en bytes de un búfer que podría contener datos descodificados de una cadena uuencoded de la longitud especificada.|  
|[uuencode](../Topic/UUEncode.md)|Llame a esta función en uuencode algunos datos.|  
|[UUEncodeGetRequiredLength](../Topic/UUEncodeGetRequiredLength.md)|Llame a esta función para obtener el tamaño en caracteres de un búfer que podría contener una cadena codificada de datos del tamaño especificado.|  
  
### Macros  
  
|||  
|-|-|  
|[ATL\_ESC marca](../Topic/ATL_ESC%20Flags.md)|Estos marcadores se utilizan para controlar el comportamiento de [EscapeXML](../Topic/EscapeXML.md).|  
|[Marcadores de ATLSMTP\_QPENCODE](../Topic/ATLSMTP_QPENCODE%20Flags.md)|Estos marcadores describen cómo la codificación citar\-imprimible debe ser realizada por [QPEncode](../Topic/QPEncode.md).|  
|[Marcadores de ATLSMTP\_UUENCODE](../Topic/ATLSMTP_UUENCODE%20Flags.md)|Estos marcadores describen cómo el uuencoding debe realizarse por [uuencode](../Topic/UUEncode.md).|  
  
## Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)   
 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)