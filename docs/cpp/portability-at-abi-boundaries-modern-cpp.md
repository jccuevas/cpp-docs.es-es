---
title: "Portabilidad en los l&#237;mites de ABI (C++ moderno) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Portabilidad en los l&#237;mites de ABI (C++ moderno)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Tipos suficientemente portables en uso y convenciones de los límites binarios de la interfaz.  Un “portable tipo” es tipo integrado de C\/C\+\+. o struct que sólo contiene tipos integrados de C.  Los tipos de clase pueden utilizar solo cuando el llamador y el destinatario coinciden con diseño, la convención de llamada, etc. Esto sólo es posible cuando ambos se compilan con el compilador y las opciones del compilador.  
  
## Cómo aplanar una clase para la portabilidad de C  
 Cuando los llamadores pueden compilarse con otro compilador\/lenguaje, después “quitar información de estructura jerárquica” a extern “C” API con una convención de llamada concreta:  
  
```cpp  
// class widget {  
//   widget();  
//   ~widget();  
//   double method( int, gadget& );  
// };  
extern “C” {    // functions using explicit “this”  
  struct widget;   // + opaque type (fwd decl only)  
  widget* STDCALL widget_create();    // ctor → create new  “this”  
  void STDCALL widget_destroy( widget* );    // dtor → consume “this”  
  double STDCALL widget_method( widget*, int, gadget* );    // method → use “this”  
}  
  
```  
  
## Vea también  
 [Aquí está otra vez C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C\+\+](../standard-library/cpp-standard-library-reference.md)