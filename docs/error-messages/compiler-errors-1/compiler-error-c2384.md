---
title: "Compiler Error C2384 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2384"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2384"
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# Compiler Error C2384
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member': no se puede aplicar \_\_declspec\(thread\) a un miembro de una clase WinRT o administrada  
  
 El modificador [thread](../../cpp/thread.md) `__declspec` no se puede utilizar en un miembro de una clase administrada o una clase de Windows en tiempo de ejecución.  
  
 El almacenamiento local para el subproceso estático solo puede usarse con DLL cargadas estáticamente; la DLL debe cargarse de manera estática al iniciarse el proceso.  El tiempo de ejecución de Windows no admite el almacenamiento local para el subproceso.  
  
 La siguiente línea genera C2384 y muestra cómo corregirlo en código C\+\+\/CLI:  
  
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