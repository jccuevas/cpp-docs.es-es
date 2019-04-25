---
title: Error del compilador C3227
ms.date: 11/04/2016
f1_keywords:
- C3227
helpviewer_keywords:
- C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
ms.openlocfilehash: b175b14af55a9a462e040f064cc6e38d13fffb94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173995"
---
# <a name="compiler-error-c3227"></a>Error del compilador C3227

'parámetro': no se puede usar 'keyword' para asignar un tipo genérico

Para crear una instancia de un tipo, se requiere un constructor adecuado. Sin embargo, el compilador no es capaz de garantizar que esté disponible un constructor adecuado.

Puede usar las plantillas en lugar de los genéricos para resolver este error, o puede usar varios métodos para crear una instancia del tipo.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3227.

```
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