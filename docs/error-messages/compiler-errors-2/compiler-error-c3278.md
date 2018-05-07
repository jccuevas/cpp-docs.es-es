---
title: Error del compilador C3278 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3278
dev_langs:
- C++
helpviewer_keywords:
- C3278
ms.assetid: 56f818f5-85a6-4792-843b-54fe16327658
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b7f05916be060b9712f6ba1b1955b37da538afe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3278"></a>Error del compilador C3278
la llamada directa del método de interfaz o puro 'método' dará un error en tiempo de ejecución  
  
 Se realizó una llamada a un método de interfaz o a un método puro, y esto no está permitido.  
  
 El código siguiente genera el error C3278:  
  
```  
// C3278_2.cpp  
// compile with: /clr  
using namespace System;  
interface class I  
{  
   void vmf();  
};  
  
public ref class C: public I  
{  
public:  
   void vmf()  
   {  
      Console::WriteLine( "In C::vmf()" );  
      I::vmf(); // C3278  
   }  
  
};  
  
int main()  
{  
   C^ pC = gcnew C;  
   pC->vmf();  
}  
```