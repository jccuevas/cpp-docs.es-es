---
title: "Error del compilador C2993 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2993"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2993"
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2993
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : tipo no válido para el parámetro de plantilla 'parámetro' sin tipo definido  
  
 No se puede declarar una plantilla sin un argumento de estructura o unión.  Utilice punteros para pasar estructuras y uniones como parámetros de plantilla.  
  
 El código siguiente genera el error C2993:  
  
```  
// C2993.cpp  
// compile with: /c  
// C2993 expected  
struct MyStruct {  
   int a;char b;  
};  
  
template <class T, struct MyStruct S>   // C2993  
  
// try the following line instead  
// template <class T, struct MyStruct * S>  
class CMyClass {};  
```  
  
 Este error también puede producirse como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003; no se permite el uso de parámetros de plantilla sin tipo definido de punto flotante.  El estándar C\+\+ no permite el uso de parámetros de plantilla sin tipo definido de punto flotante.  
  
 Si se trata de una plantilla de función, utilice un argumento de función para transferir el parámetro de plantilla sin tipo definido de punto flotante \(este código será válido en las versiones Visual Studio .NET 2003 y Visual Studio .NET de Visual C\+\+\).  Si se trata de una plantilla de clase, no hay una solución sencilla.  
  
```  
// C2993b.cpp  
// compile with: /c  
template<class T, float f> void func(T) {}   // C2993  
  
// OK  
template<class T>   void func2(T, float) {}  
```