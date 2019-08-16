---
title: propiedad (C++)
ms.date: 11/04/2016
f1_keywords:
- property_cpp
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
ms.openlocfilehash: ece1016b7a18873dfa477b0f8b6ae4271a0f8001
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301492"
---
# <a name="property-c"></a>propiedad (C++)

**Específicos de Microsoft**

Este atributo se puede aplicar a los "miembros de datos virtuales" no estáticos en una definición de clase o estructura. El compilador trata a estos "miembros de datos virtuales" como miembros de datos y cambia sus referencias en las llamadas de función.

## <a name="syntax"></a>Sintaxis

```
   __declspec( property( get=get_func_name ) ) declarator
   __declspec( property( put=put_func_name ) ) declarator
   __declspec( property( get=get_func_name, put=put_func_name ) ) declarator
```

## <a name="remarks"></a>Comentarios

Cuando el compilador ve un miembro de datos declarado con este atributo a la derecha de un operador de selección de miembro ("**.**"o"**->**"), lo convierte a la operación un `get` o `put` función, dependiendo de si una expresión es un valor l o un valor r. En contextos más complicados, como "`+=`", se realiza una reescritura usan ambos `get` y `put`.

Este atributo se puede utilizar también en la declaración de una matriz vacía en una definición de clase o estructura. Por ejemplo:

```cpp
__declspec(property(get=GetX, put=PutX)) int x[];
```

La instrucción anterior indica que `x[]` se puede utilizar con uno o más índices de matriz. En este caso, `i=p->x[a][b]` se convertirá en `i=p->GetX(a, b)` y `p->x[a][b] = i` se convertirá en `p->PutX(a, b, i);`

**FIN de Específicos de Microsoft**

## <a name="example"></a>Ejemplo

```cpp
// declspec_property.cpp
struct S {
   int i;
   void putprop(int j) {
      i = j;
   }

   int getprop() {
      return i;
   }

   __declspec(property(get = getprop, put = putprop)) int the_prop;
};

int main() {
   S s;
   s.the_prop = 5;
   return s.the_prop;
}
```

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)