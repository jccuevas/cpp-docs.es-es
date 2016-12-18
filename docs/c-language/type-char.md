---
title: "Tipo char | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "char (palabra clave) [C]"
  - "tipo char"
  - "unsigned char (palabra clave) [C]"
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tipo char
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tipo `char` se usa para almacenar el valor entero de un miembro del juego de caracteres que se puede representar.  Ese valor entero es el código ASCII correspondiente al carácter especificado.  
  
 **Específicos de Microsoft**  
  
 Los valores de carácter de tipo `unsigned char` tienen un intervalo de 0 a 0xFF hexadecimal.  **signed char** tiene un intervalo de 0x80 a 0x7F.  Estos intervalos se traducen a 0 a 255 decimal y –128 a \+127 decimal, respectivamente.  La opción del compilador \/J cambia el valor predeterminado de **signed** a `unsigned`.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md)