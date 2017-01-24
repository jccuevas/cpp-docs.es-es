---
title: "Ya no se admiten instrucciones &#39;Get&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30829"
  - "bc30829"
helpviewer_keywords: 
  - "BC30829"
ms.assetid: 8d798357-7efb-4423-9808-8b20777b97ba
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ya no se admiten instrucciones &#39;Get&#39;.
Ya no se admiten instrucciones `Get`. La función de E\/S de archivos está disponible en el espacio de nombres `Microsoft.VisualBasic`.  
  
 `Get` no se admite para operaciones de archivo y solo puede usarse en la sintaxis del procedimiento de propiedad.  
  
 **Identificador de error:** BC30829  
  
### Para corregir este error  
  
1.  Realice operaciones de archivo mediante los miembros de las funciones de tiempo de ejecución `System.IO`, `FileSystemObject` y [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)].  
  
## Vea también  
 [Procesar unidades, directorios y archivos](../Topic/Processing%20Drives,%20Directories,%20and%20Files%20\(Visual%20Basic\).md)   
 [Get \(Instrucción\)](../Topic/Get%20Statement.md)   
 [Acceso a archivos con Visual Basic](../Topic/File%20Access%20with%20Visual%20Basic.md)