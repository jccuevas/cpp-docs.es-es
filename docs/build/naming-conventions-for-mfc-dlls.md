---
title: "Convenciones de nomenclatura para archivos DLL de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], nombres de bibliotecas"
  - "DLL [C++], convenciones de nomenclatura"
  - "bibliotecas [C++], nombres de archivos DLL de MFC"
  - "DLL de MFC [C++], convenciones de nomenclatura"
  - "bibliotecas MFC [C++], convenciones de nomenclatura"
  - "convenciones de nomenclatura [C++], archivos DLL de MFC"
  - "versiones de DLL compartidas [C++]"
ms.assetid: 0db9c3f3-87d3-40e8-8964-250f9d2a2209
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Convenciones de nomenclatura para archivos DLL de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los archivos DLL y las bibliotecas incluidos en MFC utilizan una convención de nomenclatura estructurada.  Esto facilita determinar qué archivo DLL o biblioteca debe utilizar para cada propósito.  
  
 Las bibliotecas de importación necesarias para compilar aplicaciones o archivos DLL de extensión que utilicen estos archivos DLL tienen el mismo nombre base que el archivo DLL, pero con una extensión de nombre de archivo .lib.  
  
### Convención de nomenclatura de archivos DLL compartidos  
  
|Archivo DLL|Descripción|  
|-----------------|-----------------|  
|MFCx0.DLL|Archivo DLL de MFC, versión de lanzamiento ANSI|  
|MFCx0U.DLL|Archivo DLL de MFC, versión de lanzamiento Unicode|  
|MFCx0D.DLL|Archivo DLL de MFC, versión de depuración ANSI|  
|MFCx0UD.DLL|Archivo DLL de MFC, versión de depuración Unicode|  
  
 Si una aplicación o un archivo DLL de extensión se vincula dinámicamente al archivo DLL compartido de MFC, deberá incluir MFCx0.DLL en el producto.  Si la aplicación requiere compatibilidad con Unicode, deberá incluir en su lugar MFCx0U.DLL.  
  
 Si el archivo DLL se vincula estáticamente a MFC, deberá vincularlo a una de las bibliotecas MFC estáticas.  A estas versiones se les asignan nombres que siguen la convención \[N&#124;U\]AFXCW\[D\].LIB.  Para obtener más información, vea la tabla "Convenciones de nomenclatura para bibliotecas de vínculos estáticos" en [Convenciones de nomenclatura para bibliotecas](../mfc/library-naming-conventions.md) \(MFC\).  
  
 Para obtener una lista de los archivos DLL de Visual C\+\+ que pueden distribuirse con las aplicaciones, lea el archivo Redist.txt del directorio de instalación de Visual Studio.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Convención de nomenclatura para bibliotecas](../mfc/library-naming-conventions.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)