---
title: Error del compilador C2396 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2396
dev_langs:
- C++
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd9007d15cb5b6f9badf8f0962c8c1aa29df5bf7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197460"
---
# <a name="compiler-error-c2396"></a>Error del compilador C2396
' your_type '': CLR o WinRT functionnot de conversión definida por el usuario válida. Debe convertir de o a: 'T^', 'T^%', 'T^&', donde T = 'your_type'  
  
 Una función de conversión en un tipo administrado o de Windows Runtime no tenía al menos un parámetro con un tipo igual al tipo que contiene la función de conversión.  
  
 El siguiente ejemplo genera el error C2396 y muestra cómo corregirlo:  
  
```  
// C2396.cpp  
// compile with: /clr /c  
  
ref struct Y {  
   static operator int(char c);   // C2396  
  
   // OK  
   static operator int(Y^ hY);  
   // or  
   static operator Y^(char c);  
};  
```