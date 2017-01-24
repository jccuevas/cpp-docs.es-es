---
title: "/IMPLIB (Asignar nombre a la biblioteca de importaci&#243;n) | Microsoft Docs"
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
  - "/implib"
  - "VC.Project.VCLinkerTool.ImportLIbrary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/IMPLIB (opción del vinculador)"
  - "IMPLIB (opción del vinculador)"
  - "-IMPLIB (opción del vinculador)"
  - "bibliotecas de importación, reemplazar nombre predeterminado"
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /IMPLIB (Asignar nombre a la biblioteca de importaci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/IMPLIB:filename  
```  
  
## Comentarios  
 donde:  
  
 *filename*  
 Nombre especificado por el usuario para la biblioteca de importación.  Reemplaza al nombre predeterminado.  
  
## Comentarios  
 La opción \/IMPLIB reemplaza el nombre predeterminado de la biblioteca de importación creada por LINK al generar un programa con exportaciones.  El nombre predeterminado se forma a partir del nombre base del archivo de salida principal y la extensión .lib.  Un programa contendrá exportaciones si se especifican uno o varios de los siguientes aspectos:  
  
-   La palabra clave [\_\_declspec\(dllexport\)](../../cpp/dllexport-dllimport.md) en el código fuente.  
  
-   [Una instrucción EXPORTS](../../build/reference/exports.md) en un archivo .def.  
  
-   Una especificación [\/EXPORT](../../build/reference/export-exports-a-function.md) en un comando LINK.  
  
 LINK hará caso omiso de \/IMPLIB cuando no se esté creando una biblioteca de importación.  Si no se especifican exportaciones, LINK no creará una biblioteca de importación.  Si se utiliza un archivo de exportación en la generación, LINK supondrá que ya existe una biblioteca de importación y no la creará.  Para obtener información acerca de las bibliotecas de importación y los archivos de exportación, vea [Referencia de LIB](../../build/reference/lib-reference.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Avanzadas**.  
  
4.  Modifique la propiedad **Biblioteca de importación**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)