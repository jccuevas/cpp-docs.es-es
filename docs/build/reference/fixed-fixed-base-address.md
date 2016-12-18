---
title: "/FIXED (Direcci&#243;n base fija) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/fixed"
  - "VC.Project.VCLinkerTool.FixedBaseAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FIXED (opción del vinculador)"
  - "FIXED (opción del vinculador)"
  - "-FIXED (opción del vinculador)"
  - "dirección base preferida para cargar programa"
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FIXED (Direcci&#243;n base fija)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/FIXED[:NO]  
```  
  
## Comentarios  
 Indica al sistema operativo que solo debe cargar el programa en su dirección base preferida.  Si dicha dirección base no está disponible, el sistema operativo no cargará el archivo.  Para obtener más información, vea [\/BASE \(Dirección base\)](../../build/reference/base-base-address.md).  
  
 \/FIXED:NO es el valor predeterminado para un archivo DLL, mientras que \/FIXED se utiliza para proyectos de cualquier otro tipo.  
  
 Si se especifica \/FIXED, LINK no generará una sección de cambio de ubicación en el programa.  En tiempo de ejecución, si el sistema operativo no logra cargar el programa en la dirección especificada, emitirá un mensaje de error y no lo cargará.  
  
 Si se especifica \/FIXED:NO, se generará una sección de cambio de ubicación en el programa.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **Vinculador**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Escriba el nombre y el valor de la opción en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)