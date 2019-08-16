---
title: Límites del compilador
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: 9663da06c97886ef1cd20ca2928944795b39dc18
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222196"
---
# <a name="compiler-limits"></a>Límites del compilador

El estándar de C++ recomienda límites para varias construcciones del lenguaje. La siguiente es una lista de los casos donde Microsoft C++ compilador implementa los límites recomendados. El primer número es el límite que se ha establecido en la imagen ISO C++ estándar 11 (INCITS/ISO/IEC 14882-2011 [2012], anexo B) y el segundo número es el límite implementado por Microsoft C++ compilador:

- Niveles de anidamiento de instrucciones compuestas, estructuras de control de iteración y estructuras de control de selección - C++ estándar: 256, Microsoft C++ compilador: depende de la combinación de instrucciones que están anidadas, pero generalmente entre 100 y 110.

- Los parámetros en una definición de macro - C++ estándar: 256, Microsoft C++ compiler: 127.

- Argumentos en una llamada de macro - C++ estándar: 256, Microsoft C++ compilador 127.

- Caracteres en un carácter literal de cadena ancho o literal de cadena (después de la concatenación) - C++ estándar: 65536, Microsoft C++ compiler: 65535 caracteres de byte único, incluido el terminador NULL y 32767 caracteres de doble byte, incluido el terminador NULL.

- Niveles de clase anidada, estructura o unión definiciones en un único `struct-declaration-list` - C++ estándar: 256, Microsoft C++ compiler: 16.

- Inicializadores de miembro en una definición de constructor - C++ estándar: 6144, Microsoft C++ compilador: 6144 como mínimo.

- Clasificaciones de ámbito de un identificador - C++ estándar: 256, Microsoft C++ compiler: 127.

- Anidar **extern** especificaciones - C++ estándar: 1024, Microsoft C++ compiler: 9 (sin contar implícito **extern** especificación en el ámbito global o 10, si se cuenta implícito **extern** especificación en el ámbito global...

- Argumentos de plantilla en una declaración de plantilla - C++ estándar: 1024, Microsoft C++ compiler: 2046.

## <a name="see-also"></a>Vea también

[Comportamiento no estándar](../cpp/nonstandard-behavior.md)