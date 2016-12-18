---
title: "/DYNAMICBASE (Usar selecci&#243;n aleatoria del dise&#241;o del espacio de direcciones) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.RandomizedBaseAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DYNAMICBASE (opción del vinculador)"
  - "DYNAMICBASE (opción del vinculador)"
  - "-DYNAMICBASE (opción del vinculador)"
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /DYNAMICBASE (Usar selecci&#243;n aleatoria del dise&#241;o del espacio de direcciones)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica si debe generarse una imagen ejecutable que puede reubicarse aleatoriamente durante la carga mediante la característica de selección aleatoria del diseño del espacio de direcciones \(ASLR\) de [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)].  
  
## Sintaxis  
  
```  
/DYNAMICBASE[:NO]  
```  
  
## Comentarios  
 De manera predeterminada, \/DYNAMICBASE está activada.  
  
 Esta opción modifica el encabezado de un archivo ejecutable para indicar si la aplicación debería reubicarse de forma aleatoria en el momento de la carga.  
  
 La aleatoriedad de diseño de espacio de direcciones se admite en [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)].  
  
### Para establecer esta opción del vinculador en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **Vinculador**.  
  
4.  Seleccione la página de propiedades **Avanzadas**.  
  
5.  Modifique la propiedad **Dirección base aleatoria**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)