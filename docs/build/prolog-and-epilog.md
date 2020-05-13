---
title: Prólogo y epílogo x64
ms.date: 12/17/2018
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
ms.openlocfilehash: d0b7444af6e434a09f6af5f5b1c144b46c79ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328431"
---
# <a name="x64-prolog-and-epilog"></a>Prólogo y epílogo x64

Cada función que asigna espacio de pila, llama a otras funciones, guarda registros no volátiles o utiliza el control de excepciones debe tener un prólogo cuyos límites de dirección se describen en los datos de desenredado asociados con la entrada de tabla de funciones respectiva. Para obtener más información, consulte Control de [excepciones x64](../build/exception-handling-x64.md). El prólogo guarda los registros de argumentos en sus direcciones de inicio si es necesario, inserta registros no volátiles en la pila, asigna la parte fija de la pila para locales y temporarios y, opcionalmente, establece un puntero de marco. Los datos de desenredado asociados deben describir la acción del prólogo y deben proporcionar la información necesaria para deshacer el efecto del código de prólogo.

Si la asignación fija en la pila es más de una página (es decir, superior a 4096 bytes), es posible que la asignación de pila pueda abarcar más de una página de memoria virtual y, por lo tanto, la asignación debe comprobarse antes de asignarla. Para ello se proporciona una rutina especial que se puede llamar desde el prólogo y que no destruye ninguno de los registros de argumentos.

El método preferido para guardar registros no volátiles es moverlos a la pila antes de la asignación de pila fija. Si la asignación de pila fija se realiza antes de que se guarden los registros no volátiles, lo más probable es que se requiera un desplazamiento de 32 bits para abordar el área de registro guardada. (Según se informa, los impulsos de los registros son tan rápidos como los movimientos y deben seguir sin hacerlo en el futuro previsible a pesar de la dependencia implícita entre los impulsos.) Los registros no volátiles se pueden guardar en cualquier orden. Sin embargo, el primer uso de un registro no volátil en el prólogo debe ser guardarlo.

## <a name="prolog-code"></a>Código de prolog

El código de un prólogo típico podría ser:

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    sub    RSP, fixed-allocation-size
    lea    R13, 128[RSP]
    ...
```

Este prólogo almacena el registro de argumentos RCX en su ubicación de inicio, guarda los registros no volátiles R13-R15, asigna la parte fija del marco de pila y establece un puntero de trama que apunta 128 bytes en el área de asignación fija. El uso de un desplazamiento permite abordar más del área de asignación fija con desplazamientos de un byte.

Si el tamaño de asignación fijo es mayor o igual que una página de memoria, se debe llamar a una función auxiliar antes de modificar RSP. Este ayudante, `__chkstk`, sondea el intervalo de pila que se va a asignar para asegurarse de que la pila se extiende correctamente. En ese caso, el ejemplo de prólogo anterior sería en su lugar:

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    mov    RAX,  fixed-allocation-size
    call   __chkstk
    sub    RSP, RAX
    lea    R13, 128[RSP]
    ...
```

La `__chkstk` aplicación auxiliar no modificará ningún registro que no sea R10, R11 y los códigos de condición. En particular, devolverá RAX sin cambios y dejará sin modificar todos los registros no volátiles y los registros que pasan argumentos.

## <a name="epilog-code"></a>Código de epilog

El código Epilog existe en cada salida a una función. Mientras que normalmente sólo hay un prólogo, puede haber muchos epíslos. El código Epilog recorta la pila a su tamaño de asignación fijo (si es necesario), desasigna la asignación de pila fija, restaura los registros no volátiles haciendo estallar sus valores guardados de la pila y devuelve.

El código de epílogo debe seguir un conjunto estricto de reglas para que el código de desenredado se desenrede de forma fiable mediante excepciones e interrupciones. Estas reglas reducen la cantidad de datos de desenredado necesarios, ya que no se necesitan datos adicionales para describir cada epílogo. En su lugar, el código de desenredado puede determinar que se está ejecutando un epílogo examinando hacia delante a través de una secuencia de código para identificar un epílogo.

Si no se utiliza ningún puntero de marco en la función, el epílogo debe desasignar primero la parte fija de la pila, se extraen los registros no volátiles y se devuelve el control a la función de llamada. Por ejemplo,

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Si se utiliza un puntero de marco en la función, la pila debe recortarse a su asignación fija antes de la ejecución del epílogo. Esta acción técnicamente no forma parte del epílogo. Por ejemplo, el siguiente epílogo podría utilizarse para deshacer el prólogo utilizado anteriormente:

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

En la práctica, cuando se utiliza un puntero de marco, no hay una buena razón para ajustar RSP en dos pasos, por lo que se utilizaría el siguiente epílogo en su lugar:

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

Estas formas son las únicas legales para un epiólogo. Debe consistir en `add RSP,constant` `lea RSP,constant[FPReg]`una o , seguida de una serie de cero `return` o `jmp`más pops de registro de 8 bytes y un archivo . (Solo se `jmp` permite un subconjunto de instrucciones en el epílogo. El subconjunto es exclusivamente `jmp` la clase de instrucciones con referencias de memoria ModRM donde el valor del campo mod mod de ModRM es 00. Está prohibido `jmp` el uso de instrucciones en el epílogo con el valor de campo ModRM mod 01 o 10. Consulte la Tabla A-15 en el Manual del Programador de Arquitectura AMD x86-64 Volumen 3: Uso general e Instrucciones del sistema, para obtener más información sobre las referencias ModRM permitidas.) No puede aparecer ningún otro código. En particular, no se puede programar nada dentro de un epílogo, incluida la carga de un valor devuelto.

Cuando no se utiliza un puntero de `add RSP,constant` marco, el epílogo debe utilizarse para desasignar la parte fija de la pila. No puede `lea RSP,constant[RSP]` usar en su lugar. Esta restricción existe para que el código de desenredado tenga menos patrones que reconocer al buscar epíslos.

Seguir estas reglas permite que el código de desenredado determine que se está ejecutando un epílogo actualmente y para simular la ejecución del resto del epílogo para permitir volver a crear el contexto de la función de llamada.

## <a name="see-also"></a>Consulte también

[x64 Convenciones de software](x64-software-conventions.md)
