---
title: "Advertencia del compilador (niveles 1 y 3) C4793 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4793"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4793"
  - "C6630"
  - "C6631"
  - "C6634"
  - "C6635"
  - "C6636"
  - "C6637"
  - "C6638"
  - "C6639"
  - "C6640"
ms.assetid: 819ada53-1d9c-49b8-a629-baf8c12314e6
caps.latest.revision: 28
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (niveles 1 y 3) C4793
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función': la función está compilada como código nativo: 'razón'  
  
 El compilador no puede compilar *function* en código administrado, aunque se especifica la opción del compilador [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) .  En su lugar, el compilador emite la advertencia C4793 y un mensaje explicativo a continuación y, a continuación compila *function* en código nativo.  El mensaje de continuación contiene el texto de *reason* que explica por qué *function* no se puede compilar en `MSIL`.  
  
 Se trata de una advertencia de nivel 1 cuando se especifica la opción del compilador `/clr:pure`.  
  
 En la siguiente tabla se muestran todos los mensajes que pueden incluirse a continuación del error.  
  
|Mensaje con la razón|Comentarios|  
|--------------------------|-----------------|  
|Los tipos de datos alineados no se admiten en código administrado|CLR debe poder asignar datos en función de las necesidades, lo cual no es posible si los datos están alineados con declaraciones del tipo [\_\_m128](../../cpp/m128.md) o [align](../../cpp/align-cpp.md).|  
|No se admiten funciones que utilizan '\_\_ImageBase' en el código administrado|`__ImageBase` es un símbolo especial del vinculador utilizado únicamente por el código nativo de bajo nivel para cargar una DLL.|  
|La opción del compilador '\/clr' no admite varargs|Las funciones nativas no pueden llamar a funciones administradas que tienen [listas de argumentos variables](../../misc/variable-argument-lists.md) \(varargs\) porque las funciones presentan distintos requisitos de diseño de pila.  No obstante, si especifica la opción del compilador `/clr:pure`, sí que se admiten listas de argumentos variables porque el ensamblado sólo puede contener funciones administradas.  Para obtener más información, vea [Código puro y comprobable](../../dotnet/pure-and-verifiable-code-cpp-cli.md).|  
|El CLR de 64 bits no admite datos declarados con el modificador \_\_ptr32|Un puntero debe tener el mismo tamaño que un puntero nativo en la plataforma actual.  Para obtener más información, vea [\_\_ptr32, \_\_ptr64](../../cpp/ptr32-ptr64.md).|  
|El CLR de 32 bits no admite datos declarados con el modificador \_\_ptr64|Un puntero debe tener el mismo tamaño que un puntero nativo en la plataforma actual.  Para obtener más información, vea [\_\_ptr32, \_\_ptr64](../../cpp/ptr32-ptr64.md).|  
|No se admiten una o varias instrucciones intrínsecas en el código administrado|El nombre de la instrucción intrínseca no está disponible en el momento en que se emite el mensaje.  Sin embargo, una instrucción intrínseca que origina este mensaje suele representar una instrucción máquina de bajo nivel.|  
|No se admite el ensamblado nativo insertado \('\_\_asm'\) en el código administrado|El [código de ensamblado insertado](../../assembler/inline/asm.md) puede incluir código nativo arbitrario, que no puede administrarse.|  
|El código thunk de una función virtual distinta de \_\_clrcall debe compilarse como código nativo|El código thunk de una función virtual distinta de [\_\_clrcall](../../cpp/clrcall.md) debe utilizar una dirección no administrada.|  
|Una función que utilice '\_setjmp' debe compilarse como nativa|El CLR debe ser capaz de controlar la ejecución de programas.  Sin embargo, la función [setjmp](../../cpp/using-setjmp-longjmp.md) omite la ejecución normal de programas ya que guarda y restaura información de bajo nivel, como registros y el estado de ejecución.|  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4793.  
  
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
  
  **advertencia C4793: 'asmfunc': la función está compilada como código nativo:**  
 **No se admite el ensamblado nativo insertado \('\_\_asm'\) en el código administrado**   
## Ejemplo  
 El ejemplo siguiente genera el error C4793.  
  
```  
// C4793_b.cpp  
// compile with: /c /clr /W3  
#include <setjmp.h>  
jmp_buf test_buf;  
  
void f() {  
   setjmp(test_buf);   // C4793 warning  
}  
```  
  
  **advertencia C4793: 'f': la función está compilada como código nativo:**  
 **Una función que utilice '\_setjmp' debe compilarse como nativa**