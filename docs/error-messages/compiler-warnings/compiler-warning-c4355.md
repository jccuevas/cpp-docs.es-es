---
title: Advertencia del compilador C4355 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4355
dev_langs:
- C++
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b7194431235e1bf375d4e6b99b66bf9a4b32e63a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4355"></a>Advertencia del compilador C4355
'this': utilizado en la lista de inicializadores de miembro base  
  
 El **esto** puntero es válido únicamente en funciones miembro no estáticas. No se puede usar en la lista de inicializadores para una clase base.  
  
 Los constructores de clase base y los constructores de miembro de clase se llama antes de **esto** constructor. En efecto, ha pasado un puntero a un objeto no construido a otro constructor. Si esos otros constructores tener acceso a los miembros o llamar a funciones miembro en el objeto, el resultado será indefinido. No debe utilizar el **esto** puntero hasta que finalicen todas las operaciones de construcción.  
  
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