---
title: "Redistribuir componentes mediante m&#243;dulos de combinaci&#243;n | Microsoft Docs"
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
  - "módulos de combinación, utilizar"
  - "redistribuir aplicaciones, mediante módulos de combinación"
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# Redistribuir componentes mediante m&#243;dulos de combinaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] incluye [módulos de combinación](http://msdn.microsoft.com/library/aa367434) para cada componente de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] que se puede redistribuir con una aplicación.  Cuando un módulo de combinación se compila en un archivo de instalación de Windows Installer, habilita la implementación de determinados archivos DLL en los equipos que tienen una plataforma específica.  En el archivo de instalación, especifique que los módulos de combinación son requisitos previos para la aplicación.  Cuando se instala [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], los módulos de combinación se instalan en la carpeta \\Archivos de programa\\Common Files\\Merge Modules\\. \(Solo se pueden redistribuir las versiones que no son de depuración de los archivos DLL de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)]\). Para obtener más información y un vínculo a una lista de los módulos de combinación que se pueden redistribuir, vea [Redistribuir archivos de Visual C\+\+](../ide/redistributing-visual-cpp-files.md).  
  
 Puede usar módulos de combinación para habilitar la instalación de los archivos DLL redistribuibles de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] en la carpeta %SYSTEMROOT%\\system32\\. \(El propio [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] emplea esta técnica\). Sin embargo, la instalación en esta carpeta producirá un error a menos que el usuario que realiza la instalación tenga derechos de administrador.  
  
 Se recomienda no usar módulos de combinación excepto cuando no tenga que mantener la aplicación y no tenga dependencias en más de una versión de los archivos DLL.  Los módulos de combinación para versiones diferentes del mismo archivo DLL no se pueden incluir en un instalador y los módulos de combinación hacen que sea difícil mantener los archivos DLL independientemente de la aplicación.  En su lugar, se recomienda instalar un paquete redistribuible de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)].  
  
## Vea también  
 [Redistribuir archivos de Visual C\+\+](../ide/redistributing-visual-cpp-files.md)