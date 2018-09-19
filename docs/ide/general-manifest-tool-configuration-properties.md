---
title: Propiedades de configuración de la herramienta Manifiesto (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.MergeRulesFile
- VC.Project.VCManifestTool.UseUnicodeResponseFiles
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.UseFAT32Workaround
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
dev_langs:
- C++
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 149facb5ed934b68d3407f9acc17238482021f06
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716321"
---
# <a name="general-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>General, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de &lt;NombreDeProyecto&gt; (Cuadro de diálogo)
Use este cuadro de diálogo para especificar las opciones generales de [Mt.exe](https://msdn.microsoft.com/library/aa375649).  
  
 Para acceder a este cuadro de diálogo de página de propiedades, abra las páginas de propiedades para el proyecto o la hoja de propiedades. Expanda el nodo **Herramienta Manifiesto** bajo **Propiedades de configuración** y, después, seleccione **General**.  
  
## <a name="uielement-list"></a>Lista de UIElement  
- **Suprimir la pancarta de inicio**

   **Sí (/nologo)** especifica que los datos de copyright de Microsoft estándar se ocultan cuando se inicia la herramienta Manifiesto. Use esta opción para suprimir la salida no deseada en los archivos de registro, cuando ejecute mt.exe como parte de un proceso de compilación o desde un entorno de compilación.  
  
- **Resultado detallado**

   **Sí (/verbose)** especifica que se mostrará información adicional de compilación durante la generación del manifiesto.  
  
- **Identidad del ensamblado**

   Usa la opción /identity para especificar una cadena de identidad, que incluye los atributos para el [Elemento \<assemblyIdentity>](/visualstudio/deployment/assemblyidentity-element-clickonce-application). Una cadena de identidad comienza con el valor para el atributo `name`, seguido por pares *atributo* = *valor*. Los atributos de una cadena de identidad se delimitan mediante una coma.  
  
   A continuación se muestra una cadena de identidad de ejemplo:  
  
   `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Páginas de propiedades de la herramienta Manifiesto](../ide/manifest-tool-property-pages.md)   
 [Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)   