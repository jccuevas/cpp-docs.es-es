---
title: Prólogo y epílogo
ms.date: 11/04/2016
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
ms.openlocfilehash: 2b54737edd46a5e108a211ee032889885be2b1da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543122"
---
# <a name="prolog-and-epilog"></a>Prólogo y epílogo

Cada función que asigna espacio de pila, llama a otras funciones, guarda los registros no volátiles o usa el control de excepciones debe tener un prólogo cuyos límites de direcciones se describen en los datos de desenredo asociados con la entrada de la tabla de función correspondiente (vea [(X64) de control de excepciones](../build/exception-handling-x64.md)). El prólogo guarda registros en sus direcciones particulares si es necesario, inserta los registros no volátiles en la pila de argumento, asigna la parte fija de la pila de objetos temporales y variables locales y, opcionalmente, establece un puntero de marco. Datos de desenredo asociado debe describir la acción del prólogo y debe proporcionar la información necesaria para deshacer el efecto del código de prólogo.

Si la asignación fija en la pila es más de una página (es decir, mayor que 4096 bytes), es posible que la asignación de la pila puede abarcar más de una página de memoria virtual y, por lo tanto, se debe comprobar la asignación antes de que está realmente asignada. Se proporciona una rutina especial que sea accesible desde el prólogo y que no destruye cualquiera de los registros de argumentos para este propósito.

Es el método preferido para guardar los registros no volátiles moverlos en la pila antes de la asignación fija de la pila. Si la asignación fija de la pila se realizaron antes de que se han guardado los registros no volátiles, entonces probablemente sería un desplazamiento de 32 bits necesario para abordar el área de registro guardada (al parecer, inserciones de los registros son tan rápidos como movimientos y deben permanecer así por el futuro inmediato a pesar de la dependencia implícita entre inserciones). Los registros no volátiles se pueden guardar en cualquier orden. Sin embargo, debe ser el primer uso de un registro permanente en el prólogo guardarlo.

El código para un prólogo típico podría ser:

```
mov       [RSP + 8], RCX
push   R15
push   R14
push   R13
sub      RSP, fixed-allocation-size
lea      R13, 128[RSP]
...
```

Este prólogo almacena el registro de argumento RCX en su ubicación inicial, no volátil guarda registra R13-R15, asigna la parte fija del marco de pila y establece un puntero de marco que apunta a 128 bytes en el área de asignación fija. Uso de un desplazamiento permite que más el área de asignación fija solucionarse con desplazamientos de byte único.

Si el tamaño de asignación fija es mayor o igual que una página de memoria, una función auxiliar debe llamarse antes de modificar RSP. Esta aplicación auxiliar, __chkstk, es responsable de sondear el rango de pila se va a asignar, para asegurarse de que la pila se extiende correctamente. En ese caso, el ejemplo anterior del prólogo en su lugar, sería:

```
mov       [RSP + 8], RCX
push   R15
push   R14
push   R13
mov      RAX,  fixed-allocation-size
call   __chkstk
sub      RSP, RAX
lea      R13, 128[RSP]
...
```

La función auxiliar __chkstk no modificará los registros que R10, R11 y los códigos de condición. En concreto, devolverá RAX sin cambios y dejar los registros no volátiles todo y registros de paso de argumentos sin modificar.

El código de epílogo existe en cada salida a una función. Mientras que hay normalmente sólo un prólogo, puede haber muchos epílogos. El código de epílogo recorta la pila a su tamaño de asignación fija (si es necesario), desasigna la asignación fija de la pila, restaura los registros no volátiles extrayendo sus valores guardados de la pila y devuelve.

El código de epílogo debe seguir un conjunto estricto de reglas para el código de desenredado desenredo de manera confiable a través de las excepciones y las interrupciones. Esto reduce la cantidad de desenredar datos necesarios, ya que no se necesita ningún dato adicional para describir cada epílogo. En su lugar, el código de desenredado puede determinar que se está ejecutando un epílogo examinando hacia delante a través de una secuencia de código para identificar un epílogo.

Si no se usa ningún puntero de marco en la función y, a continuación, el epílogo primero debe desasignar la parte fija de la pila, se extraen los registros no volátiles y el control se devuelve a la función que realiza la llamada. Por ejemplo,

```
add      RSP, fixed-allocation-size
pop      R13
pop      R14
pop      R15
ret
```

Si se usa un puntero de marco en la función, se debe recortar la pila para su asignación fija antes de la ejecución del epílogo. Esto es técnicamente no forma parte del epílogo. Por ejemplo, el epílogo siguiente podría usarse para deshacer el prólogo utilizado previamente:

```
lea      RSP, -128[R13]
; epilogue proper starts here
add      RSP, fixed-allocation-size
pop      R13
pop      R14
pop      R15
ret
```

En la práctica, cuando se usa un puntero de marco, no hay ninguna razón para ajustar RSP en dos pasos, por lo que el epílogo siguiente podría usarse en su lugar:

```
lea      RSP, fixed-allocation-size - 128[R13]
pop      R13
pop      R14
pop      R15
ret
```

Estos son los formularios sólo legales para un epílogo. Debe constar de uno de ellos un `add RSP,constant` o `lea RSP,constant[FPReg]`, seguido de una serie de cero o más puntos de presencia de 8 bytes y un valor devuelto o una jmp. (Solo un subconjunto de instrucciones jmp están permitidas en el epílogo. Estos son exclusivamente de la clase de instrucciones jmp con referencias de memoria ModRM donde ModRM mod campo value 00. Se prohíbe el uso de instrucciones jmp en el epílogo con valor de campo de módulo ModRM 01 o 10. Consulte la tabla A-15 en volumen de Manual 3 de AMD 64 x86 arquitectura del programador: de propósito General y las instrucciones del sistema, para obtener más información sobre las referencias de ModRM permitidas.). No puede aparecer ningún otro código. En concreto, se puede programar nada dentro de un epílogo, incluida la carga de un valor devuelto.

Tenga en cuenta que, cuando no se usa un puntero de marco, se debe utilizar el epílogo `add RSP,constant` para desasignar la parte fija de la pila. No puede usar `lea RSP,constant[RSP]` en su lugar. Esta restricción existe por lo que el código de desenredado tiene menos modelos para reconocer al buscar epílogos.

Las siguientes reglas permite que el código de desenredo para determinar que actualmente se está ejecutando un epílogo y simular la ejecución del resto del epílogo para permitir volver a crear el contexto de la función de llamada.

## <a name="see-also"></a>Vea también

[Convenciones de software x64](../build/x64-software-conventions.md)