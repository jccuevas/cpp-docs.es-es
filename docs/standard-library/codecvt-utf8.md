---
title: "codecvt_utf8 | Microsoft Docs"
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
  - "std.codecvt_utf8"
  - "std::codecvt_utf8"
  - "codecvt_utf8"
  - "codecvt/std::codecvt_utf8"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt_utf8 (clase)"
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt_utf8
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa una faceta de [configuración regional](../standard-library/locale-class.md) que convierte entre caracteres anchos codificados como UCS\-2 o UCS\-4, y una secuencia de bytes codificada como UTF\-8.  
  
## Sintaxis  
  
```  
template<  
    class Elem,  
    unsigned long Maxcode = 0x10ffff,  
    codecvt_mode Mode = (codecvt_mode)0  
>  
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>  
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