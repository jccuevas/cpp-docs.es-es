---
title: "Error de MSBuild MSB3256 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB3256"
ms.assetid: 809ccd0a-78cd-4bf5-83a8-2fb51815ea27
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3256
**MSB3256: No se leyeron ensamblados de las listas redist.  No se pudo generar una lista de exclusión del subconjunto de TargetFramework.**  
  
 No se pudo encontrar una lista de elementos redistribuibles \(lista redist\).  
  
 Para generar una lista de los ensamblados que se van a excluir del subconjunto .NET Framework, se necesitan dos archivos: una "lista redist" denominada FrameworkList.xml, que contiene los nombres de los elementos redistribuibles de .NET Framework, y una "lista subset" denominada client.xml, que contiene los nombres de los elementos de .NET Framework.  Dado que la definición del subconjunto necesita las dos listas, si falta la lista redist, no se podrá usar como destino el subconjunto .NET Framework.  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] es un subconjunto de la biblioteca completa en tiempo de ejecución de [!INCLUDE[net_v35_short](../misc/includes/net_v35_short_md.md)].  Para obtener más información acerca de [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], vea [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
### Para corregir este error  
  
-   Proporcione una lista redist válida denominada FrameworkList.xml o utilice como destino la biblioteca redistribuible completa de [!INCLUDE[net_v35_short](../misc/includes/net_v35_short_md.md)].  Para obtener más información acerca de cómo se especifica como destino la versión completa de [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)], vea [Cómo: Usar como destino una versión de .NET Framework](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md).  
  
## Vea también  
 [Versión de .NET Framework de destino y plataforma de destino](../Topic/MSBuild%20Target%20Framework%20and%20Target%20Platform.md)   
 [Elemento Project \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [Recursos adicionales](../Topic/Additional%20MSBuild%20Resources.md)