---
title: "Clase de contenedor::reference | Microsoft Docs"
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
helpviewer_keywords: 
  - "reference (método)"
ms.assetid: ab85a9fb-c628-4761-9a5f-a0231fad7690
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Clase de contenedor::reference
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Este tema está en la documentación de Visual C\+\+ como ejemplo no funcional de contenedores utilizados en la biblioteca estándar de C\+\+.  Para obtener más información, vea [Contenedores STL](../standard-library/stl-containers.md).  
  
 Describe un objeto que puede actuar como referencia a un elemento de la secuencia controlada.  
  
## Sintaxis  
  
```  
  
typedef T2 reference;  
  
```  
  
## Comentarios  
 Se describe aquí como sinónimo del tipo sin especificar **T2** \(normalmente **Alloc::reference**\).  Un objeto de **reference** tipo se pueda convertir en un objeto de [const\_reference](../standard-library/container-class-const-reference.md)escrito.  
  
## Vea también  
 [Sample Container \(Clase\)](../standard-library/sample-container-class.md)