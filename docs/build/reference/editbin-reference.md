---
title: "Referencia de EDITBIN | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "editbin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "datos binarios, editar"
  - "COFF (archivos), editar"
  - "EDITBIN (programa)"
  - "archivos objeto, modificar"
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Referencia de EDITBIN
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft COFF Binary File Editor \(EDITBIN.EXE\) modifica archivos binarios en formato Common Object File Format \(COFF\).  Puede utilizar EDITBIN para modificar archivos objeto, archivos ejecutables y bibliotecas de vínculos dinámicos \(DLL\).  
  
> [!NOTE]
>  Sólo puede iniciar esta herramienta desde el símbolo del sistema de [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)].  No puede iniciar desde una ventana del símbolo del sistema o desde el Explorador de archivos.  
  
 No se puede utilizar EDITBIN en archivos producidos con la opción de compilador [\/GL](../../build/reference/gl-whole-program-optimization.md).  Para modificar archivos binarios producidos con la opción \/GL tendrá que volver a compilar y vincular.  
  
-   [Línea de comandos de EDITBIN](../../build/reference/editbin-command-line.md)  
  
-   [Opciones de EDITBIN](../../build/reference/editbin-options.md)  
  
## Vea también  
 [Herramientas de compilación de C\/C\+\+](../../build/reference/c-cpp-build-tools.md)