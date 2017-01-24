---
title: "Archivos .obj como entrada del vinculador | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos .obj como entrada del vinculador"
  - "COFF (archivos)"
  - "LINK (herramienta) [C++], .obj (archivos)"
  - "vinculador [C++], archivos OBJ como entrada"
  - "archivos OBJ como entrada del vinculador"
  - "archivos objeto, resultados del vinculador"
  - "OMF (archivos objeto)"
ms.assetid: 3028e423-8b10-4972-8eb4-6e9ae58f0a26
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Archivos .obj como entrada del vinculador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La herramienta del vinculador \(LINK.EXE\) acepta archivos .obj en formato de archivo de objeto común \(COFF\).  
  
## Comentarios  
 Microsoft proporciona un documento descargable que define el formato de archivo de objeto común.  Para obtener más información, revisión 8,1 de descarga o posterior de [Portable ejecutable de Microsoft y especificación de formato de archivo objeto común](http://go.microsoft.com/fwlink/?LinkId=93292).  
  
## Compatibilidad con Unicode  
 A partir de Visual Studio 2005, el compilador de Microsoft Visual C\+\+ admite caracteres Unicode en identificadores como se define en los estándares ISO\/IEC C y C\+\+.  Las versiones anteriores del compilador sólo admitían caracteres ASCII en identificadores.  Para admitir Unicode en los nombres de funciones, clases y elementos estáticos, el compilador y el vinculador usan la codificación UTF\-8 Unicode para los símbolos COFF en los archivos .obj.  La codificación UTF\-8 ofrece compatibilidad ascendente con la codificación ASCII usada en versiones anteriores de Visual Studio.  
  
 Para obtener más información sobre el compilador y el vinculador, vea [Compatibilidad con Unicode en el compilador y el vinculador](../../build/reference/unicode-support-in-the-compiler-and-linker.md).  Para obtener más información sobre el estándar Unicode, vea [Unicode](http://go.microsoft.com/fwlink/?LinkId=37123) organization.  
  
## Vea también  
 [Archivos de entrada de LINK](../../build/reference/link-input-files.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [Compatibilidad con Unicode](../../text/support-for-unicode.md)   
 [Compatibilidad con Unicode en el compilador y el vinculador](../../build/reference/unicode-support-in-the-compiler-and-linker.md)   
 [Estándar Unicode](http://go.microsoft.com/fwlink/?LinkId=37123)   
 [Common object file format specification](http://go.microsoft.com/fwlink/?LinkId=93292)