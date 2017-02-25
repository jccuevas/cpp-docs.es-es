---
title: "Administraci&#243;n de memoria: Asignaci&#243;n del mont&#243;n | Microsoft Docs"
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
  - "delete (operador), usar con depuración MFC"
  - "detectar pérdidas de memoria"
  - "asignación en el montón"
  - "asignación en el montón, descripción"
  - "asignación de memoria, memoria de montón"
  - "pérdidas de memoria, detectar"
  - "memoria, detectar pérdidas"
  - "new (operador), usar con depuración MFC"
ms.assetid: a5d949c6-1b79-476e-9c66-513a558203d9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Administraci&#243;n de memoria: Asignaci&#243;n del mont&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La pila se reserva para la asignación de memoria necesita del programa.  Es un área independientemente del código de programa y la pila.  Los programas de c típicos utilizan funciones `malloc` y **free** para asignar y para la desasignación de memoria del montón.  La versión de depuración de MFC proporciona versiones modificadas de los operadores integrados **new** y **borrar** de C\+\+ para asignar y desasignar para objetos en memoria de la pila.  
  
 Cuando se utiliza **new** y **borrar** en lugar de `malloc` y de **free**, puede aprovechar las mejoras de depuración de administración de memoria de la biblioteca de clases, que pueden ser útiles para detectar pérdidas de memoria.  Al compilar el programa con la versión de lanzamiento de MFC, las versiones estándar de los operadores de **new** y de **borrar** proporcionan una manera eficaz de asignar y desasignar de memoria \(la versión de lanzamiento de MFC no proporciona versiones modificadas de estos operadores\).  
  
 Observe que el tamaño total de los objetos asignados en el montón está limitado por la memoria virtual disponible en el sistema.  
  
## Vea también  
 [Administración de memoria](../mfc/memory-management.md)