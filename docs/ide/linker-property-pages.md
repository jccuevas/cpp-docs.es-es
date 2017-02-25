---
title: "P&#225;ginas de propiedades Vinculador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.RegisterOutput"
  - "VC.Project.VCLinkerTool.IgnoreImportLibrary"
  - "VC.Project.VCLinkerTool.UseLibraryDependencyInputs"
  - "VC.Project.VCLinkerTool.LinkLibraryDependencies"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "redirección por usuario"
  - "páginas de propiedades Vinculador"
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# P&#225;ginas de propiedades Vinculador
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se describen las siguientes propiedades de la página de propiedades **General** del vinculador:  
  
 **Omitir biblioteca de importación**  
 Indica al vinculador que no intente vincular ningún archivo .lib generado en esta compilación a ningún proyecto dependiente.  Esto permite al sistema de proyectos controlar los archivos .dll que no producen un archivo .lib cuando se compilan.  Si un proyecto depende de otro proyecto que genera un archivo DLL, el sistema de proyectos vinculará automáticamente el archivo .lib generado por ese proyecto secundario.  Esto puede no ser necesario en el caso de proyectos que generan archivos DLL COM o archivos DLL solo de recursos; estos archivos DLL no tienen exportaciones significativas.  Si un archivo DLL no tiene exportaciones, el vinculador no generará un archivo .lib.  Si no hay ningún archivo de exportación .lib en el disco y el sistema de proyectos indica al vinculador que debe establecer un vínculo con este archivo DLL \(que falta\), se producirá un error en el vinculador.  
  
 Utilice **Omitir biblioteca de importación** para resolver este problema.  Cuando se establece en `Yes`, el sistema de proyectos pasará por alto la presencia o ausencia de ese archivo .lib y evitará que cualquier proyecto que dependa de este proyecto se vincule al archivo .lib inexistente.  
  
 Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.  
  
 **Registrar resultados**  
 Ejecuta regsvr32.exe \/s $\(TargetPath\), que solo es válido para proyectos de archivo .dll.  En los proyectos de archivo .exe se omite esta propiedad.  Si desea registrar un resultado de tipo .exe, establezca un evento posterior a la compilación en la configuración para que realice el registro personalizado que siempre se necesita para los archivos .exe registrados.  
  
 Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.  
  
 **Redirección por usuario**  
 El registro en [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] se ha realizado tradicionalmente en HKEY\_CLASSES\_ROOT \(HKCR\).  Con [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)], para obtener acceso a HKCR se debe ejecutar [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] en modo elevado.  Los desarrolladores no siempre desean trabajar en modo elevado, pero aun así deben trabajar con el registro.  La redirección por usuario le permite registrar sin tener que trabajar en este modo.  
  
 La redirección por usuario forzará la redirección a HKEY\_CURRENT\_USER \(HKCU\) de todas las escrituras en HKCR.  Si la redirección por usuario está desactivada, puede producir [Error PRJ0050 al compilar el proyecto](../error-messages/tool-errors/project-build-error-prj0050.md) cuando el programa intenta escribir en HKCR.  
  
 **Vincular dependencias de biblioteca**  
 Ofrece la posibilidad de vincular en los archivos .lib generados por proyectos dependientes.  Normalmente, se debe vincular en el archivo .lib.  
  
 También puede especificar un archivo .obj proporcionando el nombre de archivo y la ruta de acceso relativa, por ejemplo **..\\..\\MyLibProject\\MyObjFile.obj**.  Si el código fuente del archivo .obj incluye un encabezado precompilado, por ejemplo pch.h, el archivo pch.obj se encuentra en la misma carpeta que **MyObjFile.obj** y debe agregar también **pch.obj** como una dependencia adicional.  
  
 **Usar entradas de dependencia de biblioteca**  
 En un proyecto grande, cuando un proyecto dependiente genera un archivo .lib, se deshabilita la vinculación incremental.  Si hay muchos proyectos dependientes que generan archivos .lib, puede llevar bastante tiempo compilar la aplicación.  Cuando esta propiedad está establecida en `Yes`, el sistema de proyectos vincula en los archivos .obj para los archivos .lib generados por proyectos dependientes, con lo que se habilita la vinculación incremental.  
  
 Para obtener información sobre cómo tener acceso a la página de propiedades **General** del vinculador, vea [Cómo: Especificar las propiedades de un proyecto con las páginas de propiedades](../misc/how-to-specify-project-properties-with-property-pages.md).  
  
## Vea también  
 [VC\+\+ Directories, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/es-es/e027448b-c811-4c3d-8531-4325ad3f6e02)   
 [Páginas de propiedades](../ide/property-pages-visual-cpp.md)