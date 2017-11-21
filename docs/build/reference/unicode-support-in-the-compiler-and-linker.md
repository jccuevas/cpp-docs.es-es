---
title: Compatibilidad con Unicode en el compilador y el vinculador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
dev_langs: C++
helpviewer_keywords: Unicode, Visual C++
ms.assetid: acc1d322-56b9-4696-a30e-2af891a4e288
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 15fefc4cc44edfd67bd8ba89ab68c6965c8639a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>Compatibilidad con Unicode en el compilador y el vinculador
Este tema describe la compatibilidad de Unicode de las herramientas de compilación de Visual C++.  
  
 Nombres de archivo  
 Los nombres de archivo especificado en la línea de comandos o en las directivas de compilador (como #include) ahora pueden contener caracteres Unicode.  
  
 Archivos de código fuente  
 Ahora se admiten caracteres Unicode en identificadores, macros, literales de cadena y carácter y en comentarios.  Ahora también se admiten nombres de carácter universal.  
  
 Unicode se puede especificar en un archivo de código fuente en las codificaciones siguientes:  
  
-   UTF-16 little endian con o sin marca de orden de bytes (BOM)  
  
-   UTF-16 big endian con o sin marca BOM  
  
-   UTF-8 con BOM  
  
 Resultado  
 Durante la compilación, el compilador genera diagnósticos en la consola en UTF-16.  Los caracteres que se pueden mostrar en la consola dependen de las propiedades de la ventana de consola.  Resultados del compilador redirigidos a un archivo está en la página de códigos de consola actual de ANSI.  
  
 Archivos de respuesta del vinculador y. DEF (archivos)  
 Archivos de respuesta y DEF (archivos) pueden ser UTF-16 con una marca de orden de bytes o ANSI.  Anteriormente sólo se admitía ANSI.  
  
 ASM y volcados de .cod  
 ASM y volcados de .cod están en ANSI predeterminada por compatibilidad con MASM.  Use /FAu para generar UTF-8.  Tenga en cuenta que si especifica/FAS, el origen entremezclados siguiendo solo se imprimirán directamente y que puede ser confusa, por ejemplo, si el código fuente es UTF-8 y no se especifica/FAsu.  
  
 Puede habilitar nombres de archivo Unicode en el entorno de desarrollo (vea [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md)), seleccione la herramienta apropiada y seleccionando la **habilitar archivos de respuesta Unicode** propiedad, que está habilitada de forma predeterminada. Uno de los motivos que puede cambiar este valor predeterminado es si se modifica el entorno de desarrollo para utilizar un compilador que no es compatible con Unicode.  
  
## <a name="see-also"></a>Vea también  
 [Compilar el código de C o C++ en la línea de comandos](../../build/building-on-the-command-line.md)