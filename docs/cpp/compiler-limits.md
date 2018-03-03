---
title: "Límites del compilador | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf668ddfa1c2d7e62ca10963827056f9661b83f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-limits"></a>Límites del compilador
El estándar de C++ recomienda límites para varias construcciones del lenguaje. A continuación se muestra una lista de casos donde el compilador de Visual C++ no implementa los límites recomendados. El primer número es el límite establecido en el estándar ISO C++ 11 (INCITS/ISO/IEC 14882-2011[2012], Anexo B) y el segundo es el límite que implementa Visual C++:  
  
-   Niveles de anidamiento de instrucciones compuestas, estructuras de control de iteración y selección del controlan estructuras - estándar de C++: 256, compilador de Visual C++: depende de la combinación de instrucciones que están anidadas, pero suele estar entre 100 y 110.  
  
-   Parámetros de definición de una macro - estándar de C++: 256, compilador de Visual C++: 127.  
  
-   Argumentos de invocación de una macro - estándar de C++: 256, el compilador de Visual C++ 127.  
  
-   Literal de cadena ancho o literal de cadena de caracteres en un carácter (después de la concatenación) - estándar de C++: 65536, compilador de Visual C++: 65535 caracteres de byte único, incluido el `null` terminador y 32767 caracteres de doble byte, incluida la `null` terminador.  
  
-   Niveles de clase anidada, una estructura o unión definiciones en un único equipo `struct-declaration-list` -estándar de C++: 256, compilador de Visual C++: 16.  
  
-   Inicializadores de miembro en una definición de constructor - estándar de C++: 6144, compilador de Visual C++: 6144 como mínimo.  
  
-   Definir el ámbito de requisitos de un identificador - estándar de C++: 256, compilador de Visual C++: 127.  
  
-   Anidar `extern` especificaciones - estándar de C++: 1024, compilador de Visual C++: 9 (sin contar la parte implícita `extern` especificación en el ámbito global o 10, si el recuento de la parte implícita `extern` especificación en el ámbito global...  
  
-   Argumentos de plantilla en una declaración de plantilla: estándar de C++: 1024, compilador de Visual C++: 2046.  
  
## <a name="see-also"></a>Vea también  
 [Comportamiento no estándar](../cpp/nonstandard-behavior.md)