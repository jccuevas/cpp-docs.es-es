---
title: "Clase de contenedor::erase | Microsoft Docs"
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
  - "erase (método)"
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Clase de contenedor::erase
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Este tema está en la documentación de Visual C\+\+ como ejemplo no funcional de contenedores utilizados en la biblioteca estándar de C\+\+.  Para obtener más información, vea [Contenedores STL](../standard-library/stl-containers.md).  
  
 Borra un elemento.  
  
## Sintaxis  
  
```  
  
      iterator erase(  
   iterator _Where   
);  
iterator erase(  
   iterator _First,  
   iterator _Last   
);  
```  
  
## Comentarios  
 La primera función miembro quita el elemento de la secuencia controlada designada por el \_Where \#\#\#. La segunda función miembro quita elementos de la secuencia controlada en el intervalo \[`_First`, `_Last`\).  Ambos devuelven un iterador que designa el primer elemento que permanece más allá de cualquier elemento quitado, o [final](../standard-library/container-class-end.md) si no existe ese elemento.  
  
 Las funciones miembro producen una excepción solo si una operación de copia se producirá una excepción.  
  
## Vea también  
 [Sample Container \(Clase\)](../standard-library/sample-container-class.md)