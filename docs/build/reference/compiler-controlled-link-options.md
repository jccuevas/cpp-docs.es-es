---
title: Opciones de LINK controladas por el compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: link
dev_langs: C++
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a0d73d46d17e14d5ce55a171887e693c425765ce
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-controlled-link-options"></a>Compiler-Controlled LINK Options
El compilador de CL llamará automáticamente a LINK a menos que especifique la opción/c.. CL proporciona cierto control sobre el vinculador a través de opciones de línea de comandos y argumentos. En la tabla siguiente se resume las características de CL que afectan a la vinculación.  
  
|Especificación de CL|Acción de CL que afecta a LINK|  
|----------------------|---------------------------------|  
|Cualquier extensión de nombre de archivo distinto. c, .cxx, .cpp o .def|Pasa un nombre de archivo como entrada de LINK|  
|*nombre de archivo*.def|Pasa/def:*filename*.def|  
|/F*número*|Pasa/Stack:*número*|  
|/FD*nombre de archivo*|Pasa/PDB:*nombre de archivo*|  
|/Fe*nombre de archivo*|Pasa/OUT:*nombre de archivo*|  
|/FM*nombre de archivo*|Pasa/Map:*nombre de archivo*|  
|/Gy|Crea funciones empaquetadas (COMDAT); permite la vinculación de nivel de función|  
|/LD|Pasa /DLL|  
|/LDd|Pasa /DLL|  
|/link|Pasa el resto de la línea de comandos a LINK|  
|/MD o /MT|Coloca un nombre de biblioteca predeterminado en el archivo .obj|  
|/MDd o /MTd|Coloca un nombre de biblioteca predeterminado en el archivo .obj. Define el símbolo **_DEBUG**|  
|/nologo|Pasa /NOLOGO|  
|/ Zd|Pasa/Debug|  
|Zi o/Z7|Pasa/Debug|  
|/Zl|Omite el nombre de la biblioteca predeterminada del archivo .obj|  
  
 Para obtener más información, consulte [Opciones del compilador](../../build/reference/compiler-options.md).  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)