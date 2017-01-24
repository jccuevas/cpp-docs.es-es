---
title: "/STUB (Nombre del archivo de c&#243;digo auxiliar de MS-DOS) | Microsoft Docs"
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
  - "/stub"
  - "VC.Project.VCLinkerTool.DosStub"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/STUB (opción del vinculador)"
  - "nombre del archivo de código auxiliar de MS-DOS (opción del vinculador)"
  - "STUB (opción del vinculador)"
  - "-STUB (opción del vinculador)"
  - "Win32 [C++], asociar un programa de código auxiliar de MS-DOS"
  - "API de Windows [C++], asociar un programa de código auxiliar de MS-DOS"
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /STUB (Nombre del archivo de c&#243;digo auxiliar de MS-DOS)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/STUB:filename  
```  
  
## Comentarios  
 donde:  
  
 *filename*  
 Aplicación de MS\-DOS.  
  
## Comentarios  
 La opción \/STUB asocia un programa de código auxiliar de MS\-DOS a un programa de Win32.  
  
 El programa de código auxiliar se invoca si el archivo es ejecutado en MS\-DOS.  Aunque suelen presentar un mensaje acorde, cualquier aplicación válida de MS\-DOS puede ser un programa de código auxiliar.  
  
 En la línea de comandos, el nombre de archivo del programa de código auxiliar \(*filename*\) se especifica detrás de un signo de dos puntos \(:\).  El vinculador comprueba este nombre del archivo y genera un mensaje de error si no es ejecutable.  El programa deberá ser un archivo .exe; un archivo .com no es válido como programa de código auxiliar.  
  
 Si no se usa esta opción, el vinculador asociará un programa de código auxiliar predeterminado que generará el siguiente mensaje:  
  
```  
This program cannot be run in MS-DOS mode.  
```  
  
 Al compilar un controlador de dispositivo virtual, *filename* le permite al usuario especificar un nombre de archivo con la estructura IMAGE\_DOS\_HEADER \(definida en WINNT.H\) para que se utilice en el VxD en lugar del encabezado predeterminado.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)