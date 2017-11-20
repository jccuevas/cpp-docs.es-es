---
title: "Llamar a funciones de C++ en el código ensamblador en línea | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0c91829eac3247255d8fe3cb966a61fca5319f94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="calling-c-functions-in-inline-assembly"></a>Llamada a funciones C++ en el ensamblado alineado
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Un bloque `__asm` solo puede llamar a funciones globales de C++ que no estén sobrecargadas. Si llama a una función global sobrecargada de C++ o a una función miembro de C++, el compilador genera un error.  
  
 También puede llamar a cualquier función declarada con **extern "C"** vinculación. Esto permite un `__asm` bloque dentro de un programa de C++ para llamar a funciones de la biblioteca de C, porque todos los archivos de encabezado estándar declaran las funciones de biblioteca con **extern "C"** vinculación.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Ensamblador insertado](../../assembler/inline/inline-assembler.md)