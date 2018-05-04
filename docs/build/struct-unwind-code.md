---
title: UNWIND_CODE (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 104955d8-7e33-4c5a-b0c6-3254648f0af3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 068acacf88e9ac968b34c26bf76657fd33adf4f3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="struct-unwindcode"></a>UNWIND_CODE (Estructura)
La matriz de códigos de desenredado se usa para registrar la secuencia de operaciones en el prólogo que afectan a los registros no volátiles y RSP. Cada elemento de código tiene el formato siguiente:  
  
|||  
|-|-|  
|UBYTE|Desplazamiento en el prólogo|  
|UBYTE: 4|Código de operación de desenredo|  
|UBYTE: 4|Información de la operación|  
  
 La matriz se ordena por orden descendente de desplazamiento en el prólogo.  
  
 **Desplazamiento en el prólogo**  
 Desplazamiento desde el principio del prólogo del final de la instrucción que realiza esta operación, más 1 (es decir, el desplazamiento del inicio de la instrucción siguiente).  
  
 **Código de operación de desenredo**  
 Nota: Ciertos códigos de operación requieren un desplazamiento sin signo a un valor en el marco de pila local. Este desplazamiento es desde el inicio (dirección más baja) de la asignación fija de la pila. Si el campo Frame Register de UNWIND_INFO es cero, este desplazamiento es from RSP. Si el campo Frame Register es distinto de cero, este es el desplazamiento desde donde se encontraba RSP cuando se estableció el registro de FP. Esto es igual al registro de FP menos el desplazamiento del registro de FP (16 * desplazamiento del registro del marco de texto escalado en UNWIND_INFO). Si se usa un registro de FP, a continuación, cualquier código de desenredado tome un desplazamiento solo debe usarse después de establece el registro de FP en el prólogo.  
  
 Para todos los códigos de operación excepto UWOP_SAVE_XMM128 y UWOP_SAVE_XMM128_FAR, el desplazamiento siempre será un múltiplo de 8, porque todos los valores de la pila de interés se almacenan en límites de 8 bytes (la propia pila siempre es alineada de 16 bytes). Para los códigos de operación que admiten un desplazamiento corto (menos de 512 KB), el valor USHORT final en los nodos para este código mantiene el desplazamiento dividido por 8. Para los códigos de operación que admiten un desplazamiento largo (512 KB < = desplazamiento < 4GB), los dos nodos USHORT finales de este código mantenga el desplazamiento (en formato little-endian).  
  
 Para los códigos de operación UWOP_SAVE_XMM128 y UWOP_SAVE_XMM128_FAR, el desplazamiento siempre serán un múltiplo de 16, dado que todas las operaciones de registros de XMM de 128 bits se deben producir en memoria con alineación de 16 bytes. Por lo tanto, se utiliza un factor de escala de 16 para UWOP_SAVE_XMM128, permitiendo desplazamientos de menos de 1 millón.  
  
 El código de operación de desenredo es uno de los siguientes:  
  
 UWOP_PUSH_NONVOL (0) 1 nodo  
  
 Insertar un registro entero no variable, disminuyendo RSP en 8. La información de la operación es el número del registro. Tenga en cuenta que, debido a restricciones en los epílogos, códigos de desenredado UWOP_PUSH_NONVOL deben aparecen primeros en el prólogo y correspondientemente, los últimos en la matriz de códigos de desenredado. Esta ordenación relativa se aplica a todos los demás códigos de desenredado excepto UWOP_PUSH_MACHFRAME.  
  
 UWOP_ALLOC_LARGE (1) 2 o 3 nodos  
  
 Asignar un área de gran tamaño en la pila. Hay dos formas. Si la información de la operación es igual a 0, el tamaño de la asignación dividido por 8 se registra en la siguiente ranura, permitiendo una asignación de hasta 512 K - 8. Si la información de la operación es igual a 1, el tamaño de la asignación sin ajuste de escala se registra en las dos siguientes ranuras en formato little-endian, permitiendo asignaciones hasta 4GB - 8.  
  
 UWOP_ALLOC_SMALL (2) 1 nodo  
  
 Asignar un área pequeña en la pila. El tamaño de la asignación es el campo de información de la operación * 8 + 8, permitiendo asignaciones de 8 a 128 bytes.  
  
 El código de desenredo para una asignación de pila siempre debe utilizar la codificación más corta posible:  
  
|||  
|-|-|  
|**Tamaño de asignación**|**Códigos de desenredado**|  
|8 a 128 bytes|UWOP_ALLOC_SMALL|  
|136 a 512K - 8 bytes|UWOP_ALLOC_LARGE, información de la operación = 0|  
|512K a 4G - 8 bytes|UWOP_ALLOC_LARGE, información de la operación = 1|  
  
 UWOP_SET_FPREG (3) 1 nodo  
  
 Establecer el registro de puntero de marco configurando el registro con cierto desplazamiento del RSP actual. El desplazamiento es igual que el campo (escalado) desplazamiento Frame Register de UNWIND_INFO * 16, permitiendo desplazamientos de 0 a 240. El uso de un desplazamiento permite establecer un puntero de marco que apunta a la mitad de la asignación fija de la pila, lo que favorece densidad del código al permitir más accesos para usar formatos de instrucción cortos. Tenga en cuenta que el campo de información de la operación está reservado y no debe usarse.  
  
 UWOP_SAVE_NONVOL (4) 2 nodos  
  
 Guardar un registro entero no variable en la pila utilizando MOV en lugar de una INSERCIÓN. Esto se utiliza principalmente para reducción hasta ajustar, donde se guarda un registro no volátil a la pila en una posición que se asignó previamente. La información de la operación es el número del registro. El desplazamiento de la pila de escala por 8 se registra en la siguiente desenredo ranura de código de operación, como se describe en la nota anterior.  
  
 UWOP_SAVE_NONVOL_FAR (5) 3 nodos  
  
 Guardar un registro entero no variable en la pila con un desplazamiento largo, utilizando MOV en lugar de una INSERCIÓN. Esto se utiliza principalmente para reducción hasta ajustar, donde se guarda un registro no volátil a la pila en una posición que se asignó previamente. La información de la operación es el número del registro. El desplazamiento de la pila sin ajuste de escala se registra en las próximas dos desenredo ranuras de código de operación, como se describe en la nota anterior.  
  
 UWOP_SAVE_XMM128 (8) 2 nodos  
  
 Guarde todos los 128 bits de un registro XMM no variable en la pila. La información de la operación es el número del registro. El desplazamiento de la pila de escala por 16 se registra en la ranura siguiente.  
  
 UWOP_SAVE_XMM128_FAR (9) 3 nodos  
  
 Guarde todos los 128 bits de un registro XMM no variable en la pila con un desplazamiento largo. La información de la operación es el número del registro. El desplazamiento de la pila sin ajuste de escala se registra en las dos siguientes ranuras.  
  
 UWOP_PUSH_MACHFRAME (10) 1 nodo  
  
 Insertar un marco del equipo.  Esto se usa para registrar el efecto de una interrupción de hardware o de una excepción. Hay dos formas. Si la información de la operación es igual a 0, éste se ha insertado en la pila:  
  
|||  
|-|-|  
|RSP + 32|SS|  
|RSP + 24|RSP anterior|  
|RSP + 16|EFLAGS|  
|RSP + 8|CS|  
|RSP|COPIAR DESDE CD|  
  
 Si la información de la operación es igual a 1, a continuación, en su lugar se ha insertado lo siguiente:  
  
|||  
|-|-|  
|RSP + 40|SS|  
|RSP + 32|RSP anterior|  
|RSP + 24|EFLAGS|  
|RSP + 16|CS|  
|RSP + 8|COPIAR DESDE CD|  
|RSP|Código de error|  
  
 Este código de desenredado aparecerá siempre en un prólogo ficticio, que realmente nunca se ejecuta, pero en su lugar aparece antes del punto de entrada real de una rutina de interrupción y existe únicamente para proporcionar un lugar para simular la inserción de un marco del equipo. UWOP_PUSH_MACHFRAME registra esa simulación, lo que indica que el equipo ha hecho conceptualmente lo siguiente:  
  
 Extraer la dirección de devolución de RIP desde la parte superior de la pila en *Temp*  
  
 Insertar SS  
  
 Insertar RSP anterior  
  
 Insertar EFLAGS  
  
 Insertar CS  
  
 Insertar *Temp*  
  
 Insertar código de Error (si la información de la operación es igual a 1)  
  
 La operación UWOP_PUSH_MACHFRAME simulada reduce RSP por 40 (información de la operación es igual a 0) o 48 (la información de la operación es igual a 1).  
  
 **Información de la operación**  
 El significado de estos 4 bits depende del código de operación. Para codificar un registro de uso general (entero), se utiliza la asignación siguiente:  
  
|||  
|-|-|  
|0|RAX|  
|1|RCX|  
|2|RDX|  
|3|RBX|  
|4|RSP|  
|5|RBP|  
|6|RSI|  
|7|RDI|  
|8 y 15|R8 a R15|  
  
## <a name="see-also"></a>Vea también  
 [Datos de desenredo para la compatibilidad con el control de excepciones y el depurador](../build/unwind-data-for-exception-handling-debugger-support.md)