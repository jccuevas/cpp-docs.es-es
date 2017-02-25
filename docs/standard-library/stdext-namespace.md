---
title: "stdext (Espacio de nombres) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_DEFINE_DEPRECATED_HASH_CLASSES (símbolo)"
  - "stdext (espacio de nombres)"
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# stdext (Espacio de nombres)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los miembros de los archivos de encabezado [\<hash\_map\>](../standard-library/hash-map.md) y [\<hash\_set\>](../standard-library/hash-set.md) no son parte del estándar ISO C\+\+. Por lo tanto, estos tipos y miembros se movieron del espacio de nombres `std` al espacio de nombres `stdext`, para seguir siendo compatibles con el estándar de C\+\+.  
  
 Al compilar con [\/Ze](../build/reference/za-ze-disable-language-extensions.md), que es el valor predeterminado, el compilador advertirá sobre el uso de `std` para los miembros de los archivos de encabezado \<hash\_map\> y \<hash\_set\>. Para deshabilitar la advertencia, use el pragma [warning](../preprocessor/warning.md).  
  
 Para que el compilador genere un error por el uso de `std` para los miembros de los archivos de encabezado \<hash\_map\> y \<hash\_set\> con **\/Ze**, agregue la siguiente directiva antes de \#include'ing en los archivos de encabezado de la biblioteca estándar de C\+\+.  
  
```  
#define _DEFINE_DEPRECATED_HASH_CLASSES 0  
```  
  
 Al compilar con **\/Za**, el compilador generará un error.  
  
## Vea también  
 [Información general de STL](../standard-library/cpp-standard-library-overview.md)