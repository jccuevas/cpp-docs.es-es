---
title: "/STACK (Asignaciones de la pila) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.StackReserveSize"
  - "VC.Project.VCLinkerTool.StackCommitSize"
  - "/stack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "STACK (opción del vinculador)"
  - "-STACK (opción del vinculador)"
  - "asignación de memoria, pila"
  - "/STACK (opción del vinculador)"
  - "pila, establecer el tamaño"
ms.assetid: 73283660-e4bd-47cc-b5ca-04c5d739034c
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# /STACK (Asignaciones de la pila)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/STACK:reserve[,commit]  
```  
  
## Comentarios  
 La opción \/STACK establece el tamaño en bytes de la pila.  Solo debe usar esta opción cuando compile un archivo .exe.  
  
 El valor `reserve` especifica la asignación total de la pila en la memoria virtual.  Para los equipos ARM, x86 y [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], el tamaño de pila predeterminado es de 1 MB.  
  
 El argumento `commit` está sujeto a interpretación por el sistema operativo.  En Windows\/Windows RT especifica la cantidad de memoria física que se debe asignar de una sola vez.  La memoria virtual confirmada hace que se reserve espacio en el archivo de paginación.  Si se asigna un valor mayor a `commit`, se ahorrará tiempo cuando la aplicación necesite más espacio de la pila, pero aumentarán los requisitos de memoria y, posiblemente, el tiempo de inicio.  Para los equipos ARM, x86 y [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], el valor de confirmación predeterminado es de 4 kB.  
  
 Especifique los valores `reserve` y `commit` en notación decimal o en la notación del lenguaje C.  
  
 Otro método para establecer el tamaño de la pila consiste en utilizar la instrucción [STACKSIZE](../../build/reference/stacksize.md) en un archivo de definición de módulos \(.def\).  **STACKSIZE** reemplaza la opción \/STACK \(asignaciones de pila\) en caso de que ambas estén especificadas.  Una vez compilado el archivo .exe, puede cambiar el tamaño de la pila con la herramienta [EDITBIN](../../build/reference/editbin-reference.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **Vinculador**.  
  
3.  Seleccione la página de propiedades **Sistema**.  
  
4.  Modifique una de las propiedades siguientes:  
  
    -   **Tamaño confirmado de la pila**  
  
    -   **Tamaño de reserva de la pila**  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea las propiedades <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)