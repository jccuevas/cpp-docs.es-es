---
title: noreturn | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noreturn_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6133fc70c5c2b8bb8f794746c1d5ca11be97b817
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031046"
---
# <a name="noreturn"></a>noreturn

## <a name="microsoft-specific"></a>Específicos de Microsoft

Esto **__declspec** atributo indica al compilador que no devuelve una función. Como consecuencia, el compilador sabe que el código después de una llamada a un **__declspec (noreturn)** función es inaccesible.

Si el compilador encuentra una función con una ruta de acceso de control que no devuelve un valor, genera una advertencia (C4715) o un mensaje de error (C2202). Si no se puede alcanzar la ruta de acceso de control debido a una función que nunca devuelve resultados, puede usar **__declspec (noreturn)** para evitar esta advertencia o error.

> [!NOTE]
>  Agregar **__declspec (noreturn)** a una función que se espera que devuelva puede provocar un comportamiento indefinido.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, la **else** cláusula no contiene una instrucción return.  Declarar `fatal` como **__declspec (noreturn)** evita un error o mensaje de advertencia.

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

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)