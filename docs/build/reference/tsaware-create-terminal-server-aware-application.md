---
title: "/TSAWARE (Crear una aplicaci&#243;n que reconozca Terminal Server) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/tsaware"
  - "VC.Project.VCLinkerTool.TerminalServerAware"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/TSAWARE (opción del vinculador)"
  - "Terminal Server"
  - "Terminal Server, aplicaciones que reconozcan Terminal Server"
  - "TSAWARE (opción del vinculador)"
  - "-TSAWARE (opción del vinculador)"
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /TSAWARE (Crear una aplicaci&#243;n que reconozca Terminal Server)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/TSAWARE[:NO]  
```  
  
## Comentarios  
 La opción \/TSAWARE establece una marca en el campo DllCharacteristics de IMAGE\_OPTIONAL\_HEADER, en el encabezado opcional de la imagen del programa.  Si se establece esta marca, Terminal Server no realizará determinados cambios en la aplicación.  
  
 Si una aplicación no está preparada para Terminal Server \(aplicación heredada\), Terminal Server llevará a cabo ciertas modificaciones en ella para que pueda funcionar correctamente en un entorno multiusuario.  Por ejemplo, Terminal Server crea una carpeta Windows virtual para que cada usuario, en lugar de recibir el directorio Windows del sistema, reciba una carpeta Windows.  Esto ofrece a los usuarios acceso a sus propios archivos INI.  Asimismo, Terminal Server realiza algunos ajustes en el Registro de la aplicación heredada.  Con ellos, se ralentiza la carga de la aplicación heredada en Terminal Server.  
  
 Una aplicación preparada para Terminal Server no depende de los archivos INI ni escribe en la clave **HKEY\_CURRENT\_USER** del Registro durante la instalación.  
  
 Si se usa \/TSAWARE y la aplicación todavía utiliza archivos INI, éstos serán compartidos por todos los usuarios del sistema.  Si esto es aceptable, aún se podrá vincular la aplicación con \/TSAWARE; de lo contrario, será necesario usar \/TSAWARE:NO.  
  
 La opción \/TSAWARE está habilitada de forma predeterminada para Windows 2000 y posteriores, así como para las aplicaciones Windows y de consola.  Para obtener más información, vea [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) y [\/VERSION](../../build/reference/version-version-information.md).  
  
 \/TSAWARE no es válida para controladores, VxD o DLL.  
  
 Si se vincula una aplicación por medio de \/TSAWARE, DUMPBIN [\/HEADERS](../../build/reference/headers.md) mostrará la información pertinente.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Sistema**.  
  
4.  Modifique la propiedad **Terminal Server**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [Storing User\-Specific Information](http://msdn.microsoft.com/library/aa383452)   
 [Legacy Applications in a Terminal Services Environment](https://msdn.microsoft.com/en-us/library/aa382957.aspx)