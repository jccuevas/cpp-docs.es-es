---
title: "codecvt_utf8_utf16 | Microsoft Docs"
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
  - "codecvt_utf8_utf16"
  - "codecvt/std::cvt_utf8_utf16"
  - "std::codecvt_utf8_utf16"
  - "std.codecvt_utf8_utf16"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt_utf8_utf16 (clase)"
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt_utf8_utf16
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa una faceta de [configuración regional](../standard-library/locale-class.md) que convierte entre caracteres anchos codificados como UTF\-16 y una secuencia de bytes codificada como UTF\-8.  
  
## Sintaxis  
  
```  
template<  
    class Elem,  
    unsigned long Maxcode = 0x10ffff,  
    codecvt_mode Mode = (codecvt_mode)0  
>  
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Elem`|El tipo de elemento de carácter ancho.|  
|`Maxcode`|El número de caracteres máximo para la faceta de la configuración regional.|  
|`Mode`|Información de configuración para la faceta de la configuración regional.|  
  
## Comentarios  
 La secuencia de bytes se puede escribir en un archivo binario o un archivo de texto.  
  
## Requisitos  
 codecvt \<de**Encabezado:** \>  
  
 **Espacio de nombres:** std