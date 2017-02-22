---
title: "/OUT (Nombre del archivo de resultados) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.OutputFile"
  - "/out"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/OUT (opción del vinculador de C++)"
  - "vinculador [C++], archivos de salida"
  - "OUT (opción del vinculador)"
  - "-OUT (opción del vinculador)"
  - "archivos de salida, name (opción del vinculador)"
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /OUT (Nombre del archivo de resultados)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/OUT:filename  
```  
  
## Comentarios  
 donde:  
  
 *filename*  
 Nombre de archivo de salida definido por el usuario.  Reemplaza al nombre predeterminado.  
  
## Comentarios  
 La opción \/OUT invalida el nombre y la ubicación predeterminados del programa que crea el vinculador.  
  
 De manera predeterminada, el vinculador compone el nombre del archivo con en el nombre base del primer archivo .obj especificado y la extensión correspondiente \(.exe o .dll\).  
  
 Esta opción utiliza el nombre base predeterminado de los archivos de asignaciones \(.mapfile\) o las bibliotecas de importación.  Para obtener información detallada, vea [Generar archivo de asignaciones](../../build/reference/map-generate-mapfile.md) \(\/MAP\) y [\/IMPLIB](../../build/reference/implib-name-import-library.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **General**.  
  
4.  Modifique la propiedad **Archivo de resultados**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)