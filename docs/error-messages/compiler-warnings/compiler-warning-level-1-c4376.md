---
title: "Advertencia del compilador (nivel 1) C4376 | Microsoft Docs"
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
  - "C4376"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4376"
ms.assetid: 5f202c74-9489-48fe-b36f-19cd882b1589
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4376
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el especificador de acceso 'especificador\_antiguo:' ya no se admite: utilice 'especificador\_nuevo:' en su lugar  
  
 Para obtener más información sobre cómo especificar la accesibilidad de tipos y miembros en los metadatos, vea [Visibilidad de tipos](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) y [Visibilidad de miembros](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility) en [Cómo: Definir y utilizar clases y structs](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4376.  
  
```  
// C4376.cpp  
// compile with: /clr /W1 /c  
public ref class G {  
public public:   // C4376  
   void m2();  
};  
  
public ref class H {  
public:   // OK  
   void m2();  
};  
```