---
title: "Error del compilador C3908 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3908"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3908"
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3908
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

nivel de acceso menos restrictivo que el de 'construcción'  
  
 Un método de descriptor de acceso de propiedad \(get o set\) no puede tener un nivel de acceso menos restrictivo que el especificado en la propia propiedad.  Ocurre lo mismo con los métodos de descriptor de acceso de evento.  
  
 Para obtener más información, vea [property](../../windows/property-cpp-component-extensions.md) y [event](../../windows/event-cpp-component-extensions.md).  
  
 El código siguiente genera el error C3908:  
  
```  
// C3908.cpp  
// compile with: /clr  
ref class X {  
protected:  
   property int i {  
   public:   // C3908 property i is protected   
      int get();  
   private:  
      void set(int);   // OK more restrictive  
   };  
};  
```