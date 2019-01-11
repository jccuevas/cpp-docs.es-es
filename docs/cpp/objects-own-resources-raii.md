---
title: Recursos propios de los objetos (RAII)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f86b484e-5a27-4c3b-a92a-dfaa5dd6d93a
ms.openlocfilehash: 5705fc1996343141b13e37d1267b2e8c981c1eba
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220431"
---
# <a name="objects-own-resources-raii"></a>Recursos propios de los objetos (RAII)

Asegúrese de que los recursos propios objetos. Este principio es que también se denomina "resource acquisition is initialization" o "RAII."

## <a name="example"></a>Ejemplo

Pasar todos los objetos "nuevo" como un argumento de constructor a otro objeto con nombre que pertenece (casi siempre unique_ptr).

```cpp
void f() {
    unique_ptr<widget> p( new widget() );
    my_class x( new widget() );
    // ...
} // automatic destruction and deallocation for both widget objects
  // automatic exception safety, as if "finally { p->dispose(); x.w.dispose(); }"
```

Pasar siempre inmediatamente cualquier recurso nuevo a otro objeto que lo posee.

```cpp
void g() {
    other_class y( OpenFile() );
    // ...
} // automatic closing and release for file resource
  // automatic exception safety, as if "finally { y.file.dispose(); }"
```

## <a name="see-also"></a>Vea también

[Aquí está otra vez C++ (C++ moderno)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
