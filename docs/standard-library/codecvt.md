---
title: "&lt; codecvt &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "codecvt"
  - "std::<codecvt>"
  - "std.<codecvt>"
  - "<codecvt>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt (encabezado)"
ms.assetid: d44ee229-00d5-4761-9b48-0c702122789d
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; codecvt &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define varias clases de plantilla que se describen los objetos basados en la clase de plantilla [codecvt](../standard-library/codecvt-class.md). Estos objetos pueden actuar como [facetas de configuración regional](../standard-library/locale-class.md#facet_class) que controlar las conversiones entre una secuencia de valores de tipo `Elem` y una secuencia de valores de tipo `char`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <codecvt>  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Las facetas de configuración regional declaradas en este encabezado conversión entre varias codificaciones de caracteres. Para los caracteres anchos (almacenados en el programa en enteros de tamaño fijo):  
  
-   UCS-4 está codificado dentro del programa en Unicode (ISO 10646)  
  
-   UCS-4 es Unicode (ISO 10646) codificado dentro del programa como un entero de 32 bits.  
  
-   UCS-2 es Unicode codificado dentro del programa  
  
-   UCS-2 es Unicode codificada con el programa como un entero de 16 bits.  
  
-   UTF-16 es Unicode codificada con el programa como una  
  
-   UTF-16 es Unicode codificada con el programa como uno o dos enteros de 16 bits. (Tenga en cuenta que esto no cumple todos los requisitos de una codificación de caracteres anchos válida para el estándar de C o C++ estándar. No obstante se usa ampliamente como tal.)  
  
 Para las secuencias de bytes (almacenadas en un archivo, transmite como una secuencia de bytes o dentro del programa en una matriz de `char`):  
  
-   UTF-8 es la codificación Unicode  
  
-   UTF-8 es Unicode codificada en una secuencia de bytes como uno o más bytes de 8 bits con un orden de bytes deterministas.  
  
-   UTF-16LE está codificado en Unicode  
  
-   UTF-16LE es Unicode codificada con una secuencia de bytes como UTF-16 con cada entero de 16 bits aparece como dos bytes de ocho bits, menos byte significativo en primer lugar.  
  
-   UTF-16LE está codificado en Unicode  
  
-   UTF-16LE es Unicode codificada con una secuencia de bytes como UTF-16 con cada entero de 16 bits aparece como dos bytes de ocho bits, byte más significativo en primer lugar.  
  
### <a name="enumerations"></a>Enumeraciones  
  
|||  
|-|-|  
|[codecvt_mode](../Topic/%3Ccodecvt%3E%20enums.md#codecvt_mode_enumeration)|Especifica la información de configuración de facetas de configuración regional.|  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[codecvt_utf8](../Topic/%3Ccodecvt%3E%20functions.md#codecvt_utf8)|Representa una faceta de configuración regional que convierte entre caracteres anchos codificados como UCS-2 o UCS-4 y una secuencia de bytes codificada en UTF-8.|  
|[codecvt_utf8_utf16](%3Ccodecvt%3E%20functions.md#codecvt_utf8_utf16)|Representa una faceta de configuración regional que convierte entre codificados como UTF-16 de caracteres anchos y una secuencia de bytes codificada en UTF-8.|  
|[codecvt_utf16](../Topic/%3Ccodecvt%3E%20functions.md#codecvt_utf16)|Representa una faceta de configuración regional que convierte entre caracteres anchos codificados como UCS-2 o UCS-4 y una secuencia de bytes que se codifican como UTF-16LE o UTF-16LE.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< codecvt>  
  
 **Espacio de nombres:** stdt  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)




