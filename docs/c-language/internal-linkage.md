---
title: "Vinculaci&#243;n interna | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "vinculación interna"
  - "vinculación [C++], internal"
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vinculaci&#243;n interna
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si la declaración de un identificador de ámbito de archivo para un objeto o una función contiene el *storage\-class\-specifier* **static**, el identificador tiene vinculación interna.  De lo contrario, el identificador tiene vinculación externa.  Vea [Clases de almacenamiento](../c-language/c-storage-classes.md) si desea una descripción del elemento no terminal *storage\-class\-specifier*.  
  
 Dentro de una unidad de traducción, cada instancia de un identificador con vinculación interna denota el mismo identificador o función.  Los identificadores vinculados internamente son exclusivos para una unidad de traducción.  
  
## Vea también  
 [Usar extern para especificar la vinculación](../cpp/using-extern-to-specify-linkage.md)