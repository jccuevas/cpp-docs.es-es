---
title: Error del compilador C3914 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3914
dev_langs:
- C++
helpviewer_keywords:
- C3914
ms.assetid: 8f3190e6-ee50-4916-9ecc-3b8748b2e1e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3818c54f3720bdff92280e04a4750ed1b4f238c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270705"
---
# <a name="compiler-error-c3914"></a>Error del compilador C3914
una propiedad predeterminada no puede ser estática  
  
Se ha declarado incorrectamente una propiedad de forma predeterminada.  Para obtener más información, consulte [Cómo: utilizar propiedades en C++ / CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md).  
  
## <a name="example"></a>Ejemplo  
El ejemplo siguiente genera C3914 y muestra cómo corregirlo.  
  
```  
// C3914.cpp  
// compile with: /clr /c  
ref struct X {  
   static property int default[int] {   // C3914  
   // try the following line instead  
   // property int default[int] {  
      int get(int) { return 0; }  
      void set(int, int) {}  
   }  
};  
```