---
title: Compilador advertencia (nivel 4) C4682 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4682
dev_langs: C++
helpviewer_keywords: C4682
ms.assetid: 858ea157-1244-4a61-85df-97b3de43d418
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d367203113ea8fad20cd914d381b4c941856d6b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4682"></a>Advertencia del compilador (nivel 4) C4682
'parameter': no se especificó ningún atributo de parámetro direccional y se establece en [in] de forma predeterminada  
  
 Un método sobre un parámetro de una interfaz con atributos no posee uno de los atributos direccionales: [in](../../windows/in-cpp.md) o [out](../../windows/out-cpp.md). El parámetro de establece de forma predeterminada en in.  
  
 De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.  
  
 El ejemplo siguiente genera la advertencia C4682:  
  
```  
// C4682.cpp  
// compile with: /W4  
#pragma warning(default : 4682)  
#include <windows.h>  
[module(name="MyModule")];  
  
[ library_block, object, uuid("c54ad59d-d516-41dd-9acd-afda17565c2b") ]  
__interface IMyIface : IUnknown  
{  
   HRESULT f1(int i, int *pi); // C4682  
   // try the following line  
   // HRESULT f1([in] int i, [in] int *pi);  
};  
  
int main()  
{  
}  
```