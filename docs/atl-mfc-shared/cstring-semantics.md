---
title: "CString Semantics | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "instrucciones de asignación, assigning CString objects"
  - "CString objects, assignment semantics"
  - "semantics in Cstring"
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# CString Semantics
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Aunque los objetos de [CString](../atl-mfc-shared/reference/cstringt-class.md) son objetos dinámicos que pueden crecer, actúan como tipos primitivos integrados y clases simples.  cada objeto de `CString` representa un valor único.  los objetos de`CString` deben considerarse como cadenas reales en lugar de como punteros a cadenas.  
  
 Puede asignar un objeto de **CString** a otro.  Sin embargo, al modificar uno de los dos objetos de `CString` , el otro objeto de `CString` no se ha modificado, como se muestra en el ejemplo siguiente:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/CPP/cstring-semantics_1.cpp)]  
  
 Nota en el ejemplo que los dos objetos de `CString` se consideran “equals” porque representan la misma cadena de caracteres.  La clase de `CString` sobrecarga el operador de igualdad \(`==`\) para comparar dos objetos de `CString` basándose en su valor \(contenido\) en lugar de su identidad \(dirección\).  
  
## Vea también  
 [Cadenas](../atl-mfc-shared/strings-atl-mfc.md)