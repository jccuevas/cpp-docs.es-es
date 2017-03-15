---
title: "Convenciones de nomenclatura de la biblioteca | Microsoft Docs"
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
  - "convenciones de código, nombres de la biblioteca MFC"
  - "aplicaciones de consola, versiones de la biblioteca MFC"
  - "convenciones [C++], nombres de la biblioteca MFC"
  - "bibliotecas [C++], static"
  - "MFC (bibliotecas), convenciones de nomenclatura"
  - "NAFXCW.LIB"
  - "NAFXCWD.LIB"
  - "convenciones de nomenclatura [C++], bibliotecas de código del objeto MFC"
  - "bibliotecas de código del objeto"
  - "bibliotecas de código del objeto, convenciones de nomenclatura MFC"
ms.assetid: 39fe7d93-5a14-4c6a-b16c-bf318fa01278
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Convenciones de nomenclatura de la biblioteca
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Bibliotecas de código objeto para MFC utilizan las convenciones de nomenclatura siguientes.  Los nombres de biblioteca tienen el formulario  
  
 w`d`.LIB de`c`*de uAFX*  
  
 donde marcadores las letras mostradas en minúsculas cursivas para los especificadores cuyos significados se muestran en la tabla siguiente:  
  
### Convenciones de nomenclatura para bibliotecas  
  
|Especificador|Valores y significados|  
|-------------------|----------------------------|  
|*u*|ANSI \(n\) o Unicode \(u\)|  
|`c`|Tipo de programa a crear: C\=all|  
|`d`|Depuración o lanzamiento: D\=Debug; omita el especificador de lanzamiento|  
  
 El valor predeterminado es compilar una aplicación ANSI de las ventanas de depuración para la plataforma de Intel: NAFXCWD.Lib.  Todas las bibliotecas incluidas en la tabla siguiente son archivo incluido en el directorio de \\atlmfc\\lib en Visual C\+\+ CD\-ROM.  
  
### Convenciones de nomenclatura para bibliotecas de vínculos estáticos  
  
|Biblioteca|Descripción|  
|----------------|-----------------|  
|NAFXCW.LIB|Biblioteca de vínculos estáticos de MFC, versión de lanzamiento|  
|NAFXCWD.LIB|Biblioteca de vínculos estáticos de MFC, versión de depuración|  
|UAFXCW.LIB|Biblioteca de vínculos estáticos de MFC con compatibilidad de Unicode, versión de lanzamiento|  
|UAFXCWD.LIB|Biblioteca de vínculos estáticos de MFC con compatibilidad de Unicode, versión de depuración|  
  
> [!NOTE]
>  Si necesita compilar una versión de la biblioteca, vea el archivo Readme.txt en el directorio de \\atlmfc\\src\\mfc.  Este archivo describe el uso del archivo MAKE proporcionado por NMAKE.  
  
 Para obtener más información, vea [Convenciones de nomenclatura para archivos DLL de MFC](../build/naming-conventions-for-mfc-dlls.md) y [Versiones de Unicode de las bibliotecas MFC](../mfc/unicode-in-mfc.md).  
  
## Vea también  
 [Versiones de la biblioteca MFC](../mfc/mfc-library-versions.md)