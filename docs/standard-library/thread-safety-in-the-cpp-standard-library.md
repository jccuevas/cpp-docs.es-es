---
title: "Seguridad para subprocesos en la biblioteca est&#225;ndar de C++ | Microsoft Docs"
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
  - "Biblioteca estándar de C++, seguridad para subprocesos"
  - "seguridad para subprocesos"
  - "seguridad para subprocesos, Biblioteca de plantillas estándar"
ms.assetid: 9351c8fb-4539-4728-b0e9-226e2ac4284b
caps.latest.revision: 21
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Seguridad para subprocesos en la biblioteca est&#225;ndar de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las siguientes normas de seguridad de subprocesos se aplican a todas las clases de la biblioteca estándar de C\+\+, lo que incluye `shared_ptr`, como se describe a continuación.  A veces se ofrecen mayores garantías, por ejemplo, los objetos iostream estándar, como se describe a continuación, y tipos diseñados específicamente para el multithreading, como los de [\<atomic\>](../standard-library/atomic.md).  
  
 Un objeto es seguro para subprocesos para leer desde múltiples subprocesos.  Por ejemplo, dado un objeto A, es seguro leer A desde el subproceso 1 y desde el subproceso 2 simultáneamente.  
  
 Si un subproceso está escribiendo un objeto, todas las lecturas y escrituras a este objeto del mismo subproceso o de otro deben protegerse.  Por ejemplo, dado un objeto A, si el subproceso 1 está escribiendo a A, debe evitarse que el subproceso 2 lea o escriba en A.  
  
 Es seguro leer y escribir una instancia de un tipo incluso si otro subproceso está leyendo o escribiendo una instancia diferente del mismo tipo.  Por ejemplo, dados los objetos A y B del mismo tipo, es seguro que A se esté escribiendo en el subproceso 1 y B se esté leyendo en el subproceso 2.  
  
## shared\_ptr  
 Varios subprocesos pueden leer y escribir simultáneamente diferentes objetos [shared\_ptr](../standard-library/shared-ptr-class.md), incluso cuando los objetos son copias que comparten la propiedad.  
  
## iostream  
 Los objetos iostream estándar `cin`, `cout`, `cerr`, `clog`, `wcin`, `wcout`, `wcerr` y `wclog` siguen las mismas normas que las otras clases, con esta excepción: es seguro escribir un objeto desde varios subprocesos.  Por ejemplo, el subproceso 1 puede escribir [cout](../Topic/cout.md) al mismo tiempo que el subproceso 2.  Sin embargo, esto puede causar que la salida de los dos subprocesos se combine.  
  
> [!NOTE]
>  Leer desde un búfer de secuencia no se considera una operación de lectura.  En lugar de eso, se considera que es una operación de escritura, porque el estado de la clase cambia.  
  
## Vea también  
 [Información general de STL](../standard-library/cpp-standard-library-overview.md)