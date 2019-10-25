---
title: Intrínsecos del controlador
ms.date: 09/02/2019
helpviewer_keywords:
- intrinsics, compiler
- compiler intrinsics
- cl.exe compiler, performance
- cl.exe compiler, intrinsics
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
ms.openlocfilehash: 8c101de6d74a4f2d3073bd220a29f2a0328d2959
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216872"
---
# <a name="compiler-intrinsics"></a>Intrínsecos del controlador

La mayoría de las funciones está recogida en bibliotecas, pero algunas funciones están incorporadas en el compilador (es decir, son intrínsecas). Estas se conocen como funciones intrínsecas o intrínsecos.

## <a name="remarks"></a>Comentarios

Si una función es un intrínseco, el código de dicha función suele estar insertado, con lo que se evita la sobrecarga de una llamada de función y se emiten instrucciones de código máquina altamente eficientes para dicha función. Un intrínseco suele ser más rápido que el ensamblado en línea equivalente, ya que el optimizador tiene un conocimiento integrado de cómo se comportan numerosos intrínsecos, por lo que pueden estar disponibles algunas optimizaciones de las que no se dispone cuando se utiliza el código ensamblado en línea. Además, el optimizador puede expandir el intrínseco de forma diferente, alinear los búferes de forma diferente o realizar otros ajustes según el contexto y los argumentos de la llamada.

El uso de intrínsecos afecta a la portabilidad del código, ya que los intrínsecos que están disponibles en Visual C++ podrían no estar disponibles si el código se compila con otros compiladores, y algunos intrínsecos que podrían estar disponibles para ciertas arquitecturas de destino no están disponibles para todas las arquitecturas. Sin embargo, los intrínsecos son generalmente mucho más portátiles que el ensamblado en línea. Los intrínsecos son necesarios en las arquitecturas de 64 bits donde no se admite el ensamblado en línea.

Algunos intrínsecos, como `__assume` y `__ReadWriteBarrier`, proporcionan información al compilador, lo que afecta al comportamiento del optimizador.

Algunos intrínsecos están disponibles solo como tal, mientras que otros están disponibles en implementaciones de intrínseco y de función. Puede indicarle al compilador que utilice la implementación de intrínseco de dos maneras, en función de si desea habilitar solo funciones específicas o de si desea habilitar todos los intrínsecos. La primera consiste en usar `#pragma intrinsic(`la *función intrínseca-List*`)`-Name. La directiva pragma puede utilizarse para especificar un solo intrínseco o varios intrínsecos separados por comas. La segunda consiste en usar la opción del compilador [/OI (generar funciones intrínsecas)](../build/reference/oi-generate-intrinsic-functions.md) , que hace que todos los intrínsecos de una plataforma determinada estén disponibles. En **/OI**, use `#pragma function(` *intrínseca-function-Name-List* `)` para forzar el uso de una llamada de función en lugar de un intrínseco. Si la documentación de una expresión intrínseca concreta que la rutina solo está disponible como intrínseco, se usa la implementación intrínseca independientemente de si se especifica **/OI** o `#pragma intrinsic` . En todos los casos ,/OI `#pragma intrinsic` o permite, pero no fuerza, que el optimizador use el intrínseco. El optimizador todavía puede llamar a la función.

Algunas funciones de biblioteca estándar de C o C++ están disponibles en las implementaciones de intrínseco de algunas arquitecturas. Cuando se llama a una función de CRT, se utiliza la implementación intrínseca si se especifica **/OI** en la línea de comandos.

Hay disponible un archivo \<de encabezado, INTRIN. h >, que declara prototipos para las funciones intrínsecas comunes. Los intrínsecos específicos del fabricante están disponibles en \<los archivos de encabezado immintrin \<. h > y ammintrin. h >. Además, algunos encabezados de Windows declaran funciones que se asignan a un intrínseco del compilador.

En las secciones siguientes se enumeran todos los intrínsecos que están disponibles en varias arquitecturas. Para obtener más información acerca de cómo funcionan los intrínsecos en un procesador de destino determinado, consulte la documentación de referencia del fabricante.

- [Intrínsecos ARM](../intrinsics/arm-intrinsics.md)

- [lista de intrínsecos x86](../intrinsics/x86-intrinsics-list.md)

- [Lista de intrínsecos de x64 (amd64)](../intrinsics/x64-amd64-intrinsics-list.md)

- [Intrínsecos disponibles en todas las arquitecturas](../intrinsics/intrinsics-available-on-all-architectures.md)

- [Lista alfabética de funciones intrínsecas](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)

## <a name="see-also"></a>Vea también

[Referencia del ensamblador de ARM](../assembler/arm/arm-assembler-reference.md)<br/>
[Referencia de Microsoft macro Assembler](../assembler/masm/microsoft-macro-assembler-reference.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Referencia de la biblioteca en tiempo de ejecución de C](../c-runtime-library/c-run-time-library-reference.md)