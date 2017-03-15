---
title: "Almacenamiento de direcciones | Microsoft Docs"
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
  - "direcciones [C++], almacenamiento de"
  - "almacenamiento [C++], direcciones"
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Almacenamiento de direcciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La cantidad de almacenamiento necesaria para una dirección y el significado de la dirección dependen de la implementación del compilador.  No existen garantías de que los punteros a tipos diferentes tengan la misma longitud.  Por consiguiente, **sizeof\(char \*\)** no es necesariamente igual a **sizeof\(int \*\)**.  
  
 **Específicos de Microsoft**  
  
 Para el compilador de C de Microsoft, **sizeof\(char \*\)** es igual a **sizeof\(int \*\)**.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Declaraciones de puntero](../c-language/pointer-declarations.md)