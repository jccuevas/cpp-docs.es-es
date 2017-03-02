---
title: Compilador advertencia (niveles 1 y 3) C4793 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4793
dev_langs:
- C++
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
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: a217d2074affa1598aef93882fb299c6fcdef5a6
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-and-3-c4793"></a>Advertencia del compilador (niveles 1 y 3) C4793
'función': función está compilada como código nativo: 'motivo'  
  
 El compilador no puede compilar *función* en código administrado, aunque el [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) se especifica la opción del compilador. En su lugar, el compilador emite la advertencia C4793 y un mensaje explicativo a continuación y, a continuación, compila *función* en código nativo. El mensaje de continuación contiene la *razón* texto que explica por qué *función* no se puede compilar para `MSIL`.  
  
 Se trata de una advertencia de nivel 1 cuando se especifica la `/clr:pure` opción del compilador.  El **/CLR: pure** opción del compilador está desusada en Visual Studio 2015.  
  
 En la tabla siguiente se enumera todos los mensajes de continuación posibles.  
  
|Mensaje motivo|Comentarios|  
|--------------------|-------------|  
|Tipos de datos alineados no se admiten en código administrado|El CLR debe poder asignar datos según sea necesario, que podría no ser posible si los datos están alineados con declaraciones como [__m128](../../cpp/m128.md) o [alinear](../../cpp/align-cpp.md).|  
|Las funciones que usan '__ImageBase' no se admiten en código administrado|`__ImageBase`es un símbolo de vinculador especial que se utiliza normalmente sólo por el código nativo de bajo nivel para cargar un archivo DLL.|  
|varargs no son compatibles con el ' / clr' opción del compilador|Funciones nativas no pueden llamar a las funciones administradas que tienen [listas de argumentos variables](../../cpp/functions-with-variable-argument-lists-cpp.md) (varargs) porque las funciones tienen requisitos de diseño de pila diferente. Sin embargo, si especifica el `/clr:pure` opción del compilador, porque el ensamblado puede contener sólo las funciones administradas se admiten las listas de argumentos variables. Para obtener más información, consulte [código puro y comprobable (C++ / CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).|  
|El CLR de 64 bits no admite datos declarados con el modificador __ptr32|Un puntero debe ser el mismo tamaño que un puntero nativo en la plataforma actual. Para obtener más información, consulte [__ptr32, \__ptr64](../../cpp/ptr32-ptr64.md).|  
|El CLR de 32 bits no admite datos declarados con el modificador __ptr64|Un puntero debe ser el mismo tamaño que un puntero nativo en la plataforma actual. Para obtener más información, consulte [__ptr32, \__ptr64](../../cpp/ptr32-ptr64.md).|  
|No se admiten uno o más elementos intrínsecos en código administrado|El nombre de la función intrínseca no está disponible en el momento en que se emite el mensaje. Sin embargo, una función intrínseca que origina este mensaje suele representa una instrucción máquina de bajo nivel.|  
|Ensamblado nativo insertado ('__asm') no se admite en código administrado|[Código de ensamblado alineado](../../assembler/inline/asm.md) pueden contener código nativo arbitrario, que no se pueden administrar.|  
|Un thunk de función virtual distinta de __clrcall debe compilarse como nativa|No[__clrcall](../../cpp/clrcall.md) código thunk de función virtual debe utilizar una dirección no administrada.|  
|Una función que utilice '_setjmp' debe compilarse como nativa|El CLR debe ser capaz de controlar la ejecución del programa. Sin embargo, el [setjmp](../../cpp/using-setjmp-longjmp.md) función omite la ejecución de programa normales por guardar y restaurar información de bajo nivel, como registros y el estado de ejecución.|  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4793.  
  
```  
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
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4793.  
  
```  
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
