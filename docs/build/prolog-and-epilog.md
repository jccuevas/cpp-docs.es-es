---
title: "Pr&#243;logo y ep&#237;logo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Pr&#243;logo y ep&#237;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada función que asigna espacio en la pila, llama a otras funciones, guarda registros no variables o utiliza control de excepciones debe tener un prólogo cuyos límites de direcciones se describan en los datos de desenredo asociados a la respectiva entrada de tabla de la función \(vea [Control de excepciones \(x64\)](../build/exception-handling-x64.md)\).  El prólogo guarda registros de argumentos en sus direcciones iniciales \(si es necesario\), introduce registros no variables en la pila, asigna la parte fija de la pila para valores locales y temporales y, opcionalmente, establece un puntero de marco.  Los datos de desenredo asociados deben describir la acción del prólogo y deben proporcionar la información necesaria para deshacer el efecto del código de prólogo.  
  
 Si la asignación fija en la pila ocupa más de una página \(es decir, es mayor que 4096 bytes\), es posible que la asignación de la pila pueda abarcar más de una página de memoria virtual y, por tanto, se debe comprobar antes de efectuarse realmente.  Con este propósito, se proporciona una rutina especial que es invocable desde el prólogo y que no destruye ninguno de los registros de argumentos.  
  
 El método preferido para guardar los registros no variables es moverlos a la pila antes de la asignación fija de la pila.  Si la asignación fija de la pila se efectuase antes de guardar los registros no variables, lo más probable es que se requiriese un desplazamiento de 32 bits para direccionar el área de registro guardada \(al parecer, las entradas de registros son igual de rápidas que los movimientos y deben mantenerse así para el futuro previsible en lugar de la dependencia implícita entre entradas\).  Los registros no variables se pueden guardar en cualquier orden.  Sin embargo, el primer uso de un registro no variable en el prólogo debe ser guardarlo.  
  
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
  
 Este prólogo almacena el registro de argumento RCX en su ubicación inicial, guarda registros no variables R13\-R15, asigna la parte fija del marco de pila y establece un puntero de marca que indica 128 bytes en el área de asignación fija.  El uso de un desplazamiento permite direccionar un área mayor que la de asignación fija con desplazamientos de un byte.  
  
 Si el tamaño de la asignación fija es mayor o igual que una página de memoria, se debe llamar a una función auxiliar antes de modificar RSP.  Esta función auxiliar, \_\_chkstk, es responsable de analizar el intervalo de la pila que se va a asignar, para garantizar que la pila se extiende correctamente.  En ese caso, el ejemplo de prólogo anterior sería ahora:  
  
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
  
 La función auxiliar \_\_chkstk no modificará ningún registro aparte de R10, R11 y los códigos de condición.  En concreto, devolverá RAX sin modificar y dejará sin modificar todos los registros no variables y los de paso de argumentos.  
  
 El código de epílogo existe en cada salida a una función.  Mientras que normalmente hay sólo un prólogo, puede haber muchos epílogos.  El código de epílogo recorta la pila a su tamaño de asignación fija \(si es necesario\), deshace la asignación fija de la pila, restaura registros no variables extrayendo sus valores guardados de la pila y devuelve el control.  
  
 El código de epílogo debe seguir un conjunto estricto de reglas para que el código de desenredo pueda efectuar desenredos de manera confiable a través de excepciones e interrupciones.  Esto reduce la cantidad de datos de desenredo requerida, porque no se necesitan datos adicionales para describir cada epílogo.  En su lugar, el código de desenredo puede determinar que se está ejecutando un epílogo examinando hacia delante una secuencia de código para identificar un epílogo.  
  
 Si no se utiliza puntero de marco en la función, el epílogo primero debe desasignar la parte fija de la pila, los registros no variables se extraen y se devuelve el control a la función de llamada.  Por ejemplo,  
  
```  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 Si se utiliza un puntero de marco en la función, la pila se debe recortar a su asignación fija antes de ejecutar el epílogo.  Esto técnicamente no forma parte del epílogo.  Por ejemplo, el epílogo siguiente se podría utilizar para deshacer el prólogo utilizado previamente:  
  
```  
lea      RSP, -128[R13]  
; epilogue proper starts here  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 En la práctica, cuando se utiliza un puntero de marco, no existe una buena razón para ajustar RSP en dos pasos, por lo que en realidad se utilizaría el siguiente epílogo:  
  
```  
lea      RSP, fixed-allocation-size – 128[R13]  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 Estos son los únicos formularios legales para un epílogo.  Debe consistir en `add RSP,constant` o `lea RSP,constant[FPReg]`, seguido de una serie de cero o más pops de registros de 8 bytes y un retorno o una instrucción jmp.  \(Sólo se permite un subconjunto de instrucciones jmp en el epílogo.  Son exclusivamente de la clase de instrucciones jmp con referencias de memoria ModRM, donde el valor de campo de módulo ModRM es 00.  El uso de instrucciones jmp en el epílogo con valor de campo de módulo ModRM 01 ó 10 está prohibido.  Vea la tabla A\-15 en el Guía del desarrollador de .NET Framework de la arquitectura AMD x86\-84, en el volumen 3, sobre instrucciones de propósito general y del sistema, para obtener más información sobre las referencias de ModRM admisibles\).  No puede aparecer ningún otro código.  En concreto, no se puede programar nada dentro de un epílogo, ni siquiera la carga de un valor devuelto.  
  
 Tenga en cuenta que, cuando no se utiliza un puntero de marco, el epílogo debe utilizar `add RSP,constant` para desasignar la parte fija de la pila.  No puede utilizar en su lugar `lea RSP,constant[RSP]`.  Esta restricción existe para que el código de desenredo tenga menos modelos para reconocer al buscar epílogos.  
  
 Si se siguen estas reglas, el código de desenredo puede determinar que se está ejecutando un epílogo y simular la ejecución del resto del epílogo para permitir la recreación del contexto de la función de llamada.  
  
## Vea también  
 [Convenciones de software x64](../build/x64-software-conventions.md)