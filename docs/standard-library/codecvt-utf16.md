---
title: "codecvt_utf16 | Microsoft Docs"
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
  - "codecvt/std::codecvt_utf16"
  - "std::codecvt_utf16"
  - "std.codecvt_utf16"
  - "codecvt_utf16"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt_utf16 (clase)"
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt_utf16
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa un [Configuración regional](../standard-library/locale-class.md) faceta que convierte entre caracteres anchos codificados como UCS\-2 o UCS\-4 y una secuencia de bytes que se codifican como UTF\-16LE o UTF\-16LE.  
  
## Sintaxis  
  
```  
template<  
    class Elem,  
    unsigned long Maxcode = 0x10ffff,  
    codecvt_mode Mode = (codecvt_mode)0  
>  
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Elem`|Tipo de elemento de carácter ancho.|  
|`Maxcode`|El número máximo de caracteres para la faceta de configuración regional.|  
|`Mode`|Información de configuración de la faceta de configuración regional.|  
  
## Comentarios  
 Esta clase de plantilla convierte entre caracteres anchos codificados como UCS\-2 o UCS\-4 y una secuencia de bytes que se codifican como UTF\-16LE, si `Mode & little_endian`, o UTF\-16LE en caso contrario.  
  
 La secuencia de bytes que debe escribirse en un archivo binario; puede dañarse si se escribe en un archivo de texto.  
  
## Requisitos  
 **Encabezado:** \< codecvt \>  
  
 **Espacio de nombres:** std