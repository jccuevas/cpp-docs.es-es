---
title: Error del compilador C3365 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3365
dev_langs: C++
helpviewer_keywords: C3365
ms.assetid: 875ec3a4-522c-4e3d-9b67-48808b857f6d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a4185f2691f3f134ed1444200e1ad5793a4853d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3365"></a>Error del compilador C3365
El operador 'operator': diferencia de operandos de tipo 'type1' y 'type2'  
  
Se intentaron componer delegados con tipos diferentes.  Vea [Cómo: definir y utilizar delegados (C++ / CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md) para obtener más información sobre los delegados.  
  
## <a name="example"></a>Ejemplo  
El ejemplo siguiente genera la advertencia C3365:  
  
```cpp  
// C3365.cpp  
// compile with: /clr  
delegate void D1();  
delegate void D2(int);  
  
ref class R {  
public:  
   void f(){}  
   void g(int){}  
};  
  
int main() {  
   D1^ d1 = gcnew D1(gcnew R, &R::f);  
   D2^ d2 = gcnew D2(gcnew R, &R::g);  
   D1^ d3 = gcnew D1(gcnew R, &R::f);  
  
   d1 += d2;   // C3365  
   d1 += d3;   // OK  
   d1();  
}  
```