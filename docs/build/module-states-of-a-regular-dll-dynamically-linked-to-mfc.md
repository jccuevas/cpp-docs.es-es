---
title: "Estados de m&#243;dulos de un archivo DLL est&#225;ndar vinculado din&#225;micamente a MFC | Microsoft Docs"
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
helpviewer_keywords: 
  - "DLL [C++], estados de módulos"
  - "DLL de MFC [C++], archivos DLL estándar"
  - "estados de módulos [C++]"
  - "estados de módulos [C++], archivos DLL estándar vinculados dinámicamente"
  - "DLL estándar [C++], vinculados dinámicamente a MFC"
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Estados de m&#243;dulos de un archivo DLL est&#225;ndar vinculado din&#225;micamente a MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La capacidad de vincular dinámicamente un archivo DLL estándar al archivo DLL de MFC permite realizar algunas configuraciones muy complicadas.  Por ejemplo, un archivo DLL estándar y el archivo ejecutable que lo utiliza pueden vincularse dinámicamente al archivo DLL de MFC y a cualquier archivo DLL de extensión.  
  
 Esta configuración plantea un problema con respecto a los datos globales de MFC, como el puntero al objeto `CWinApp` actual y asignaciones de identificadores.  
  
 Antes de la versión 4.0 de MFC, estos datos globales residían en el archivo DLL de MFC y los compartían todos los módulos del proceso.  Dado que cada proceso que utiliza un archivo Win32.DLL obtiene su propia copia de los datos del archivo DLL, este esquema proporcionaba una forma sencilla de efectuar el seguimiento de los datos por proceso.  Además, puesto que el modelo AFXDLL presuponía que sólo habría un objeto `CWinApp` y sólo un conjunto de asignaciones de identificadores en el proceso, se podía efectuar el seguimiento de estos elementos en el propio archivo DLL de MFC.  
  
 Pero con la capacidad de vincular dinámicamente un archivo DLL estándar al archivo DLL de MFC, ahora es posible tener dos o más objetos `CWinApp` en un proceso \(y también dos o más conjuntos de asignaciones de identificadores\).  ¿Cómo hace MFC un seguimiento de los que tiene que utilizar?  
  
 La solución es proporcionar a cada módulo \(aplicación o DLL estándar\) su propia copia de esta información de estado global.  Por tanto, una llamada a **AfxGetApp**  en el archivo DLL estándar devuelve un puntero al objeto `CWinApp` del archivo DLL, no al del ejecutable.  Esta copia por módulo de los datos globales de MFC se conoce como un estado del módulo y se describe en la [Nota técnica 58 de MFC](../mfc/tn058-mfc-module-state-implementation.md).  
  
 El procedimiento de ventana común de MFC cambia automáticamente al estado de módulo correcto, por lo que no tiene que ocuparse de ello en ningún controlador de mensajes implementado en el archivo DLL estándar.  Pero cuando el archivo ejecutable realice una llamada al archivo DLL estándar, tendrá que establecer explícitamente el estado de módulo actual para el del archivo DLL.  Para ello, utilice la macro **AFX\_MANAGE\_STATE**  en cada función exportada desde el archivo DLL.  Para ello, debe agregar la siguiente línea de código al principio de las funciones exportadas desde el archivo DLL:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Administrar los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [Archivos DLL estándar vinculados dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Archivos DLL de extensión](../build/extension-dlls-overview.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)