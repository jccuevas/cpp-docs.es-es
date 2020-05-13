---
title: Límites del compilador
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: 9e61cae1638c87f03b6fa775552408961bde6859
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189587"
---
# <a name="compiler-limits"></a>Límites del compilador

El estándar de C++ recomienda límites para varias construcciones del lenguaje. A continuación se muestra una lista de casos en los C++ que el compilador de Microsoft no implementa los límites recomendados. El primer número es el límite que se establece en el estándar C++ ISO 11 (INCITS/ISO/IEC 14882-2011 [2012], anexo B) y el segundo número es el límite implementado por el C++ compilador de Microsoft:

- Niveles de anidamiento de instrucciones compuestas, estructuras de control de iteración y C++ estructuras de control de selección C++ : estándar: 256, compilador de Microsoft: depende de la combinación de instrucciones anidadas, pero por lo general entre 100 y 110.

- Parámetros en una definición de C++ macro: estándar: 256, C++ compilador de Microsoft: 127.

- Argumentos en una invocación de macros: estándar: 256, compilador 127 de C++ Microsoft C++ .

- Caracteres en un literal de cadena de caracteres o literal de cadena ancho (después de C++ la concatenación)- C++ estándar: 65536, compilador de Microsoft: 65535 caracteres de un solo byte, incluido el terminador null, y 32767 caracteres de doble byte, incluido el terminador null.

- Niveles de definiciones de clase anidada, estructura o unión en una única `struct-declaration-list` C++ estándar: 256, Microsoft C++ Compiler: 16.

- Inicializadores de miembro en una definición de C++ constructor: estándar: 6144 C++ , compilador de Microsoft: al menos 6144.

- Calificaciones de ámbito de un identificador: C++ estándar: 256, compilador de Microsoft C++ : 127.

- Especificaciones **extern** anidadas: C++ estándar: 1024, compilador de Microsoft C++ : 9 (sin contar la especificación **extern** implícita en el ámbito global, o 10, si se cuenta la especificación **extern** implícita en el ámbito global.

- Argumentos de plantilla en una declaración de C++ plantilla: estándar: 1024 C++ , compilador de Microsoft: 2046.

## <a name="see-also"></a>Consulte también

[Comportamiento no estándar](../cpp/nonstandard-behavior.md)
