---
title: "Problemas comunes de migraci&#243;n a 64 bits en Visual C++ | Microsoft Docs"
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
  - "portabilidad de código de 32 bits [C++]"
  - "aplicaciones de 64 bits [C++]"
  - "compilador de 64 bits [C++], migración"
  - "compilador de 64 bits [C++], trasladar código de 32 bits"
  - "programación de 64 bits [C++], migración"
  - "migración [C++], problemas de código de 64 bits"
  - "trasladar código de 32 bits a código de 64 bits"
  - "actualizar aplicaciones de Visual C++, código de 32 bits"
  - "Win64 [C++]"
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Problemas comunes de migraci&#243;n a 64 bits en Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al utilizar Visual C\+\+ para crear aplicaciones que se ejecutan en un sistema operativo Windows de 64 bits, debe tener en cuenta lo siguiente:  
  
-   `int` y `long` son valores de 32 bits en sistemas operativos Windows de 64 bits.  Debe tener cuidado de no asignar punteros a variables de 32 bits en los programas que piense compilar para plataformas de 64 bits.  Los punteros son de 64 bits en las plataformas de 64 bits; si asigna un puntero a una variable de 32 bits, se truncará su valor.  
  
-   `size_t`, `time_t` y  `ptrdiff_t` son valores de 64 bits en sistemas operativos Windows de 64 bits.  
  
-   `time_t` es un valor de 32 bits en sistemas de operativos Windows de 32 bits en las versiones de Visual C\+\+ anteriores a Visual C\+\+ 2005.  `time_t` es ahora un entero de 64 bits de forma predeterminada.  Para más información, vea [Administración de la duración](../c-runtime-library/time-management.md).  
  
     Debe tener en cuenta los lugares en que el código toma un valor `int` y lo procesa como valor `size_t` o `time_t`.  Es posible que el número aumente hasta superar un número de 32 bits y que los datos se trunquen al volver a pasarlo al almacenamiento `int`.  
  
 El modificador `printf` %x \(`int` en formato hexadecimal\) no funcionará según lo esperado en un sistema operativo Windows de 64 bits.  Sólo operará en los primeros 32 bits del valor que se le pasa.  
  
-   Use % I32x para presentar un tipo entero de 32 bits en formato hexadecimal.  
  
-   Use % I32x para presentar un tipo entero de 64 bits en formato hexadecimal.  
  
-   El modificador %p \(un puntero en formato hexadecimal\) funcionará según lo esperado en un sistema operativo Windows de 64 bits.  
  
 Para obtener más información, consulte:  
  
-   [Opciones del compilador](../build/reference/compiler-options.md)  
  
-   [\<caps:sentence id\="tgt18" sentenceid\="8228b16e9fef41dbba1af1d78bf0cc87" class\="tgtSentence"\>Sugerencias de migración\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/aa384214)  
  
## Vea también  
 [Configurar programas de 64 bits](../build/configuring-programs-for-64-bit-visual-cpp.md)   
 [Trasladar un programa](http://msdn.microsoft.com/es-es/c36c44b3-5a9b-4bb4-9b7a-469aa770ed00)