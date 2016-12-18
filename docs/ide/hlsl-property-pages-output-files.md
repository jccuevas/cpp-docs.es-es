---
title: "P&#225;ginas de propiedades HLSL: archivos de salida | Microsoft Docs"
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
  - "VC.Project.FXCompilerTool.AssemblerOutput"
  - "VC.Project.FXCompilerTool.ObjectFileOutput"
  - "VC.Project.FXCompilerTool.HeaderFileOutput"
  - "VC.Project.FXCompilerTool.VariableName"
  - "VC.Project.FXCompilerTool.AssemblerOutputFile"
dev_langs: 
  - "C++"
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
caps.latest.revision: 5
caps.handback.revision: 5
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# P&#225;ginas de propiedades HLSL: archivos de salida
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para configurar las propiedades siguientes del compilador de HLSL \(fxc.exe\), utilice la propiedad **ARCHIVOS DE SALIDA** .  Para obtener información sobre cómo tener acceso a la página de propiedades **ARCHIVOS DE SALIDA** en la carpeta de HLSL, vea [Cómo: Especificar propiedades de proyecto con páginas de propiedades](../misc/how-to-specify-project-properties-with-property-pages.md).  
  
## Lista de UIElement  
 **Nombre de la variable de encabezado**  
 Especifica el nombre de una matriz que es código objeto codificadas utilizado de HLSL.  La matriz se incluye en un archivo de encabezado generado por el compilador de HLSL.  El nombre del archivo de encabezado se especifica mediante la propiedad **Nombre del archivo de encabezado** .  
  
 Esta propiedad corresponde a **\/Vn\[name\]** el argumento de línea de comandos.  
  
 **Nombre del archivo de encabezado**  
 Especifica el nombre del archivo de encabezado generado por el compilador de HLSL.  El encabezado contiene el código objeto de HLSL que se codifica en una matriz.  El nombre de la matriz es especificado por la propiedad **Nombre de la variable de encabezado** .  
  
 Esta propiedad corresponde a **\/Fh\[name\]** el argumento de línea de comandos.  
  
 **Nombre de archivo de objeto**  
 Especifica el nombre del archivo objeto generado por el compilador de HLSL.  De forma predeterminada, el valor es **% $ \(OutDir\) \(filename\) .cso**.  
  
 Esta propiedad corresponde a **\/Fo\[name\]** el argumento de línea de comandos.  
  
 **Salida de código ensamblador**  
 **Lista de ensamblado \- solo \(\/Fc\)** para generar simplemente instrucciones en lenguaje de ensamblado.  **Código y hex. \(\/Fx\) del ensamblado** para generar instrucciones de lenguaje de ensamblado y el Op. Sys. \- código correspondiente en hexadecimal.  De forma predeterminada, no se genera ninguna lista.  
  
 **Archivo de salida de código ensamblador**  
 Especifica el nombre de archivo de la lista de ensamblado generado por el compilador de HLSL.  
  
 Esta propiedad corresponde a los argumentos de línea de comandos de **\/Fc\[name\]** y de **\/Fx \[name\]** .  
  
## Vea también  
 [Páginas de propiedades HLSL](../ide/hlsl-property-pages.md)   
 [Páginas de propiedades HLSL: General](../ide/hlsl-property-pages-general.md)   
 [Páginas de propiedades HLSL: Avanzadas](../ide/hlsl-property-pages-advanced.md)