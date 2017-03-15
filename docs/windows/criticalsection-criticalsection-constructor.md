---
title: "CriticalSection::CriticalSection (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CriticalSection, constructor"
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# CriticalSection::CriticalSection (Constructor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inicializa un objeto de sincronización que es similar a un objeto mutex, pero se puede utilizar por sólo los subprocesos de un proceso único.  
  
## Sintaxis  
  
```  
explicit CriticalSection(  
   ULONG spincount = 0  
);  
```  
  
#### Parámetros  
 `spincount`  
 El recuento de número para el objeto de sección crítica.  El valor predeterminado es 0.  
  
## Comentarios  
 Para obtener más información sobre las secciones y spincounts crticial, vea la función de **InitializeCriticalSectionAndSpinCount** en la sección de sincronización de documenation de API de Windows.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [CriticalSection \(Clase\)](../Topic/CriticalSection%20Class.md)