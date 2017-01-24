---
title: "Error del compilador C3227 | Microsoft Docs"
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
  - "C3227"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3227"
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3227
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'parámetro' : no se puede utilizar 'palabra clave' para asignar un tipo genérico  
  
 Para crear instancias de un tipo, se requiere un constructor adecuado.  Sin embargo, el compilador no puede garantizar que está disponible uno.  
  
 Puede utilizar plantillas en vez de genéricos para corregir este error o usar uno de los diversos métodos con el fin de crear un instancia del tipo.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3227.  
  
```  
// C3227.cpp  
// compile with: /clr /c  
generic<class T> interface class ICreate {  
   static T Create();  
};  
  
generic <class T>  
where T : ICreate<T>  
ref class C {  
   void f() {  
      T t = new T;   // C3227  
  
      // OK  
      T t2 = ICreate<T>::Create();  
      T t3 = safe_cast<T>( System::Activator::CreateInstance(T::typeid) );  
   }  
};  
```