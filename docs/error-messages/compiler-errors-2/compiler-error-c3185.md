---
title: Error de compilador Error C3185 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3185
dev_langs:
- C++
helpviewer_keywords:
- C3185
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce6eea7c9a40f9dd38bf6892995eaa52ac540de7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256192"
---
# <a name="compiler-error-c3185"></a>Error C3185 de Error del compilador
'typeid' usado en un tipo ’type’ administrado o de WinRT; use 'operator' en su lugar  
  
 No se puede aplicar el [typeid](../../cpp/typeid-operator.md) operador administrada o WinRT escriba; use [typeid](../../windows/typeid-cpp-component-extensions.md) en su lugar.  
  
 El ejemplo siguiente genera el error C3185 y muestra cómo corregirlo:  
  
```  
// C3185a.cpp  
// compile with: /clr  
ref class Base {};  
ref class Derived : public Base {};  
  
int main() {  
   Derived ^ pd = gcnew Derived;  
   Base ^pb = pd;  
   const type_info & t1 = typeid(pb);   // C3185  
   System::Type ^ MyType = Base::typeid;   // OK  
};  
```  
