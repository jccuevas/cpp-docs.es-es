---
title: "/NXCOMPAT (compatible con la prevenci&#243;n de ejecuci&#243;n de datos) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/NXCOMPAT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/NXCOMPAT (opción del vinculador)"
  - "NXCOMPAT (opción del vinculador)"
  - "-NXCOMPAT (opción del vinculador)"
ms.assetid: 5858e7ff-24d3-4ac3-9046-af2c9e220d9b
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /NXCOMPAT (compatible con la prevenci&#243;n de ejecuci&#243;n de datos)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Indica que se probó una aplicación ejecutable para que fuera compatible con la característica de Prevención de ejecución de datos de Windows.  
  
## Sintaxis  
  
```  
/NXCOMPAT[:NO]  
```  
  
## Comentarios  
 La opción **\/NXCOMPAT** está activada de manera predeterminada.  
  
 **\/NXCOMPAT:NO** puede utilizarse para especificar explícitamente un archivo ejecutable como no compatible con la Prevención de ejecución de datos.  
  
 Para obtener más información sobre la Prevención de ejecución de datos, vea estos artículos:  
  
-   [Descripción detallada de la característica Prevención de ejecución de datos \(DEP\)](http://go.microsoft.com/fwlink/?LinkID=157771) en el sitio web de Ayuda y soporte técnico de Microsoft  
  
-   [Prevención de ejecución de datos](http://go.microsoft.com/fwlink/?LinkID=157770) en el sitio web de MSDN  
  
-   [Prevención de ejecución de datos \(incrustada en Windows\)](http://go.microsoft.com/fwlink/?LinkID=157768) en el sitio web de MSDN  
  
### Para establecer esta opción del vinculador en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)