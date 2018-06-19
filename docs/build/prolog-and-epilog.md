---
title: Prólogo y epílogo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2939293fe5fbdfd07cb12470790de5b064489d7f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372014"
---
# <a name="prolog-and-epilog"></a>Prólogo y epílogo
Cada función que asigna espacio de pila, llama a otras funciones, guarda los registros no volátiles o usa el control de excepciones debe tener un prólogo cuyos límites de direcciones se describen en los datos de desenredo asociados a la entrada de tabla de la función respectiva (vea [(X64) el control de excepciones](../build/exception-handling-x64.md)). El prólogo guarda argumento registros en sus direcciones particulares si es necesario, inserta los registros no volátiles en la pila, asigna la parte fija de la pila para los objetos temporales y variables locales y, opcionalmente, establece un puntero de marco. Datos de desenredo asociado debe describir la acción del prólogo y debe proporcionar la información necesaria para deshacer el efecto del código de prólogo.  
  
 Si la asignación fija en la pila es más de una página (es decir, mayor que 4096 bytes), es posible que la asignación de pila podría abarcar más de una página de memoria virtual y, por lo tanto, debe comprobarse la asignación antes de que realmente está asignada. Para ello, se proporciona una rutina especial a la que se pueda llamar desde el prólogo y que no destruye ninguno de los registros de argumentos.  
  
 Es el método preferido para guardar los registros no volátiles moverlos en la pila antes de la asignación fija de la pila. Si la asignación fija de la pila se realizaron antes de que se han guardado los registros no volátiles, probablemente sería un desplazamiento de 32 bits necesario para abordar el área de registro guardada (al parecer, inserciones de registros son tan rápidos como movimientos y deben mantenerse así para el futuro inmediato a pesar de la dependencia implícita entre inserciones). Los registros no volátiles se pueden guardar en cualquier orden. Sin embargo, debe ser el primer uso de un registro no volátil en el prólogo de guardarlo.  
  
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
  
 Este prólogo almacena el registro de argumento RCX en su ubicación inicial, no volátil guarda registra R13-R15, asigna la parte fija del marco de pila y establece un puntero de marca que indica 128 bytes en el área de asignación fija. El uso de un desplazamiento permite más el área de asignación fija solucionarse con desplazamientos de un byte.  
  
 Si el tamaño de asignación fija es mayor o igual que una página de memoria, una función auxiliar debe llamarse antes de modificar RSP. Esta función auxiliar, __chkstk, es responsable de sondeo del intervalo de pila se va a asignar, para asegurarse de que la pila se ha ampliado correctamente. En ese caso, el ejemplo de prólogo anterior en lugar de ello sería:  
  
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
  
 La función auxiliar __chkstk no modificará los registros que R10, R11 y los códigos de condición. En concreto, se devolverá RAX sin modificar y dejar los registros no volátiles todo y registros de pasar argumentos sin modificar.  
  
 El código de epílogo existe en cada salida a una función. Mientras que hay normalmente sólo un prólogo, puede haber muchos epílogos. El código de epílogo recorta la pila a su tamaño de asignación fija (si es necesario), cancela la asignación de la asignación fija de la pila, restaura los registros no volátiles por retirar sus valores guardados de la pila y devuelve.  
  
 El código de epílogo debe seguir un conjunto estricto de reglas para el código de desenredado confiable desenredado a través de excepciones e interrupciones. Esto reduce la cantidad de datos necesarios, de desenredado porque ningún dato adicional es necesaria para describir cada epílogo. En su lugar, el código de desenredo puede determinar que se está ejecutando un epílogo examinando hacia delante a través de una secuencia de código para identificar un epílogo.  
  
 Si se utiliza ningún puntero de marco en la función y, a continuación, el epílogo primero debe desasignar la parte fija de la pila, se extraen los registros no volátiles y control se devuelve a la función que realiza la llamada. Por ejemplo,  
  
```  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 Si se usa un puntero de marco en la función, la pila se debe recortar a su asignación fija antes de la ejecución del epílogo. Esto es técnicamente no forma parte del epílogo. Por ejemplo, el epílogo siguiente podría utilizarse para deshacer el prólogo utilizado previamente:  
  
```  
lea      RSP, -128[R13]  
; epilogue proper starts here  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 En la práctica, cuando se utiliza un puntero de marco, no hay ninguna razón de peso para ajustar RSP en dos pasos, por lo que se utilizaría en su lugar el epílogo siguiente:  
  
```  
lea      RSP, fixed-allocation-size - 128[R13]  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 Estos son los únicos formularios legales para un epílogo. Debe constar de uno de ellos un `add RSP,constant` o `lea RSP,constant[FPReg]`, seguido de una serie de cero o más extracciones de registro de 8 bytes y un retorno o una instrucción jmp. (Solo un subconjunto de instrucciones jmp están permitidas en el epílogo. Se trata únicamente de la clase de instrucciones jmp con referencias de memoria ModRM donde el campo de módulo ModRM valor 00. El uso de instrucciones jmp en el epílogo con valor de campo de módulo ModRM 01 ó 10 está prohibido. Consulte tabla A-15 en Manual volumen 3 AMD 64 x86 arquitectura del programador: de propósito General y las instrucciones del sistema, para obtener más información sobre las referencias de ModRM permitidas.). No puede aparecer ningún otro código. En concreto, se puede programar nada dentro de un epílogo, incluida la carga de un valor devuelto.  
  
 Tenga en cuenta que, cuando no se utiliza un puntero de marco, el epílogo debe utilizar `add RSP,constant` para desasignar la parte fija de la pila. Puede que no use `lea RSP,constant[RSP]` en su lugar. Esta restricción existe para que el código de desenredo tenga menos modelos para reconocer al buscar epílogos.  
  
 Estas reglas permite que el código de desenredo para determinar que actualmente se está ejecutando un epílogo y simular la ejecución del resto del epílogo para permitir volver a crear el contexto de la función de llamada.  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de software x64](../build/x64-software-conventions.md)