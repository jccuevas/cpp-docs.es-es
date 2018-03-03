---
title: Error del compilador C2384 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2384
dev_langs:
- C++
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a7494c38c787a0e0877496a8f65556d568d77f7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2384"></a>Error del compilador C2384
'member': no se puede aplicar __declspec(thread) a un miembro de una clase WinRT o administrada  
  
 El [subproceso](../../cpp/thread.md) `__declspec` modificador no se puede usar en un miembro de una clase administrada o una clase en tiempo de ejecución de Windows.  
  
 El almacenamiento local para el subproceso estático solo puede usarse con DLL cargadas estáticamente; la DLL debe cargarse de manera estática al iniciarse el proceso. El tiempo de ejecución de Windows no admite el almacenamiento local para el subproceso.  
  
 La siguiente línea genera C2384 y muestra cómo corregirlo en código C++/CLI:  
  
```  
// C2384.cpp  
// compile with: /clr /c  
public ref class B {  
public:  
   __declspec( thread ) static int tls_i = 1;   // C2384  
  
   // OK - declare with attribute instead  
   [System::ThreadStaticAttribute]  
   static int tls_j;  
};  
```