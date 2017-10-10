---
title: Error del compilador C2842 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2842
dev_langs:
- C++
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 3998ff0b07ba78228ac51bccac047d8889ccf81b
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

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

