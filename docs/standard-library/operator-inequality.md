---
title: "operator!= | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::!="
  - "!="
  - "std::operator!="
  - "std.operator!="
  - "std.!="
  - "operator!="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "!= (operador)"
  - "operador !="
  - "operator!="
ms.assetid: ef2be7f0-1c94-4edc-b65c-731fddd519f4
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator!=
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Este tema está en la documentación de Visual C\+\+ como ejemplo no funcional de contenedores utilizados en la biblioteca estándar de C\+\+.  Para obtener más información, vea [Contenedores STL](../standard-library/stl-containers.md).  
  
 Overload `operator!=` para comparar dos objetos de clase de plantilla [Contenedor](../standard-library/sample-container-class.md).  
  
## Sintaxis  
  
```  
  
   template<class Ty>  
bool operator!=(  
   const Container <Ty>& _Left,  
   const Container <Ty>& _Right  
);  
```  
  
## Valor devuelto  
 Devuelve \#\#\#\!\(\_Left **\=\=** `_Right`\).  
  
## Vea también  
 [\<sample container\>](../standard-library/sample-container.md)