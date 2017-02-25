---
title: "Aislamiento de la biblioteca de controles comunes de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC, biblioteca de controles comunes"
ms.assetid: 7471e6f0-49b0-47f7-86e7-8d6bc3541694
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Aislamiento de la biblioteca de controles comunes de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La biblioteca de Controles comunes ahora se aísla dentro de MFC, lo que módulos diferentes \(como archivos DLL de usuario\) utilizan versiones diferentes de Controles comunes que la biblioteca especificando la versión en los manifiestos.  
  
 Una aplicación MFC \(o el código de usuario denominado por MFC\) llama a la biblioteca API de Controles comunes con funciones de contenedor con nombre `Afx`*FunctionName*, donde es el nombre *FunctionName* de Controles comunes API.  Las invocaciones de funciones se definen en afxcomctl32.h y afxcomctl32.inl.  
  
 Puede utilizar macros de [AFX\_COMCTL32\_IF\_EXISTS](../Topic/AFX_COMCTL32_IF_EXISTS.md) y de [AFX\_COMCTL32\_IF\_EXISTS2](../Topic/AFX_COMCTL32_IF_EXISTS2.md) \(definidas en afxcomctl32.h\) para determinar si la biblioteca de Controles comunes implementa algunas API en lugar de llamar a [GetProcAddress](../build/getprocaddress.md).  
  
 Técnicamente, se llama a la biblioteca API a través de una clase contenedora, `CComCtlWrapper` de Controles comunes \(definido en afxcomctl32.h\).  `CComCtlWrapper` también es responsable de cargar y descargar de comctl32.dll.  El estado del módulo MFC contiene un puntero a una instancia de `CComCtlWrapper`.  Puede tener acceso a la clase contenedora mediante la macro de `afxComCtlWrapper` .  
  
 Observe que llamando a Controles comunes API directamente \(sin utilizar funciones de contenedor MFC\) de una aplicación o un usuario MFC funcionará DLL en la mayoría de los casos, dado que vinculan la aplicación o usuario DLL de MFC a la biblioteca de Controles comunes solicitado en su manifiesto\).  Sin embargo, el código MFC tiene que utilizar contenedores, porque el código MFC se podría llamar de las DLL de usuario con distintas versiones de la biblioteca de Controles comunes.