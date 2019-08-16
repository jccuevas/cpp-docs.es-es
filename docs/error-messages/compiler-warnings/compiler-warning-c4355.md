---
title: Advertencia del compilador C4355
ms.date: 11/04/2016
f1_keywords:
- C4355
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
ms.openlocfilehash: 6b74c8dd5ce9860cb218d21790f12ba05e9be22f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151830"
---
# <a name="compiler-warning-c4355"></a>Advertencia del compilador C4355

'this': utilizado en la lista de inicializadores de miembro base

El **esto** puntero es válido únicamente en funciones miembro no estáticas. No se puede usar en la lista de inicializadores para una clase base.

Los constructores de clase base y miembros de clase se denominan antes **esto** constructor. De hecho, ha pasado un puntero a un objeto no construido a otro constructor. Si esos otros constructores tener acceso a los miembros o llamar a funciones miembro en esto, el resultado será undefined. No se debe usar el **esto** puntero hasta que finalice la construcción todas.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

El ejemplo siguiente genera C4355:

```
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