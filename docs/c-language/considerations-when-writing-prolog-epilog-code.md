---
title: Consideraciones para escribir código de prólogo y epílogo
ms.date: 11/04/2016
helpviewer_keywords:
- layouts, stack frame
- stack frame layout
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: 3b8addec-e809-48e4-b1d0-5bad133bd4b8
ms.openlocfilehash: e7bfeccf41b9e4dace49e9ab209a94598c492b41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515536"
---
# <a name="considerations-when-writing-prologepilog-code"></a>Consideraciones para escribir código de prólogo y epílogo

**Específicos de Microsoft**

Antes de escribir sus propias secuencias de código de prólogo y epílogo, es importante que comprenda cómo se diseña el marco de pila. También es útil saber utilizar la constante predefinida **__LOCAL_SIZE**.

##  <a name="_clang_c_stack_frame_layout"></a> Diseño del marco de pila de C

En este ejemplo se muestra el código de prólogo estándar que puede aparecer en una función de 32 bits:

```
push     ebp                 ; Save ebp
mov      ebp, esp            ; Set stack frame pointer
sub      esp, localbytes     ; Allocate space for locals
push     <registers>         ; Save registers
```

La variable `localbytes` representa el número de bytes necesarios en la pila para las variables locales y la variable `registers` es un marcador de posición que representa la lista de registros que se guarden en la pila. Después de insertar los registros, puede colocar cualquier otro dato adecuado en la pila. A continuación, se muestra el código de epílogo correspondiente:

```
pop      <registers>         ; Restore registers
mov      esp, ebp            ; Restore stack pointer
pop      ebp                 ; Restore ebp
ret                          ; Return from function
```

La pila siempre va de mayor a menor (de las direcciones de memoria superiores a las inferiores). El puntero base (`ebp`) señala al valor insertado de `ebp`. El área de variables locales comienza en `ebp-2`. Para tener acceso a las variables locales, calcule un desplazamiento de `ebp` restando el valor apropiado a `ebp`.

##  <a name="_clang_the___local_size_constant"></a> La constante __LOCAL_SIZE

El compilador proporciona una constante, **__LOCAL_SIZE**, para su uso en el bloque de ensamblador alineado del código de prólogo de la función. Esta constante se utiliza para asignar espacio para las variables locales del marco de pila en código de prólogo personalizado.

El compilador determina el valor de **__LOCAL_SIZE**. El valor es el número total de bytes de todas las variables locales definidas por el usuario y las variables temporales generadas por el compilador. **__LOCAL_SIZE** se puede utilizar como operando inmediato; no se puede utilizar en una expresión. No debe cambiar o volver a definir el valor de esta constante. Por ejemplo:

```
mov      eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov      eax, [ebp - __LOCAL_SIZE]   ;Error
```

En el ejemplo siguiente de una función naked que contiene secuencias personalizadas de prólogo y de epílogo se utiliza **__LOCAL_SIZE** en la secuencia de prólogo:

```
__declspec ( naked ) func()
{
   int i;
   int j;

   __asm      /* prolog */
      {
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */

   __asm      /* epilog */
      {
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Funciones naked](../c-language/naked-functions.md)