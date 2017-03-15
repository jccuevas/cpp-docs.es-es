---
title: "/HEAP (Establecer el tama&#241;o del mont&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.HeapCommitSize"
  - "/heap"
  - "VC.Project.VCLinkerTool.HeapReserveSize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/HEAP (opción del vinculador)"
  - "asignación en el montón, establecer el tamaño del montón"
  - "HEAP (opción del vinculador)"
  - "-HEAP (opción del vinculador)"
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /HEAP (Establecer el tama&#241;o del mont&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/HEAP:reserve[,commit]  
```  
  
## Comentarios  
 La opción \/HEAP establece el tamaño del montón en bytes.  Esta opción sólo se puede usar al compilar archivos .exe.  
  
 El argumento *reserve* especifica la asignación total de memoria virtual del montón.  El tamaño predeterminado del montón es de 1 MB.  El vinculador redondeará el valor especificado a los 4 bytes más próximos.  
  
 El argumento opcional `commit` está sujeto a interpretación por el sistema operativo.  En Windows NT y Windows 2000, especifica la cantidad de memoria física que se debe asignar de una sola vez.  La memoria virtual confirmada hace que se reserve espacio en el archivo de paginación.  Si se confirma un valor más alto en `commit`, se ahorrará tiempo cuando la aplicación necesite más espacio del montón, pero también aumentarán los requisitos de memoria y, posiblemente, el tiempo de inicio.  
  
 Especifique los valores *reserve* y `commit` en notación decimal o en la notación del lenguaje C.  
  
 Es posible obtener esta misma funcionalidad mediante un archivo de definición de módulos con [HEAPSIZE](../../build/reference/heapsize.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Sistema**.  
  
4.  Modifique la propiedad **Tamaño dedicado del montón**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)