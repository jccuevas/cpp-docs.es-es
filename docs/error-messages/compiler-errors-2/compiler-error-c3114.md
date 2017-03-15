---
title: "Error del compilador C3114 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3114"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3114"
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3114
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'argumento': no es un argumento de atributo con nombre válido  
  
 Para que un miembro de datos de clase de atributos sea un argumento con nombre válido, no se debe marcar `static`, `const` ni `literal`.  Si es una propiedad, no debe ser `static` y debe tener descriptores de acceso get y set.  
  
 Para obtener más información, vea [propiedad](../../windows/property-cpp-component-extensions.md) y [Atributos definidos por el usuario](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3114.  
  
```  
// C3114.cpp  
// compile with: /clr /c  
public ref class A : System::Attribute {  
public:  
   static property int StaticProp {  
      int get();  
   }  
  
   property int Prop2 {  
      int get();  
      void set(int i);  
   }  
};  
  
[A(StaticProp=123)]   // C3114  
public ref class R {};  
  
[A(Prop2=123)]   // OK  
public ref class S {};  
```