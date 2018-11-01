---
title: Miembros de datos mutables (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: 8d592eb97f70bfc26c075317c57ec4d5c78e3956
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514184"
---
# <a name="mutable-data-members-c"></a>Miembros de datos mutables (C++)

Esta palabra clave solo se puede aplicar a los miembros de datos no estáticos y no constantes de una clase. Si se declara un miembro de datos **mutable**, es legal para asignar un valor a este miembro de datos desde un **const** función miembro.

## <a name="syntax"></a>Sintaxis

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>Comentarios

Por ejemplo, el siguiente código se compilará sin errores porque `m_accessCount` se ha declarado como **mutable**y por lo tanto, se puede modificar mediante `GetFlag` aunque `GetFlag` es una función miembro const.

```cpp
// mutable.cpp
class X
{
public:
   bool GetFlag() const
   {
      m_accessCount++;
      return m_flag;
   }
private:
   bool m_flag;
   mutable int m_accessCount;
};

int main()
{
}
```

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)