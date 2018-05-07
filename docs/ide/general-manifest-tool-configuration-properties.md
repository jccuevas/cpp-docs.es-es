---
title: Manifiesto de propiedades de configuración de la herramienta (Visual C++) | Documentos de Microsoft
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
ms.openlocfilehash: 1953e7c37c07f66845510efe037015a537aa7baa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="general-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>General, herramienta manifiesto, propiedades de configuración, &lt;Projectname&gt; cuadro de diálogo páginas de propiedades
Utilice este cuadro de diálogo para especificar las opciones generales de [Mt.exe](http://msdn.microsoft.com/library/aa375649).  
  
 Para obtener acceso a este cuadro de diálogo de la página de propiedades, abra las páginas de propiedades para el proyecto o la hoja de propiedades. Expanda el **herramienta manifiesto** nodo bajo **propiedades de configuración**y, a continuación, seleccione **General**.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Suprimir el titular de inicio**  
 **Sí (/ nologo)** especifica que los datos de copyright de Microsoft estándares se ocultan cuando se inicia la herramienta de manifiesto. Utilice esta opción para suprimir la salida no deseado en los archivos de registro, cuando ejecute mt.exe como parte de un proceso de compilación o de un entorno de compilación.  
  
 **Resultados detallados**  
 **Sí (/verbose)** especifica que se mostrará información adicional de compilación durante la generación del manifiesto.  
  
 **Identidad del ensamblado**  
 Utiliza la opción /identity para especificar una cadena de identidad, que incluye los atributos para el [ \<assemblyIdentity > elemento](/visualstudio/deployment/assemblyidentity-element-clickonce-application). Una cadena de identidad comienza con el valor de la `name` atributo y va seguida por *atributo* = *valor* pares. Los atributos en una cadena de identidad se delimitan mediante una coma.  
  
 El siguiente es un ejemplo de cadena de identidad:  
  
 `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Páginas de propiedades de la herramienta manifiesto](../ide/manifest-tool-property-pages.md)   
 [Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)   