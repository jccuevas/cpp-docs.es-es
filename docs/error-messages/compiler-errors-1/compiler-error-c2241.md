---
title: "Error del compilador C2241 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2241"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2241"
ms.assetid: 2f4e2c2c-b95c-4afe-bbe0-4214cd39d140
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C2241
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador': el acceso a miembros está restringido  
  
 El código intenta acceder a un miembro privado o protegido.  
  
### Para corregir mediante las siguientes posibles soluciones  
  
1.  Cambie el nivel de acceso del miembro.  
  
2.  Declare el miembro como `friend` de la función de acceso.