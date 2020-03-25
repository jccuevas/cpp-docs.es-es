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
ms.openlocfilehash: f16e466ebb5f31231411eaaf9a1a85bfcc46a34d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169583"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Llamada a funciones C++ en el ensamblado alineado

**Específicos de Microsoft**

Un bloque `__asm` solo puede llamar a funciones globales de C++ que no estén sobrecargadas. Si llama a una función global sobrecargada de C++ o a una función miembro de C++, el compilador genera un error.

También puede llamar a cualquier función declarada con la vinculación **extern "C"** . Esto permite que un bloque `__asm` dentro C++ de un programa llame a las funciones de la biblioteca de C, ya que todos los archivos de encabezado estándar declaran las funciones de la biblioteca para que tengan vinculación **extern "C"** .

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Ensamblador insertado](../../assembler/inline/inline-assembler.md)<br/>
