---
title: Advertencia del compilador C4355
ms.date: 11/04/2016
f1_keywords:
- C4355
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
ms.openlocfilehash: ddc0d1968ae373ff1e81c98a513e6f84fdb885e1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165332"
---
# <a name="compiler-warning-c4355"></a>Advertencia del compilador C4355

'this': utilizado en la lista de inicializadores de miembro base

El puntero **this** solo es válido dentro de las funciones miembro no estáticas. No se puede usar en la lista de inicializadores de una clase base.

Se llama a los constructores de clase base y a los constructores de miembros de clase antes de **este** constructor. En efecto, ha pasado un puntero a un objeto no construido a otro constructor. Si esos otros constructores obtienen acceso a los miembros o llaman a funciones miembro de este, el resultado será undefined. No debe utilizar el puntero **this** hasta que se haya completado toda la construcción.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

En el ejemplo siguiente se genera C4355:

```cpp
// C4355.cpp
// compile with: /w14355 /c
#include <tchar.h>

class CDerived;
class CBase {
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function() = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase {
public:
   CDerived() : CBase(this) {};   // C4355 "this" used in derived c'tor
   virtual void function() {};
};

CBase::~CBase() {
   m_pDerived -> function();
}

int main() {
   CDerived myDerived;
}
```
