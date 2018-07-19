---
title: Límites del compilador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecf3351180fbff4d6872c7027eee90b92e560059
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37938904"
---
# <a name="compiler-limits"></a>Límites del compilador
El estándar de C++ recomienda límites para varias construcciones del lenguaje. A continuación se muestra una lista de casos donde el compilador de Visual C++ no implementa los límites recomendados. El primer número es el límite establecido en el estándar ISO C++ 11 (INCITS/ISO/IEC 14882-2011[2012], Anexo B) y el segundo es el límite que implementa Visual C++:  
  
-   Niveles de anidamiento de instrucciones compuestas, estructuras de control de iteración y selección de controlan las estructuras: estándar de C++: 256, compilador de Visual C++: depende de la combinación de instrucciones que están anidadas, pero generalmente entre 100 y 110.  
  
-   Los parámetros en una definición de macro: estándar de C++: 256, compilador de Visual C++: 127.  
  
-   Argumentos en una llamada de macro: estándar de C++: 256, el compilador de Visual C++ 127.  
  
-   Caracteres en un carácter literal de cadena ancho o literal de cadena (después de la concatenación) - estándar de C++: 65536, compilador de Visual C++: 65535 caracteres de byte único, incluido el terminador NULL y 32767 caracteres de doble byte, incluido el terminador NULL.  
  
-   Niveles de clase anidada, estructura o unión definiciones en un único `struct-declaration-list` -estándar de C++: 256, compilador de Visual C++: 16.  
  
-   Inicializadores de miembro en una definición de constructor: estándar de C++: 6144, compilador de Visual C++: 6144 como mínimo.  
  
-   Clasificaciones de ámbito de un identificador: estándar de C++: 256, compilador de Visual C++: 127.  
  
-   Anidar **extern** especificaciones - estándar de C++: 1024, el compilador de Visual C++: 9 (sin contar implícito **extern** especificación en el ámbito global o 10, si se cuenta implícito **extern**  especificación en el ámbito global...  
  
-   Argumentos de plantilla en una declaración de plantilla: estándar de C++: 1024, el compilador de Visual C++: 2046.  
  
## <a name="see-also"></a>Vea también  
 [Comportamiento no estándar](../cpp/nonstandard-behavior.md)