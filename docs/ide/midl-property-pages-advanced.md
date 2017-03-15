---
title: "P&#225;ginas de propiedades MIDL: Avanzadas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCMidlTool.ErrorCheckBounds"
  - "VC.Project.VCMidlTool.ErrorCheckStubData"
  - "VC.Project.VCMidlTool.ErrorCheckAllocations"
  - "VC.Project.VCMidlTool.CPreprocessOptions"
  - "VC.Project.VCMidlTool.UndefinePreprocessorDefinitions"
  - "VC.Project.VCMidlTool.EnableErrorChecks"
  - "VC.Project.VCMidlTool.RedirectOutputAndErrors"
  - "VC.Project.VCMidlTool.ErrorCheckEnumRange"
  - "VC.Project.VCMidlTool.StructMemberAlignment"
  - "VC.Project.VCMidlTool.ErrorCheckRefPointers"
  - "VC.Project.VCMidlTool.ValidateParameters"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MIDL, páginas de propiedades"
ms.assetid: d1c92e01-f403-4ed6-ab45-4043a3c9c6bb
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# P&#225;ginas de propiedades MIDL: Avanzadas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La página de propiedades **Avanzadas** de la carpeta **MIDL** especifica las siguientes opciones del compilador de MIDL:  
  
-   Habilitar la comprobación de errores \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   Comprobar asignaciones \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   Comprobar enlaces \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   Comprobar intervalo de enumeración \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   Comprobar punteros de referencia \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   Comprobar ruta interna de los datos \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   Validar parámetros \([\/robust](http://msdn.microsoft.com/library/windows/desktop/aa367363)\) \*  
  
-   Alineación de miembros de struct \([\/Zp](http://msdn.microsoft.com/library/windows/desktop/aa367388)\)  
  
-   Redirigir resultados \([\/o](http://msdn.microsoft.com/library/windows/desktop/aa367351)\)  
  
-   Opciones de preproceso de C \([\/cpp\_opt](http://msdn.microsoft.com/library/windows/desktop/aa367318)\)  
  
-   Anular definiciones del preprocesador \([\/U](http://msdn.microsoft.com/library/windows/desktop/aa367373)\)  
  
 \* \/robust solo se utiliza en la compilación para equipos con Windows 2000 o posterior.  Si compila un proyecto ATL y desea utilizar \/robust, cambie esta línea en el archivo dlldatax.c:  
  
```  
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM  
to   
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM  
```  
  
 Para obtener información sobre cómo tener acceso a la página de propiedades **Avanzadas** de la carpeta **MIDL**, vea [Cómo: Especificar las propiedades de un proyecto con las páginas de propiedades](../misc/how-to-specify-project-properties-with-property-pages.md).  
  
 Para obtener información sobre cómo obtener acceso mediante programación a las opciones de MIDL para los proyectos de C\+\+, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>.  
  
## Vea también  
 [Páginas de propiedades MIDL](../ide/midl-property-pages.md)