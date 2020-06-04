---
title: propiedad (C++)
ms.date: 11/04/2016
f1_keywords:
- property_cpp
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
ms.openlocfilehash: 03f71739698fd20a01fd72567ce5b9babc176327
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179307"
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

## <a name="remarks"></a>Observaciones

Cuando el compilador ve un miembro de datos declarado con este atributo a la derecha de un operador de selección de miembro (" **.** " o " **->** "), convierte la operación en una función `get` o `put`, en función de si dicha expresión es un valor l o un valor r. En contextos más complicados, como "`+=`", una reescritura se lleva a cabo en `get` y `put`.

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

## <a name="see-also"></a>Consulte también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
