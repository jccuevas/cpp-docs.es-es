---
title: Error del compilador C2842 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2842
dev_langs:
- C++
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe0a95edfa484eb8606b914424e52483c4c1c52d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245301"
---
# <a name="compiler-error-c2842"></a>Error del compilador C2842
'class': un tipo de WinRT o administrado no puede definir su propio 'operator new' u 'operator delete'  
  
 Puede definir sus propios ** operador new o **operador delete** para administrar la asignación de memoria en el montón nativo. Sin embargo, las clases de referencia no pueden definir estos operadores porque solo se asignan en el montón administrado.  

  
 Para obtener más información, consulte [operadores definidos por el usuario (C++ / CLI)](../../dotnet/user-defined-operators-cpp-cli.md).  
  
## <a name="example"></a>Ejemplo  
 El código siguiente genera el error C2842.  
  
```  
// C2842.cpp  
// compile with: /clr /c  
ref class G {  
   void* operator new( size_t nSize );   // C2842  
};  
```  
