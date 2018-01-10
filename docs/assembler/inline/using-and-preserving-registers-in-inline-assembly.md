---
title: "Uso y conservación de registros en un ensamblado en línea | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 66805c6e9331f55beb01b13a536596c53e35049c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>Uso y conservación de registros en un ensamblado alineado
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 En general, no se debe suponer que un registro tendrá un valor determinado cuando se inicia un bloque `__asm`. No está garantizado que los valores del registro se conserven entre bloques `__asm` separados. Si se finaliza un bloque de código alineado y se inicia otro, no se puede confiar en que los registros del segundo bloque retengan sus valores desde el primer bloque. Un bloque `__asm` hereda los valores de registro resultantes del flujo de control normal.  
  
 Si usa la convención de llamada `__fastcall`, el compilador pasa argumentos de función en registros en lugar de en la pila. Esto puede crear problemas en funciones con bloques `__asm` porque una función no tiene ninguna manera de distinguir qué parámetro está en cada registro. Si la función recibe un parámetro en EAX e inmediatamente almacena algo más en EAX, el parámetro original se pierde. Además, debe guardar el registro ECX en cualquier función declarada con `__fastcall`.  
  
 Para evitar tales conflictos de registro, no use la convención `__fastcall` para funciones que contengan un bloque `__asm`. Si especifica la convención `__fastcall` globalmente con la opción del compilador /Gr, declare cada función que contenga un bloque `__asm` con `__cdecl` o `__stdcall`. (El atributo `__cdecl` indica al compilador que use la convención de llamada de C para esa función). Si no compila con /Gr, evite declarar la función con el atributo `__fastcall`.  
  
 Cuando use `__asm` para escribir lenguaje de ensamblado en funciones de C/C++, no necesitará conservar los registros EAX, EBX, ECX, EDX, ESI o EDI. Por ejemplo, en la POWER2. Ejemplo de C en [escribir funciones con ensamblado alineado](../../assembler/inline/writing-functions-with-inline-assembly.md), el `power2` función no conserva el valor en el registro EAX. Sin embargo, el uso de estos registros afectará a la calidad del código, porque el asignador de registro no puede usarlos para almacenar valores a través de bloques `__asm`. Además, usando EBX, ESI o EDI en el código de ensamblado alineado, se fuerza el compilador para guardar y restaurar esos registros en el prólogo y en el epílogo de la función.  
  
 Debe conservar otros registros que use (tales como DS, SS, SP, BP y los registros de marca) para el ámbito del bloque `__asm`. Debe conservar los registros ESP y EBP a menos que tenga alguna razón para cambiarlos (para cambiar pilas, por ejemplo). Consulte también [optimizar el código ensamblador en línea](../../assembler/inline/optimizing-inline-assembly.md).  
  
 Algunos tipos SSE requieren la alineación de la pila de ocho bytes, forzando al compilador para que emita código de dinámico de alineación de pila. Para poder tener acceso a las variables locales y a los parámetros de función después de la alineación, el compilador mantiene dos punteros de marco.  Si el compilador realiza la omisión de puntero de marco (FPO), usará EBP y ESP.  Si el compilador no realiza FPO, usará EBX y EBP. Para asegurarse de que el código se ejecuta correctamente, no modifique EBX en código asm si la función requiere la alineación dinámica de pila, porque podría alterar el puntero de marco. Saque los tipos alineados de ocho bytes de la función o evite usar EBX.  
  
> [!NOTE]
>  Si el código de ensamblado alineado cambia la marca de dirección mediante instrucciones STD o CLD, debe restablecer la marca a su valor original.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Ensamblador insertado](../../assembler/inline/inline-assembler.md)