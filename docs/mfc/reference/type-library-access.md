---
title: "Acceso a la biblioteca de tipos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bibliotecas de tipos, obtener acceso"
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
caps.latest.revision: 14
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Acceso a la biblioteca de tipos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las bibliotecas de tipos exponen las interfaces de un control OLE a otras aplicaciones OLE\- con conocimiento pleno.  Cada control OLE debe tener una biblioteca de tipos si fuese una o más interfaces a exponerse.  
  
 Las siguientes macros permiten que un control OLE proporciona acceso a una biblioteca de tipos:  
  
### Biblioteca de tipos Access  
  
|||  
|-|-|  
|[DECLARE\_OLETYPELIB](../Topic/DECLARE_OLETYPELIB.md)|Declara una función miembro de `GetTypeLib` de un control OLE \(se utiliza en la declaración de clase\).|  
|[IMPLEMENT\_OLETYPELIB](../Topic/IMPLEMENT_OLETYPELIB.md)|Implementa una función miembro de `GetTypeLib` de un control OLE \(se utiliza en la implementación de la clase\).|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)