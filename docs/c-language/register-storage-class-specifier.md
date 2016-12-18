---
title: "register (Especificador de clase de almacenamiento) | Microsoft Docs"
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
  - "register (clase de almacenamiento)"
  - "variables de registro"
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# register (Especificador de clase de almacenamiento)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 El compilador de Microsoft C\/C\+\+ no admite solicitudes de usuario para variables de registro.  Sin embargo, a efectos de portabilidad, el compilador acepta toda la demás semántica asociada a la palabra clave **register**.  Por ejemplo, no puede aplicar el operador unario de dirección \(**&**\) a un objeto del registro ni puede usar la palabra clave **register** en matrices.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Especificadores de clase de almacenamiento para las declaraciones de nivel interno](../c-language/storage-class-specifiers-for-internal-level-declarations.md)