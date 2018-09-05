---
title: Llamar a funciones de C++ en ensamblado alineado | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: 4717ae24dc1a0b6f51f7a00f68f6569c2f988c65
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678949"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Llamada a funciones C++ en el ensamblado alineado

**Específicos de Microsoft**

Un bloque `__asm` solo puede llamar a funciones globales de C++ que no estén sobrecargadas. Si llama a una función global sobrecargada de C++ o a una función miembro de C++, el compilador genera un error.

También puede llamar a cualquier función declarada con **extern "C"** vinculación. Esto permite un `__asm` bloque dentro de un programa de C++ para llamar a las funciones de biblioteca de C, porque todos los archivos de encabezado estándar declaran las funciones de biblioteca para tener **extern "C"** vinculación.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Ensamblador insertado](../../assembler/inline/inline-assembler.md)<br/>