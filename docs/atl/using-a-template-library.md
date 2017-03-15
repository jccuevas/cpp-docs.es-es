---
title: "Using a Template Library | Microsoft Docs"
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
  - "template libraries"
ms.assetid: 5e80ec6e-a61c-41ce-b34b-9a6252c46265
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Using a Template Library
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una plantilla es similar a una macro.  Como con una macro, invocar una plantilla provoca para expandir \(con la sustitución de parámetros adecuada\) para codificarle ha escrito.  Sin embargo, una plantilla va más lejos que esto a habilitar la creación de nuevas clases basadas en los tipos que se pasa como parámetros.  Estas formas tipo\- seguras de nuevo implementar de las clases de realizar la operación expresada en el código de plantilla.  
  
 Las bibliotecas de plantilla como ATL difieren de las bibliotecas de clases tradicionales de C\+\+ en que se proporcionan únicamente como código fuente \(o como código fuente con un poco, admitiendo runtime\) y no son intrínsecamente o necesariamente jerárquicas de naturaleza.  En lugar de derivarse de una clase para obtener la funcionalidad desea, crea instancias de una clase de una plantilla.  
  
## Vea también  
 [Introducción a ATL](../atl/introduction-to-atl.md)