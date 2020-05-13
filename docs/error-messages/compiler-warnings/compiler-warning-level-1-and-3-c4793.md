---
title: Advertencia del compilador (niveles 1 y 3) C4793
ms.date: 11/04/2016
f1_keywords:
- C4793
helpviewer_keywords:
- C6634
- C6635
- C6640
- C6630
- C6639
- C6636
- C6638
- C6631
- C6637
- C4793
ms.assetid: 819ada53-1d9c-49b8-a629-baf8c12314e6
ms.openlocfilehash: de6f514d8e3ad8e7715c9cd13a695e3398fffc8d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164812"
---
# <a name="compiler-warning-level-1-and-3-c4793"></a>Advertencia del compilador (niveles 1 y 3) C4793

> '*función*': la función se compila como código nativo: '*Reason*'

## <a name="remarks"></a>Observaciones

El compilador no puede compilar la *función* en código administrado, aunque se haya especificado la opción del compilador [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) . En su lugar, el compilador emite la advertencia C4793 y un mensaje de continuación explicativo y, a continuación, compila la *función* en código nativo. El mensaje de continuación contiene el texto de la *razón* que explica por qué la *función* no se puede compilar en `MSIL`.

Se trata de una advertencia de nivel 1 al especificar la opción del compilador **/clr: Pure** .  La opción del compilador **/clr: Pure** ha quedado en desuso en visual Studio 2015 y no se admite en visual Studio 2017.

En la tabla siguiente se enumeran todos los mensajes de continuación posibles.

|Mensaje de motivo|Observaciones|
|--------------------|-------------|
|Los tipos de datos alineados no se admiten en código administrado|CLR debe ser capaz de asignar datos según sea necesario, lo que podría no ser posible si los datos se alinean con declaraciones como [__m128](../../cpp/m128.md) o [align](../../cpp/align-cpp.md).|
|Las funciones que usan ' __ImageBase ' no se admiten en código administrado|`__ImageBase` es un símbolo del enlazador especial que normalmente solo usa código nativo de bajo nivel para cargar un archivo DLL.|
|varargs no es compatible con la opción del compilador '/CLR '|Las funciones nativas no pueden llamar a funciones administradas que tengan [listas de argumentos variables](../../cpp/functions-with-variable-argument-lists-cpp.md) (varargs) porque las funciones tienen requisitos de diseño de pila diferentes. Sin embargo, si se especifica la opción del compilador **/clr: Pure** , se admiten las listas de argumentos variables porque el ensamblado solo puede contener funciones administradas. Para obtener más información, consulte [código puro y comprobableC++(/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).|
|El CLR de 64 bits no admite los datos declarados con el modificador __ptr32|Un puntero debe tener el mismo tamaño que un puntero nativo en la plataforma actual. Para obtener más información, vea [__ptr32, \__ptr64](../../cpp/ptr32-ptr64.md).|
|El CLR de 32 bits no admite los datos declarados con el modificador __ptr64|Un puntero debe tener el mismo tamaño que un puntero nativo en la plataforma actual. Para obtener más información, vea [__ptr32, \__ptr64](../../cpp/ptr32-ptr64.md).|
|Uno o más intrínsecos no se admiten en código administrado|El nombre del intrínseco no está disponible en el momento en que se emite el mensaje. Sin embargo, un intrínseco que provoca este mensaje suele representar una instrucción máquina de bajo nivel.|
|El ensamblado nativo alineado (' __asm ') no se admite en código administrado|El [código de ensamblado alineado](../../assembler/inline/asm.md) puede contener código nativo arbitrario, que no se puede administrar.|
|Un código thunk de función virtual no __clrcall se debe compilar como nativo|Un código thunk de función virtual no[__clrcall](../../cpp/clrcall.md) debe usar una dirección no administrada.|
|Una función que usa ' _setjmp ' debe compilarse como nativa|CLR debe ser capaz de controlar la ejecución del programa. Sin embargo, la función [setjmp](../../cpp/using-setjmp-longjmp.md) omite la ejecución de programas normal guardando y restaurando información de bajo nivel, como registros y estado de ejecución.|

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4793.

```cpp
// C4793.cpp
// compile with: /c /clr /W3
// processor: x86
int asmfunc(void) {   // C4793, compiled as unmanaged, native code
   __asm {
      mov eax, 0
   }
}
```

```Output
warning C4793: 'asmfunc' : function is compiled as native code:
        Inline native assembly ('__asm') is not supported in managed code
```

En el ejemplo siguiente se genera C4793.

```cpp
// C4793_b.cpp
// compile with: /c /clr /W3
#include <setjmp.h>
jmp_buf test_buf;

void f() {
   setjmp(test_buf);   // C4793 warning
}
```

```Output
warning C4793: 'f' : function is compiled as native code:
        A function using '_setjmp' must be compiled as native
```
