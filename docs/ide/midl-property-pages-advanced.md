---
title: 'Páginas de propiedades MIDL: Avanzadas | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ValidateParameters
dev_langs:
- C++
helpviewer_keywords:
- MIDL, property pages
ms.assetid: d1c92e01-f403-4ed6-ab45-4043a3c9c6bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5f87518c23848cea91a3e3c48361aa0a63fa88a2
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33330809"
---
# <a name="midl-property-pages-advanced"></a>Páginas de propiedades MIDL: Avanzadas
En la página de propiedades **Avanzadas** de la carpeta **MIDL** se especifican las opciones del compilador MIDL siguientes:  
  
-   Habilitar comprobación de errores ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Comprobar asignaciones ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Comprobar límites ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Comprobar intervalo de enumeración ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Comprobar punteros de referencia ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Comprobar código auxiliar de los datos ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Validar parámetros ([/robust](http://msdn.microsoft.com/library/windows/desktop/aa367363)) *  
  
-   Alineación de miembros de struct ([/Zp](http://msdn.microsoft.com/library/windows/desktop/aa367388))  
  
-   Redirigir resultados ([/o](http://msdn.microsoft.com/library/windows/desktop/aa367351))  
  
-   Opciones de preproceso de C ([/cpp_opt](http://msdn.microsoft.com/library/windows/desktop/aa367318))  
  
-   Anular definiciones del preprocesador ([/U](http://msdn.microsoft.com/library/windows/desktop/aa367373))  
  
 \* /robust solo se usa al compilar para un equipo Windows 2000 o posterior. Si compila un proyecto ATL y quiere usar /robust, cambie esta línea en el archivo dlldatax.c:  
  
```  
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM  
to   
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM  
```  
  
 Para obtener información sobre cómo acceder a la página de propiedades **Avanzadas** de la carpeta **MIDL**, vea [Trabajar con propiedades de proyecto](../ide/working-with-project-properties.md).  
  
 Para obtener información sobre cómo acceder mediante programación a las opciones de MIDL para los proyectos de C++, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>.  
  
## <a name="see-also"></a>Vea también  
 [Páginas de propiedades MIDL](../ide/midl-property-pages.md)