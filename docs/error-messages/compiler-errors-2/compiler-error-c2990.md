---
title: Error del compilador C2990
ms.date: 11/04/2016
f1_keywords:
- C2990
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
ms.openlocfilehash: 16c111a0fb8608615abaee495680fa38920b6c77
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447348"
---
# <a name="compiler-error-c2990"></a>Error del compilador C2990

'class': tipo de no clase como ya se ha sido declarado como tipo de clase

La clase de plantilla o no genéricos vuelve a definir una clase genérica o de plantilla. Compruebe los archivos de encabezado de conflictos.

El ejemplo siguiente genera el error C2990:

```
// C2990.cpp
// compile with: /c
template <class T>
class C{};
class C{};   // C2990
```

C2990 también puede producirse al usar genéricos:

```
// C2990b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC;

ref struct GC {};   // C2990
```

C2990 también puede producirse debido a un cambio importante en Microsoft C++ compilador para Visual Studio 2005; Ahora, el compilador requiere que sea idéntica con respecto a la especificación de la plantilla varias declaraciones para el mismo tipo.

El ejemplo siguiente genera el error C2990:

```
// C2990c.cpp
// compile with: /c
template<class T>
class A;

template<class T>
struct A2 {
   friend class A;   // C2990
};

// OK
template<class T>
struct B {
   template<class T>
   friend class A;
};
```