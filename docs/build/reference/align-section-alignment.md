---
title: "/ALIGN (Alineaci&#243;n de secci&#243;n) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.Alignment"
  - "/align"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ALIGN (opción del vinculador)"
  - "ALIGN (opción del vinculador)"
  - "-ALIGN (opción del vinculador)"
  - "alineación de sección"
  - "secciones"
  - "secciones, especificar la alineación"
ms.assetid: f2f8ac24-e90e-4bea-8205-f2960a3b1740
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ALIGN (Alineaci&#243;n de secci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ALIGN[:number]  
```  
  
## Comentarios  
 donde:  
  
 `number`  
 El valor de alineación.  
  
## Comentarios  
 La opción \/ALIGN especifica la alineación de cada sección incluida en el espacio de dirección lineal del programa.  El argumento `number` se expresa en bytes y debe ser una potencia de dos.  El valor predeterminado es 4 KB \(4096\).  El vinculador emite una advertencia si la alineación produce una imagen no válida.  
  
 Salvo que se esté programando una aplicación del tipo de un controlador de dispositivo, no será necesario modificar la alineación.  
  
 Es posible modificar la alineación de una sección concreta por medio del parámetro de alineación de la opción [\/SECTION](../../build/reference/section-specify-section-attributes.md).  
  
 El valor de alineación especificado no puede ser menor que la alineación de la mayor de las secciones.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)