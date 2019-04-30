---
title: Límites del compilador
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: a0c6041d326982dc9807355733cf714dcfa62ca8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399166"
---
# <a name="compiler-limits"></a>Límites del compilador

El estándar de C++ recomienda límites para varias construcciones del lenguaje. A continuación se muestra una lista de casos donde el compilador de Visual C++ no implementa los límites recomendados. El primer número es el límite establecido en el estándar ISO C++ 11 (INCITS/ISO/IEC 14882-2011[2012], Anexo B) y el segundo es el límite que implementa Visual C++:

- Niveles de anidamiento de instrucciones compuestas, estructuras de control de iteración y estructuras de control de selección - C++ estándar: 256, visual C++ compilador: depende de la combinación de instrucciones que están anidadas, pero generalmente entre 100 y 110.

- Los parámetros en una definición de macro - C++ estándar: 256, Visual C++ compiler: 127.

- Argumentos en una llamada de macro - C++ estándar: 256, visual C++ compilador 127.

- Caracteres en un carácter literal de cadena ancho o literal de cadena (después de la concatenación) - C++ estándar: 65536, Visual C++ compiler: 65535 caracteres de byte único, incluido el terminador NULL y 32767 caracteres de doble byte, incluido el terminador NULL.

- Niveles de clase anidada, estructura o unión definiciones en un único `struct-declaration-list` - C++ estándar: 256, Visual C++ compiler: 16.

- Inicializadores de miembro en una definición de constructor - C++ estándar: 6144, visual C++ compilador: 6144 como mínimo.

- Clasificaciones de ámbito de un identificador - C++ estándar: 256, Visual C++ compiler: 127.

- Anidar **extern** especificaciones - C++ estándar: 1024, Visual C++ compiler: 9 (sin contar implícito **extern** especificación en el ámbito global o 10, si se cuenta implícito **extern** especificación en el ámbito global...

- Argumentos de plantilla en una declaración de plantilla - C++ estándar: 1024, Visual C++ compiler: 2046.

## <a name="see-also"></a>Vea también

[Comportamiento no estándar](../cpp/nonstandard-behavior.md)