---
title: Error del compilador C3227
ms.date: 11/04/2016
f1_keywords:
- C3227
helpviewer_keywords:
- C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
ms.openlocfilehash: 460000531dba77e42379199f276c9e2e02f43a9b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743424"
---
# <a name="compiler-error-c3227"></a>Error del compilador C3227

' parámetro ': no se puede usar ' palabra clave ' para asignar un tipo genérico

Para crear una instancia de un tipo, se requiere un constructor adecuado. Sin embargo, el compilador no puede garantizar que un constructor adecuado esté disponible.

Puede usar plantillas en lugar de genéricos para resolver este error, o puede usar uno de varios métodos para crear una instancia del tipo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3227.

```cpp
// C3227.cpp
// compile with: /clr /c
generic<class T> interface class ICreate {
   static T Create();
};

generic <class T>
where T : ICreate<T>
ref class C {
   void f() {
      T t = new T;   // C3227

      // OK
      T t2 = ICreate<T>::Create();
      T t3 = safe_cast<T>( System::Activator::CreateInstance(T::typeid) );
   }
};
```
