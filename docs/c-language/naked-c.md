---
title: "Naked (C) | Microsoft Docs"
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
  - "código de epílogo"
  - "naked (palabra clave) [C]"
  - "naked (palabra clave) [C], atributo de clase de almacenamiento"
  - "código de prólogo"
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Naked (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 El atributo de clase de almacenamiento naked es una extensión específica de Microsoft para el lenguaje C.  El compilador genera código sin código de prólogo y epílogo para las funciones declaradas con el atributo de clase de almacenamiento naked.  Las funciones naked son útiles cuando se necesita escribir secuencias de código de prólogo\/epílogo propias mediante código ensamblador alineado.  Las funciones naked son útiles para escribir controladores de dispositivos virtuales.  
  
 Para obtener información concreta sobre cómo se usa el atributo naked, vea [Funciones naked](../c-language/naked-functions.md).  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Atributos extendidos de clase de almacenamiento de C](../c-language/c-extended-storage-class-attributes.md)