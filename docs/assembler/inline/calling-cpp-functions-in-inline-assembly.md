---
title: Llamada a funciones C++ en el ensamblado alineado
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
ms.openlocfilehash: 666f7b2a59f0d48a14be54a439b6402f2a4d3128
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167275"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Llamada a funciones C++ en el ensamblado alineado

**Específicos de Microsoft**

Un bloque `__asm` solo puede llamar a funciones globales de C++ que no estén sobrecargadas. Si llama a una función global sobrecargada de C++ o a una función miembro de C++, el compilador genera un error.

También puede llamar a cualquier función declarada con **extern "C"** vinculación. Esto permite un `__asm` bloque dentro de un programa de C++ para llamar a las funciones de biblioteca de C, porque todos los archivos de encabezado estándar declaran las funciones de biblioteca para tener **extern "C"** vinculación.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Ensamblador insertado](../../assembler/inline/inline-assembler.md)<br/>