---
title: "TN047: Reducir los requisitos de las transacciones de base de datos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TN047"
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# TN047: Reducir los requisitos de las transacciones de base de datos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta nota de la tecnología, que tratados los requisitos de la transacción de las clases de base de datos ODBC de MFC, está obsoleto.  Antes de MFC 4,2, las clases de base de datos requieren que los cursores se conservarán en los conjuntos de registros después de una operación de **CommitTrans** o de **Reversión** .  Si el controlador ODBC y DBMS no admitía este nivel de conservación de cursor, las clases de base de datos no esté habilitado transacciones.  
  
 Empezando por MFC 4,2, las clases de base de datos han reducido la restricción para exigir la conservación del cursor.  Las transacciones se habilitadas si el controlador las admite.  Sin embargo, ahora debe comprobar el efecto de una operación de **CommitTrans** o de **Reversión** en conjuntos de registros abiertos.  Vea funciones [CDatabase::GetCursorCommitBehavior](../Topic/CDatabase::GetCursorCommitBehavior.md) y [CDatabase::GetCursorRollbackBehavior](../Topic/CDatabase::GetCursorRollbackBehavior.md) miembro para obtener más información.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)