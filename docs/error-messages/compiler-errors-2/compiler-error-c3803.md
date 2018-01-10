---
title: Error del compilador C3803 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3803
dev_langs: C++
helpviewer_keywords: C3803
ms.assetid: bad5fb9a-ed9a-4c15-96e7-cf06e200a50d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d1729991d1e8649e79a924fc61203bac57194696
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3803"></a>Error del compilador C3803
'property': propiedad tiene un tipo que no es compatible con uno de su descriptores de acceso 'descriptor de acceso'  
  
 El tipo de una propiedad definida con [propiedad](../../cpp/property-cpp.md) no coincide con el tipo de valor devuelto para una de sus funciones de descriptor de acceso.  
  
 El ejemplo siguiente genera C3803:  
  
```  
// C3803.cpp  
struct A  
{  
   __declspec(property(get=GetIt)) int i;  
   char GetIt()  
   {  
      return 0;  
   }  
  
   /*  
   // try the following definition instead  
   int GetIt()  
   {  
      return 0;  
   }  
   */  
}; // C3803  
  
int main()  
{  
}  
```