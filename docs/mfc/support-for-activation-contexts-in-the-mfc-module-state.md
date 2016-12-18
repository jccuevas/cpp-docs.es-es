---
title: "Compatibilidad con los contextos de activaci&#243;n en el estado del m&#243;dulo MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contextos de activación [C++]"
  - "contextos de activación [C++], compatibilidad con MFC"
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Compatibilidad con los contextos de activaci&#243;n en el estado del m&#243;dulo MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC crea un contexto de activación mediante un recurso manifiesto proporcionado por el módulo del usuario.  Para obtener más información sobre cómo se crean los contextos de activación, vea los temas siguientes:  
  
-   [Activation Contexts](http://msdn.microsoft.com/library/aa374153)  
  
-   [Application Manifests](http://msdn.microsoft.com/library/aa374191)  
  
-   [Assembly Manifests](http://msdn.microsoft.com/library/aa374219)  
  
## Comentarios  
 Al leer estos temas de [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] , observe que el mecanismo de contexto de activación de MFC se parece al contexto de activación de [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] salvo que MFC no utiliza el contexto API de [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] Activación.  
  
 El contexto de activación funciona en aplicaciones MFC, archivos DLL de usuario, y archivos DLL de extensión de las maneras siguientes:  
  
-   Las aplicaciones MFC utilizan el Id. de recurso 1 para el recurso del manifiesto.  En este caso, MFC no crea su propio contexto de activación, pero utiliza el contexto de la aplicación.  
  
-   Los archivos DLL de MFC utilizan el Id. de recurso 2 para el recurso del manifiesto.  Aquí, MFC crea un contexto de activación para cada usuario DLL, de modo que varios archivos DLL de usuario pueden utilizar versiones diferentes de las mismas bibliotecas \(por ejemplo, la biblioteca de Controles comunes\).  
  
-   Los archivos DLL de extensión MFC se basan en las aplicaciones o archivos DLL de usuario que hospedan para establecer el contexto de activación.  
  
 Aunque el estado del contexto de activación pueda modificar utilizando los procesos descritos en [Using the Activation Context API](http://msdn.microsoft.com/library/aa376620), mediante el mecanismo de contexto de activación de MFC puede ser útil al desarrollar las arquitecturas de complemento DLL\- basadas donde no es fácil \(o imposible\) cambiar manualmente el estado de activación antes y después de las llamadas individuales a los complementos externos.  
  
 El contexto de activación se crea en [AfxWinInit](../Topic/AfxWinInit.md).  Se destruye en `AFX_MODULE_STATE` destructor.  Un identificador de contexto de activación se mantiene `AFX_MODULE_STATE`. \(`AFX_MODULE_STATE` se describe en [AfxGetStaticModuleState](../Topic/AfxGetStaticModuleState.md).\)  
  
 La macro de [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md) activa y desactiva el contexto de activación.  `AFX_MANAGE_STATE` está habilitada para las bibliotecas MFC estáticas, así como los archivos DLL de MFC, permitir que el código MFC se ejecuta en el contexto adecuado de activación seleccionado por el usuario.  
  
## Vea también  
 [Activation Contexts](http://msdn.microsoft.com/library/aa374153)   
 [Application Manifests](http://msdn.microsoft.com/library/aa374191)   
 [Assembly Manifests](http://msdn.microsoft.com/library/aa374219)   
 [AfxWinInit](../Topic/AfxWinInit.md)   
 [AfxGetStaticModuleState](../Topic/AfxGetStaticModuleState.md)   
 [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md)