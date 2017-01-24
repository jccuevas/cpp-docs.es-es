---
title: "L&#237;mites del compilador | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador), límites para constructores de lenguaje"
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# L&#237;mites del compilador
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El estándar de C\+\+ recomienda límites para varias construcciones del lenguaje.  A continuación se muestra una lista de casos donde el compilador de Visual C\+\+ no implementa los límites recomendados.  El primer número es el límite establecido en el estándar ISO C\+\+ 11 \(INCITS\/ISO\/IEC 14882\-2011\[2012\], Anexo B\) y el segundo es el límite que implementa Visual C\+\+:  
  
-   Niveles de anidamiento de instrucciones compuestas, estructuras de control de la iteración y estructuras de control de selección \[estándar de C\+\+: 256\] \(Compilador de Visual C\+\+: depende de la combinación de instrucciones que estén anidadas, pero suele ser entre 100 y 110\).  
  
-   Parámetros en una definición de macro \[estándar de C\+\+: 256\] \(Compilador de Visual C\+\+: 127\).  
  
-   Argumentos en una llamada de macro \[estándar de C\+\+: 256\] \(Compilador de Visual C\+\+ 127\).  
  
-   Caracteres en un literal de cadena de caracteres o literal de cadena ancho \(después de la concatenación\) \[estándar de C\+\+: 65536\] \(Compilador de Visual C\+\+: 65.535 caracteres de un solo byte, incluido el terminador `null`, y 32.767 caracteres de doble byte, incluido el terminador `null`\).  
  
-   Niveles de definiciones de clase anidada, estructura o unión en una sola lista `struct-declaration-list` \[estándar de C\+\+: 256\] \(Compilador de Visual C\+\+: 16\).  
  
-   Inicializadores de miembro en una definición de constructor \[estándar de C\+\+: 6144\] \(Compilador de Visual C\+\+: 6.144 como mínimo\).  
  
-   Clasificaciones de ámbito de un identificador \[estándar de C\+\+: 256\] \(Compilador de Visual C\+\+: 127\).  
  
-   Especificaciones de `extern` anidadas \[estándar de C\+\+: 1024\] \(Compilador de Visual C\+\+: 9 \(sin contar la especificación de `extern` implícita en el ámbito global, o 10, si se cuenta la especificación de `extern` implícita en el ámbito global\).  
  
-   Argumentos de plantilla en una declaración de plantilla \[estándar de C\+\+: 1024\] \(Compilador de Visual C\+\+: 2046\).  
  
## Vea también  
 [Comportamiento no estándar](../cpp/nonstandard-behavior.md)