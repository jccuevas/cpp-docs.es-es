---
title: Ensamblador alineado (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C]
- inline assembler [C]
ms.assetid: 821acc77-60b1-434c-ba54-2ba930a25ab4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd380a9c10c2e1c8a5715a05b9a63cbd6c6df973
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051976"
---
# <a name="inline-assembler-c"></a>Ensamblador alineado (C)

**Específicos de Microsoft**

El ensamblador alineado permite incrustar instrucciones de lenguaje de ensamblado directamente en los programas de origen C sin realizar pasos adicionales de ensamblado y vínculo. El ensamblador alineado se compila en el compilador; por lo tanto, no se necesita un ensamblador independiente como Microsoft Macro Assembler (MASM).

Dado que el ensamblador alineado no requiere pasos de ensamblado y vínculo independientes y de vínculo, es más aconsejable que un ensamblador independiente. El código de ensamblado alineado puede utilizar cualquier nombre de variable o de función de C que esté en el ámbito, por lo que resulta fácil integrarlo con el código C del programa. Y, dado que el código de ensamblado se puede combinar con instrucciones de C, puede realizar tareas complicadas o imposibles solo en C.

La palabra clave `__asm` invoca el ensamblador alineado y puede aparecer siempre que una instrucción de C sea válida. No puede aparecer por sí sola. Debe ir seguida de una instrucción de ensamblado, un grupo de instrucciones entre llaves o, como mínimo, un par de llaves vacío. El término "bloque `__asm`" aquí hace referencia a cualquier instrucción o grupo de instrucciones, incluido o no entre llaves.

El código siguiente es un bloque `__asm` simple incluido entre llaves. (El código es una secuencia de prólogo de función personalizada).

```
__asm
{
   push ebp
   mov  ebp, esp
   sub  esp, __LOCAL_SIZE
}
```

Como alternativa, puede colocar `__asm` delante de cada instrucción de ensamblado:

```
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

Dado que la palabra clave `__asm` es un separador de la instrucción, también puede colocar las instrucciones de ensamblado en la misma línea:

```
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Atributos de función](../c-language/function-attributes.md)