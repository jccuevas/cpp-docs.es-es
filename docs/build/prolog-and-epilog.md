---
title: Prólogo y epílogo x64
ms.date: 12/17/2018
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
ms.openlocfilehash: d0b7444af6e434a09f6af5f5b1c144b46c79ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328431"
---
# <a name="x64-prolog-and-epilog"></a>Prólogo y epílogo x64

Todas las funciones que asignan espacio de pila, llaman a otras funciones, guardan registros no volátiles o usan el control de excepciones deben tener un prólogo cuyos límites de dirección se describen en los datos de desenredado asociados a la entrada de la tabla de funciones correspondiente. Para obtener más información, vea [Control de excepciones x64](../build/exception-handling-x64.md). El prólogo guarda los registros de argumentos en sus direcciones de inicio si es necesario, envía registros no volátiles en la pila, asigna la parte fija de la pila para variables locales y objetos temporales y, opcionalmente, establece un puntero de marco. Los datos de desenredado asociados deben describir la acción del prólogo y proporcionar la información necesaria para deshacer el efecto del código de prólogo.

Si la asignación fija en la pila es más de una página (es decir, mayor de 4096 bytes), es posible que la asignación de la pila pueda abarcar más de una página de memoria virtual y, por tanto, se debe comprobar la asignación antes de asignarla. Para este fin, se proporciona una rutina especial a la que se puede llamar desde el prólogo y que no destruye ninguno de los registros de argumento.

El método preferido para guardar registros no volátiles consiste en moverlos a la pila antes de la asignación de pila fija. Si se realiza la asignación de pila fija antes de que se guarden los registros no volátiles, lo más probable es que se requiera un desplazamiento de 32 bits para abordar el área de registro guardada. (Supuestamente, las inserciones de registros son tan rápidas como los movimientos y deben conservarse para el futuro inmediato a pesar de la dependencia implícita entre inserciones). Los registros no volátiles se pueden guardar en cualquier orden. Pero el primer uso de un registro no volátil en el prólogo debe ser para guardarlo.

## <a name="prolog-code"></a>Código de prólogo

El código de un prólogo típico podría ser el siguiente:

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    sub    RSP, fixed-allocation-size
    lea    R13, 128[RSP]
    ...
```

En este prólogo se almacena el registro de argumento RCX en su ubicación de inicio, se guardan los registros no volátiles R13-R15, se asigna la parte fija del marco de pila y se establece un puntero de marco que apunta a 128 bytes en el área de asignación fija. El uso de un desplazamiento permite acceder a una mayor parte del área de asignación fija con desplazamientos de un byte.

Si el tamaño de asignación fija es mayor o igual que una página de memoria, se debe llamar a una función auxiliar antes de modificar RSP. Este asistente, `__chkstk`, sondea el intervalo de pila que se va a asignar para asegurarse de que la pila se extienda de la forma correcta. En ese caso, el ejemplo de prólogo anterior ahora sería el siguiente:

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

El asistente `__chkstk` no modificará ningún registro que no sea R10, R11 y los códigos de condición. En concreto, devolverá RAX sin modificar y dejará sin cambios todos los registros no volátiles y los registros de paso de argumentos.

## <a name="epilog-code"></a>Código de epílogo

El código de epílogo existe en cada salida a una función. Mientras que normalmente solo hay un prólogo, puede haber muchos epílogos. El código de epílogo recorta la pila a su tamaño de asignación fijo (si es necesario), desasigna la asignación de pila fija, restaura los registros no volátiles mediante la extracción de sus valores guardados de la pila y devuelve un valor.

El código de epílogo debe seguir un conjunto estricto de reglas para que el código de desenredo se desenrede de forma confiable a través de excepciones e interrupciones. Estas reglas reducen la cantidad de datos de desenredo necesarios, ya que no se necesitan datos adicionales para describir cada epílogo. En su lugar, el código de desenredado puede determinar que se está ejecutando un epílogo mediante un examen de un flujo de código para identificar un epílogo.

Si no se usa ningún puntero de marco en la función, el epílogo debe desasignar primero la parte fija de la pila, extraer los registros no volátiles y devolver el control a la función de llamada. Por ejemplo,

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Si en la función se usa un puntero de marco, la pila se debe recortar a su asignación fija antes de la ejecución del epílogo. Técnicamente, esta acción no forma parte del epílogo. Por ejemplo, se podría utilizar el epílogo siguiente para deshacer el prólogo que se ha usado antes:

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

En la práctica, cuando se usa un puntero de marco, no es necesario ajustar RSP en dos pasos, por lo que en su lugar se usaría el siguiente epílogo:

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

Estos son los únicos formatos válidos para un epílogo. Debe constar de una instancia de `add RSP,constant` o `lea RSP,constant[FPReg]`, seguida de una serie de cero o más extracciones de registro de 8 bytes y una instancia de `return` o `jmp`. (Solo se permite un subconjunto de instrucciones `jmp` en el epílogo. El subconjunto es exclusivamente la clase de instrucciones `jmp` con referencias de memoria ModRM, donde el valor del campo mod de ModRM es 00. Se prohíbe el uso de instrucciones `jmp` en el epílogo con el valor de campo mod de ModRM 01 o 10. Vea la Tabla A-15 del Manual del programador de arquitectura x86-64 de AMD volumen 3: Instrucciones de uso general y del sistema, para obtener más información sobre las referencias de ModRM permitidas). No puede aparecer ningún otro código. En concreto, no se puede programar nada en un epílogo, incluida la carga de un valor devuelto.

Cuando no se usa un puntero de marco, el epílogo debe utilizar `add RSP,constant` para desasignar la parte fija de la pila. No puede usar `lea RSP,constant[RSP]` en su lugar. Esta restricción existe para que el código de desenredado tenga menos patrones que reconocer al buscar los epílogos.

Si se siguen estas reglas, el código de desenredado puede determinar que un epílogo se está ejecutando actualmente y simular la ejecución del resto del epílogo para permitir volver a crear el contexto de la función de llamada.

## <a name="see-also"></a>Vea también

[Convenciones de software x64](x64-software-conventions.md)
