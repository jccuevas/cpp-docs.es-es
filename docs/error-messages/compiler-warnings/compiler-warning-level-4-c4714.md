---
title: Advertencia del compilador (nivel 4) C4714
ms.date: 11/04/2016
f1_keywords:
- C4714
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
ms.openlocfilehash: 8ea4212eaddf14546827728b31299063021a959f
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989637"
---
# <a name="compiler-warning-level-4-c4714"></a>Advertencia del compilador (nivel 4) C4714

función ' function ' marcada como __forceinline no insertada

Se seleccionó la función especificada para la expansión en línea, pero el compilador no realizó la inserción.

Aunque `__forceinline` es una indicación más segura del compilador que `__inline`, la inserción se sigue realizando a discreción del compilador, pero no se usa ninguna heurística para determinar las ventajas de insertar esta función.

En algunos casos, el compilador no insertará una función concreta por motivos mecánicos. Por ejemplo, el compilador no insertará:

- Una función si daría como resultado la combinación de SEH y C++ EH.

- Algunas funciones con objetos construidos de copia pasados por valor cuando-GX/EHs/EHa está activada.

- Funciones que devuelven un objeto que no se pudo desenredar por valor cuando-GX/EHs/EHa está activada.

- Funciones con ensamblado alineado al compilar sin-og/OX/o1/o2.

- Funciona con una lista de argumentos de variable.

- Función con una instrucción **try** (C++ control de excepciones).

En el ejemplo siguiente se genera C4714:

```cpp
// C4714.cpp
// compile with: /Ob1 /GX /W4
__forceinline void func1()
{
   try
   {
   }
   catch (...)
   {
   }
}

void func2()
{
   func1();   // C4714
}

int main()
{
}
```
