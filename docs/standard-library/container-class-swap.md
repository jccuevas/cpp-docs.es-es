---
title: "Clase de contenedor::swap | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "swap (método)"
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Clase de contenedor::swap
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Este tema está en la documentación de Visual C\+\+ como ejemplo no funcional de contenedores utilizados en la biblioteca estándar de C\+\+.  Para obtener más información, vea [Contenedores STL](../standard-library/stl-containers.md).  
  
 Cambia las secuencias controladas entre **\*this** y `_Right`.  
  
## Sintaxis  
  
```  
  
      void swap(  
   Container& _Right  
);  
```  
  
## Comentarios  
 Si **get\_allocator \=\=** `_Right`**.get\_allocator**, lo hace así en tiempo constante.  Si no, realiza varias asignaciones de elementos y el constructor llama proporcional al número de elementos de las dos secuencias controladas.  
  
## Vea también  
 [Sample Container \(Clase\)](../standard-library/sample-container-class.md)