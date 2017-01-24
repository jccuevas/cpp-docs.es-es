---
title: "operator&gt; (&lt;sample container&gt;) | Microsoft Docs"
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
  - "std::operator>"
  - "std.>"
  - "std.operator>"
  - "operator>"
  - "std::>"
  - ">"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "> (operador), comparar objetos específicos"
  - "operador >"
ms.assetid: 49bd417a-3305-4ffa-9884-39d3904ed87d
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator&gt; (&lt;sample container&gt;)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Este tema está en la documentación de Visual C\+\+ como ejemplo no funcional de contenedores utilizados en la biblioteca estándar de C\+\+.  Para obtener más información, vea [Contenedores STL](../standard-library/stl-containers.md).  
  
 Overload **operador ?\>** para comparar dos objetos de clase de plantilla [Contenedor](../standard-library/sample-container-class.md).  
  
## Sintaxis  
  
```  
  
   template<class Ty>  
bool operator*gt;(  
   const Container <Ty>& _Left,  
   const Container <Ty>& _Right  
);  
```  
  
## Valor devuelto  
 Devuelve el \_Left \< de \_Right.  
  
## Vea también  
 [\<sample container\>](../standard-library/sample-container.md)