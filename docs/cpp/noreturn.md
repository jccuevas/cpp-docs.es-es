---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: a30840aa0556a7324ba24c0f2aaec57dea88d082
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367864"
---
# <a name="noreturn"></a>noreturn

**Microsoft Specific**

Este **atributo __declspec** indica al compilador que una función no devuelve. Como consecuencia, el compilador sabe que el código que sigue a una llamada a una función **__declspec(noreturn)** es inalcanzable.

Si el compilador encuentra una función con una ruta de acceso de control que no devuelve un valor, genera una advertencia (C4715) o un mensaje de error (C2202). Si no se puede alcanzar la ruta de acceso de control debido a una función que nunca devuelve, puede usar **__declspec(noreturn)** para evitar esta advertencia o error.

> [!NOTE]
> Agregar **__declspec(noreturn)** a una función que se espera que se devuelva puede dar lugar a un comportamiento indefinido.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, la cláusula **else** no contiene una instrucción return.  Declarar `fatal` como **__declspec(noreturn)** evita un error o mensaje de advertencia.

```cpp
// noreturn2.cpp
__declspec(noreturn) extern void fatal () {}

int main() {
   if(1)
     return 1;
   else if(0)
     return 0;
   else
     fatal();
}
```

**END Microsoft Specific**

## <a name="see-also"></a>Consulte también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
