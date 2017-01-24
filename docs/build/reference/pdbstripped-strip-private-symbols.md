---
title: "/PDBSTRIPPED (Quitar s&#237;mbolos privados) | Microsoft Docs"
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
  - "/pdbstripped"
  - "VC.Project.VCLinkerTool.StripPrivateSymbols"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb (archivos), eliminación de símbolos privados"
  - "/PDBSTRIPPED (opción del vinculador)"
  - "PDB (archivos), eliminación de símbolos privados"
  - "PDBSTRIPPED (opción del vinculador)"
  - "-PDBSTRIPPED (opción del vinculador)"
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /PDBSTRIPPED (Quitar s&#237;mbolos privados)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/PDBSTRIPPED:pdb_file_name  
```  
  
## Comentarios  
 donde:  
  
 *pdb\_file\_name*  
 Nombre especificado por el usuario para la base de datos de programa \(PDB\) reducida que crea el vinculador.  
  
## Comentarios  
 La opción \/PDBSTRIPPED crea un segundo archivo de base de datos de programa \(PDB\) cuando se genera la imagen de un programa con cualquiera de las opciones del compilador o el vinculador que generan archivos PDB \([\/DEBUG](../../build/reference/debug-generate-debug-info.md), [\/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), \/Zd o \/Zi\).  En este segundo archivo PDB se omiten los símbolos que no se desea suministrar a los clientes.  El segundo archivo sólo contiene:  
  
-   Símbolos públicos  
  
-   La lista de archivos objeto y las partes del archivo ejecutable a las que contribuyen  
  
-   Los registros de depuración de la optimización de punteros de marco \(FPO\) utilizados para recorrer la pila  
  
 El archivo PDB reducido no contiene:  
  
-   Información de tipos  
  
-   Información de números de línea  
  
-   Símbolos CodeView por archivos objeto, como los de funciones, locales y datos estáticos  
  
 El archivo PDB completo seguirá generándose si se utiliza \/PDBSTRIPPED.  
  
 Si no crea un archivo PDB, \/PDBSTRIPPED se pasará por alto.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Depurar**.  
  
4.  Modifique la propiedad **Quitar símbolos privados**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)