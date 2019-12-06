---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: f9ca61c9d734ccdd6b8d8374ed3a7c4128ee3d5e
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857377"
---
# <a name="noreturn"></a>noreturn

**Específicos de Microsoft**

Este **__declspec** atributo indica al compilador que una función no devuelve. Como consecuencia, el compilador sabe que el código que sigue a una llamada a una función **__declspec (noreturn)** no es accesible.

Si el compilador encuentra una función con una ruta de acceso de control que no devuelve un valor, genera una advertencia (C4715) o un mensaje de error (C2202). Si no se puede tener acceso a la ruta de acceso del control debido a una función que no devuelve nunca, puede usar **__declspec (noreturn)** para evitar esta advertencia o error.

> [!NOTE]
>  Agregar **__declspec (noreturn)** a una función que se espera que devuelva puede dar lugar a un comportamiento indefinido.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, la cláusula **else** no contiene una instrucción return.  La declaración de `fatal` como **__declspec (noreturn)** evita un mensaje de error o de advertencia.

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

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)