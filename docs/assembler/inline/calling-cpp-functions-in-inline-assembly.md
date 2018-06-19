---
title: Llamar a funciones de C++ en el código ensamblador en línea | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffbd8038d240bc2ab0240d172d914790b6ca02ab
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049628"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Llamada a funciones C++ en el ensamblado alineado
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Un bloque `__asm` solo puede llamar a funciones globales de C++ que no estén sobrecargadas. Si llama a una función global sobrecargada de C++ o a una función miembro de C++, el compilador genera un error.  
  
 También puede llamar a cualquier función declarada con **extern "C"** vinculación. Esto permite un `__asm` bloque dentro de un programa de C++ para llamar a funciones de la biblioteca de C, porque todos los archivos de encabezado estándar declaran las funciones de biblioteca con **extern "C"** vinculación.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Ensamblador insertado](../../assembler/inline/inline-assembler.md)