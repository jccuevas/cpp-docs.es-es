---
title: Miembros de datos mutables (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: db3a9594a77a9ada971213eaea74a9842bd96a54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179346"
---
# <a name="mutable-data-members-c"></a>Miembros de datos mutables (C++)

Esta palabra clave solo se puede aplicar a los miembros de datos no estáticos y no constantes de una clase. Si un miembro de datos se declara **mutable**, es válido asignar un valor a este miembro de datos a partir de una función miembro **const** .

## <a name="syntax"></a>Sintaxis

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>Observaciones

Por ejemplo, el código siguiente se compilará sin errores porque `m_accessCount` se ha declarado como **mutable**y, por lo tanto, se puede modificar mediante `GetFlag` aunque `GetFlag` sea una función miembro const.

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

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)
