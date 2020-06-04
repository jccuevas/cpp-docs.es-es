---
title: __super
ms.date: 11/04/2016
f1_keywords:
- __super_cpp
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
ms.openlocfilehash: b6f6a7e108224ab4c97893104c5d6c38d325fa42
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160832"
---
# <a name="__super"></a>__super

**Específicos de Microsoft**

Permite establecer explícitamente que se está llamando a una implementación de la clase base para una función que se va a reemplazar.

## <a name="syntax"></a>Sintaxis

```
__super::member_function();
```

## <a name="remarks"></a>Observaciones

Todos los métodos accesibles de la clase base se consideran durante la fase de la resolución de sobrecarga y la función que proporciona la mejor coincidencia es la que se llama.

**__super** solo puede aparecer dentro del cuerpo de una función miembro.

**__super** no se puede usar con una declaración using. Vea [usar declaración](../cpp/using-declaration.md) para obtener más información.

Con la introducción de [atributos](../windows/attributes/attributes-alphabetical-reference.md) que insertan código, es posible que el código contenga una o varias clases base cuyos nombres no sepa pero que contengan métodos a los que desea llamar.

## <a name="example"></a>Ejemplo

```cpp
// deriv_super.cpp
// compile with: /c
struct B1 {
   void mf(int) {}
};

struct B2 {
   void mf(short) {}

   void mf(char) {}
};

struct D : B1, B2 {
   void mf(short) {
      __super::mf(1);   // Calls B1::mf(int)
      __super::mf('s');   // Calls B2::mf(char)
   }
};
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)
