---
title: "operator== (&lt;sample container&gt;) | Microsoft Docs"
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
  - "std.=="
  - "std::=="
  - "operator=="
  - "std.operator=="
  - "std::operator=="
  - "=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "== (operador), con objetos específicos de la biblioteca estándar de C++"
  - "operador ==, contenedores"
  - "operator==, contenedores"
ms.assetid: d3d8754e-5157-4b8b-bf9c-da41856f5eed
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator== (&lt;sample container&gt;)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Este tema está en la documentación de Visual C\+\+ como ejemplo no funcional de contenedores utilizados en la biblioteca estándar de C\+\+.  Para obtener más información, vea [Contenedores STL](../standard-library/stl-containers.md).  
  
 Overload `operator==` para comparar dos objetos de clase de plantilla [Contenedor](../standard-library/sample-container-class.md).  
  
## Sintaxis  
  
```  
  
   template<class Ty>  
bool operator==(  
   const Container <Ty>& _Left,  
   const Container <Ty>& _Right  
);  
```  
  
## Valor devuelto  
 Devuelve `_Left`\#\#\#.[tamaño](../standard-library/container-class-size.md) **\=\=** `_Right`**.size && equal**\(\_Left \#\#\#. [inicio](../standard-library/container-class-begin.md), `_Left`.  *[final](../standard-library/container-class-end.md), \_Right***.begin**\).  
  
## Vea también  
 [\<sample container\>](../standard-library/sample-container.md)