---
title: Miembros de datos mutables (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- mutable_cpp
dev_langs:
- C++
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de0a208341e6a687d1319c4d8d60cc8671555dd6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107008"
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