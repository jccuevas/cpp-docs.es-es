---
title: "Corrección de dependencias en los datos internos de biblioteca | Microsoft Docs"
ms.custom: 
ms.date: 05/24/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- library internals in an upgraded Visual C++ project
- _Hash_seq in an upgraded Visual C++ project
ms.assetid: 493e0452-6ecb-4edc-ae20-b6fce2d7d3c5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e6bd85de7c5235dcee0547e982d10a7abde954d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fix-your-dependencies-on-library-internals"></a>Corrección de dependencias en los datos internos de biblioteca

Microsoft ha publicado el código fuente de la biblioteca estándar, la mayor parte de la biblioteca del entorno de ejecución de C y otras bibliotecas de Microsoft en muchas versiones de Visual Studio. Lo que se pretende es ayudarle a entender el comportamiento de las bibliotecas y a depurar código. Un efecto secundario de que se publique el código fuente de las bibliotecas es que algunas funciones, estructuras de datos y valores internos quedan expuestos, aunque no formen parte de la interfaz de la biblioteca. Normalmente tienen nombres que comienzan por dos caracteres de subrayado o por un carácter de subrayado seguido de una letra mayúscula: se trata de nombres que la biblioteca estándar de C++ reserva para las implementaciones. Estas funciones, estructuras de datos y valores son detalles de implementación que pueden cambiar, ya que las bibliotecas van evolucionando con el tiempo, por lo que se desaconseja establecer dependencias en ellos. Si lo hace, correrá el riesgo de obtener código no portátil y de sufrir problemas al intentar migrar el código a las nuevas versiones de las bibliotecas.  

En la mayoría de los casos, los documentos de novedades o de cambios importantes de cada versión de Visual Studio no reflejan cambios en los datos internos de las bibliotecas. Al fin y al cabo, se supone que no debe verse afectado por estos detalles de implementación. Sin embargo, a veces la tentación de recurrir al uso de parte del código que ve en la biblioteca es demasiado grande. En este tema se describen las dependencias de datos internos de CRT o de la biblioteca estándar que pueden haberse creado y cómo actualizar el código para quitar esas dependencias, de forma que sea más portátil o permita migrar a las nuevas versiones de la biblioteca.

## <a name="hashseq"></a>_Hash_seq  

La función de hash interna `std::_Hash_seq(const unsigned char *, size_t)`, que sirve para implementar `std::hash` en algunos tipos de cadenas, era visible en las versiones recientes de la biblioteca estándar. Esta función implementaba un elemento [hash FNV-1a]( https://en.wikipedia.org/wiki/Fowler%E2%80%93Noll%E2%80%93Vo_hash_function) en una secuencia de caracteres.  
  
Existen dos formas de quitar esta dependencia.  

-   Si lo que quiere es poner una secuencia `const char *` en un contenedor sin ordenar usando el mismo código hash que `basic_string`, puede hacerlo recurriendo a la sobrecarga de plantilla `std::hash`, que toma un elemento `std::string_view` que, a su vez, devuelve ese código hash en un formato portátil. El código de biblioteca de cadenas puede depender, o no, del uso de un hash FNV-1a en el futuro, por lo que esta es la mejor manera de evitar una dependencia de un algoritmo hash en particular. 
  
-   Si lo que pretende es generar un elemento hash FNV-1a sobre memoria arbitraria, hemos creado ese código y lo hemos puesto a su disposición en GitHub, en el repositorio [VCSamples]( https://github.com/Microsoft/vcsamples), en un archivo de encabezado independiente [fnv1a.hpp](https://github.com/Microsoft/VCSamples/tree/master/VC2015Samples/_Hash_seq), bajo una [licencia de MIT](https://github.com/Microsoft/VCSamples/blob/master/license.txt). También hemos incluido una copia aquí para su comodidad. Puede copiar este código en un archivo de encabezado, agregar el encabezado a cualquier código afectado y, después, buscar y reemplazar `_Hash_seq` por `fnv1a_hash_bytes`. Obtendrá exactamente el mismo comportamiento que la implementación interna en `_Hash_seq`. 

```cpp  
/*
VCSamples
Copyright (c) Microsoft Corporation
All rights reserved. 
MIT License
Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED *AS IS*, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
*/
#include <stddef.h>

inline size_t fnv1a_hash_bytes(const unsigned char * first, size_t count) {
#if defined(_WIN64)
    static_assert(sizeof(size_t) == 8, "This code is for 64-bit size_t.");
    const size_t fnv_offset_basis = 14695981039346656037ULL;
    const size_t fnv_prime = 1099511628211ULL;

#else /* defined(_WIN64) */
    static_assert(sizeof(size_t) == 4, "This code is for 32-bit size_t.");
    const size_t fnv_offset_basis = 2166136261U;
    const size_t fnv_prime = 16777619U;
#endif /* defined(_WIN64) */

    size_t result = fnv_offset_basis;
    for (size_t next = 0; next < count; ++next)
        {   // fold in another byte
        result ^= (size_t)first[next];
        result *= fnv_prime;
        }
    return (result);
}
```  
  
## <a name="see-also"></a>Vea también  
  
[Actualizar proyectos desde versiones anteriores de Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[Información general sobre posibles problemas de actualización (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)  
[Actualizar código a CRT universal](upgrade-your-code-to-the-universal-crt.md)  
