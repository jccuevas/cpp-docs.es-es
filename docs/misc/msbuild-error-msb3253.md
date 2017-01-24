---
title: "Error de MSBuild MSB3253 | Microsoft Docs"
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
  - "MSB3253"
ms.assetid: d4b5eb5b-703b-4b80-aa5d-6c70ff9fe84d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3253
**MSB3253: El ensamblado \<nombre\> al que se hace referencia en el proyecto depende de \<nombre2\>, que no está incluido en .NET Framework Client Profile.**  
  
 Uno de los ensamblados, o de los ensamblados dependientes, al que se hace referencia en el proyecto depende de otro ensamblado que no está incluido en [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)].  
  
 Este mensaje normalmente aparece cuando un proyecto hace referencia a un control o DLL de terceros que, a su vez, hace referencia a un ensamblado externo.  Por ejemplo, un proyecto utiliza un control que, a su vez, utiliza una funcionalidad incluida en la versión completa de [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)].  Si el destino de la aplicación se cambia a [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] y la aplicación se instala en un sistema que no tiene [!INCLUDE[net_v35_long](../misc/includes/net_v35_long_md.md)], es posible que la aplicación no funcione correctamente si intenta obtener acceso a la funcionalidad que no está incluida en el subconjunto de [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)].  
  
 Este mensaje de "error" en realidad es solamente una advertencia; con todo, la aplicación se compilará.  Sin embargo, puede producirse algún error posteriormente si el control o DLL hace referencia a una funcionalidad que se encuentra en un ensamblado ausente.  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] es un subconjunto de la biblioteca completa en tiempo de ejecución de [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 3.5.  Para obtener más información acerca de [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], vea [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
### Para corregir este error  
  
-   Quite la referencia al ensamblado especificado del proyecto o especifique como destino la versión completa de [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] en lugar de la biblioteca del subconjunto [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)].  Para obtener más información acerca de cómo se especifica como destino la versión completa de [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)], vea [Cómo: Usar como destino una versión de .NET Framework](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md).  
  
## Vea también  
 [Versión de .NET Framework de destino y plataforma de destino](../Topic/MSBuild%20Target%20Framework%20and%20Target%20Platform.md)   
 [Elemento Project \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [Recursos adicionales](../Topic/Additional%20MSBuild%20Resources.md)