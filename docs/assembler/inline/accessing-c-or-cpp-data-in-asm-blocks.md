---
title: Acceso a datos de C o C++ en bloques __asm | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9e4b684c878e630de81ac712fab714dc09db5ff
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685042"
---
# <a name="accessing-c-or-c-data-in-asm-blocks"></a>Acceso a datos de C o C++ en bloques __asm

**Específicos de Microsoft**

Una gran ventaja del ensamblado insertado es la capacidad de hacer referencia a variables de C o C++ por nombre. Un bloque `__asm` puede hacer referencia a cualquier símbolo, incluidos los nombres de variables que esté en el ámbito donde aparece el bloque. Por ejemplo, si la variable C `var` está en el ámbito, la instrucción

```cpp
__asm mov eax, var
```

almacena el valor de `var` en EAX.

Si una clase, estructura o unión miembro tiene un nombre único, un `__asm` bloque puede hacer referencia a él con el nombre de miembro, sin especificar la variable o `typedef` nombre antes del período (**.**) operador. Si el nombre de miembro no es único, sin embargo, debe colocar una variable o un nombre `typedef` inmediatamente antes del operador de punto. Por ejemplo, los tipos de estructura del ejemplo siguiente comparten `same_name` como nombre de miembro:.

Si declara variables con los tipos

```cpp
struct first_type hal;
struct second_type oat;
```

todas las referencias al miembro `same_name` deben utilizar el nombre de variable porque `same_name` no es único. Pero el miembro `weasel` tiene un nombre único, por lo que se puede hacer referencia al mismo usando únicamente el nombre del miembro:

```cpp
// InlineAssembler_Accessing_C_asm_Blocks.cpp
// processor: x86
#include <stdio.h>
struct first_type
{
   char *weasel;
   int same_name;
};

struct second_type
{
   int wonton;
   long same_name;
};

int main()
{
   struct first_type hal;
   struct second_type oat;

   __asm
   {
      lea ebx, hal
      mov ecx, [ebx]hal.same_name ; Must use 'hal'
      mov esi, [ebx].weasel       ; Can omit 'hal'
   }
   return 0;
}
```

Observe que la omisión del nombre de variable es cuestión simplemente de comodidad de codificación. Se generan las mismas instrucciones de ensamblado tanto si el nombre de variable está presente como si no.

Puede tener acceso a los miembros de datos de C++ sin tener en cuenta las restricciones de acceso. Sin embargo, no se puede llamar a funciones miembro.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Uso de C o C++ en bloques __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>