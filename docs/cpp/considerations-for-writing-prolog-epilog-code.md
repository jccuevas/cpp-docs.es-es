---
title: Consideraciones para escribir código de prólogo-epílogo
ms.date: 11/04/2016
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
ms.openlocfilehash: a598ddbdd1b5f91c97e32905202e264b444c05d0
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988704"
---
# <a name="considerations-for-writing-prologepilog-code"></a>Consideraciones para escribir código de prólogo/epílogo

**Específicos de Microsoft**

Antes de escribir sus propias secuencias de código de prólogo y epílogo, es importante comprender cómo se diseña el marco de pila. También es útil saber cómo usar el símbolo de `__LOCAL_SIZE`.

##  <a name="_pluslang_c.2b2b_.stack_frame_layout"></a>Diseño del marco de pila

En este ejemplo se muestra el código de prólogo estándar que puede aparecer en una función de 32 bits:

```
push        ebp                ; Save ebp
mov         ebp, esp           ; Set stack frame pointer
sub         esp, localbytes    ; Allocate space for locals
push        <registers>        ; Save registers
```

La variable `localbytes` representa el número de bytes necesarios en la pila para las variables locales y la variable `<registers>` es un marcador de posición que representa la lista de registros que se guarden en la pila. Después de insertar los registros, puede colocar cualquier otro dato adecuado en la pila. A continuación, se muestra el código de epílogo correspondiente:

```
pop         <registers>   ; Restore registers
mov         esp, ebp      ; Restore stack pointer
pop         ebp           ; Restore ebp
ret                       ; Return from function
```

La pila siempre va de mayor a menor (de las direcciones de memoria superiores a las inferiores). El puntero base (`ebp`) señala al valor insertado de `ebp`. El área de valores locales comienza en `ebp-4`. Para tener acceso a las variables locales, calcule un desplazamiento de `ebp` restando el valor apropiado a `ebp`.

##  <a name="_pluslang___local_size"></a>__LOCAL_SIZE

El compilador proporciona un símbolo, `__LOCAL_SIZE`, para su uso en el bloque de ensamblador alineado del código de prólogo de la función. Este símbolo se utiliza para asignar espacio para variables locales del marco de pila en código de prólogo personalizado.

El compilador determina el valor de `__LOCAL_SIZE`. Su valor es el número total de bytes de todas las variables locales definidas por el usuario y las variables temporales generadas por el compilador. `__LOCAL_SIZE` solo se puede usar como operando inmediato; no se puede usar en una expresión. No debe cambiar o volver a definir el valor de este símbolo. Por ejemplo:

```
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov        eax, [ebp - __LOCAL_SIZE]   ;Error
```

En el ejemplo siguiente de una función Naked que contiene secuencias personalizadas de prólogo y epílogo se usa el símbolo de `__LOCAL_SIZE` en la secuencia de prólogo:

```cpp
// the__local_size_symbol.cpp
// processor: x86
__declspec ( naked ) int main() {
   int i;
   int j;

   __asm {      /* prolog */
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */
   __asm {   /* epilog */
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Llamadas de función naked](../cpp/naked-function-calls.md)
