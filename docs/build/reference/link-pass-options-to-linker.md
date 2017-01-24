---
title: "/link (Pasar opciones al vinculador) | Microsoft Docs"
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
  - "/link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/link (opción del compilador) [C++]"
  - "cl.exe (compilador) [C++], pasar opciones al vinculador"
  - "link (opción del compilador) [C++]"
  - "-link (opción del compilador) [C++]"
  - "vinculador [C++], pasar opciones a"
  - "pasar opciones al vinculador"
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /link (Pasar opciones al vinculador)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Pasa una o más opciones del vinculador al vinculador.  
  
## Sintaxis  
  
```  
/link linkeroptions  
```  
  
## Argumentos  
 `linkeroptions`  
 La opción u opciones que se pasan al vinculador.  
  
## Comentarios  
 La opción **\/link** y sus opciones del vinculador deben aparecer detrás de los nombres de archivo y de las opciones de CL.  Es necesario incluir un espacio entre **\/link** y `linkeroptions`.  Para obtener más información, vea [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en una página de propiedades del vinculador.  
  
4.  Modifique una o varias propiedades.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Esta opción del compilador no se puede modificar mediante programación.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)