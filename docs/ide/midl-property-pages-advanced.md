---
title: "Páginas de propiedades MIDL: Avanzadas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d6e7dde047c3311c6fd694a91c7a63fcfbcc95d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="midl-property-pages-advanced"></a>Páginas de propiedades MIDL: Avanzadas
El **avanzadas** página de propiedades de la **MIDL** carpeta especifica las opciones del compilador MIDL siguientes:  
  
-   Habilitar comprobación de errores ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Comprobar asignaciones ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Compruebe los límites ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Comprobar intervalo de enumeración ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Comprobar punteros de referencia ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Comprobar los datos de código auxiliar ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Validar parámetros ([/ robust](http://msdn.microsoft.com/library/windows/desktop/aa367363)) *  
  
-   Alineación de miembros de estructura ([/Zp](http://msdn.microsoft.com/library/windows/desktop/aa367388))  
  
-   Redirigir la salida ([/o](http://msdn.microsoft.com/library/windows/desktop/aa367351))  
  
-   Opciones de preproceso de C ([/cpp_opt](http://msdn.microsoft.com/library/windows/desktop/aa367318))  
  
-   Anular definiciones del preprocesador ([/U](http://msdn.microsoft.com/library/windows/desktop/aa367373))  
  
 \*/ es sólido únicamente para su uso al compilar para una máquina posterior o Windows 2000. Si compila un proyecto ATL y desea utilizar / robust, cambie esta línea en el archivo dlldatax.c:  
  
```  
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM  
to   
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM  
```  
  
 Para obtener información sobre cómo obtener acceso a la **avanzadas** página de propiedades de la **MIDL** carpeta, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
 Para obtener información sobre cómo obtener acceso mediante programación a las opciones de MIDL para los proyectos de C++, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>.  
  
## <a name="see-also"></a>Vea también  
 [Páginas de propiedades MIDL](../ide/midl-property-pages.md)