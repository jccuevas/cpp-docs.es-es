---
title: "safe_cast (Extensiones de componentes de C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "safe_cast"
  - "safe_cast_cpp"
  - "stdcli::language::safe_cast"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "safe_cast (palabra clave) [C++]"
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# safe_cast (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La operación `safe_cast`, si es correcta, devuelve la expresión especificada como el tipo especificado; en caso contrario, produce una `InvalidCastException`.  
  
## Todos los runtimes  
 \(No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes.\)  
  
### Sintaxis  
  
```cpp  
  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### Parámetros  
  
### Comentarios  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 `safe_cast` permite cambiar el tipo de una expresión especificada.  En situaciones donde se espera claramente una variable o parámetro convertible a un tipo determinado, puede usar safe\_cast sin un bloque try\-catch para detectar errores de programación durante el desarrollo.  Para obtener más información, vea [Convertir \(C\+\+\/CX\)](http://msdn.microsoft.com/library/windows/apps/hh755802.aspx).  
  
### Sintaxis  
  
```cpp  
  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### Parámetros  
 *type\-id*  
 Tipo al que se va a convertir *expression*.  Identificador de un tipo de valor o referencia, un tipo de valor o una referencia de seguimiento a una referencia o tipo de valor.  
  
 *expression*  
 Expresión que evalúa a un identificador de un tipo de valor o referencia, un tipo de valor o una referencia de seguimiento a una referencia o tipo de valor.  
  
### Comentarios  
 `safe_cast` genera una `InvalidCastException` si no puede convertir *expression* al tipo especificado por *type\-id*.  Para detectar la `InvalidCastException`, especifique la opción del compilador [\/EH \(Modelo de control de excepciones\)](../build/reference/eh-exception-handling-model.md) y use una instrucción try\/catch.  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
### Ejemplos  
 **Ejemplo**  
  
 En el siguiente código de ejemplo se indica cómo usar `safe_cast` con [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].  
  
```cpp#  
// safe_cast_ZW.cpp  
// compile with: /ZW /EHsc  
  
using namespace default;  
using namespace Platform;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main(Array<String^>^ args) {  
   I1^ i1 = ref new X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // Fails because i1 is not derived from I3.  
   }   
   catch(InvalidCastException^ ic) {  
     wprintf(L"Caught expected exception: %s\n", ic->Message);  
   }  
}  
```  
  
 **Resultado**  
  
  **Excepción esperada detectada: InvalidCastException**   
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 `safe_cast` permite cambiar el tipo de una expresión y generar código MSIL comprobable.  
  
### Sintaxis  
  
```cpp  
  
[cli]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### Parámetros  
 *type\-id*  
 Identificador de un tipo de valor o referencia, un tipo de valor o una referencia de seguimiento a una referencia o tipo de valor.  
  
 *expression*  
 Expresión que evalúa a un identificador de un tipo de valor o referencia, un tipo de valor o una referencia de seguimiento a una referencia o tipo de valor.  
  
### Comentarios  
 La expresión `safe_cast<`*type\-id*`>(`*expression*`)` convierte la expresión de operando a un objeto de tipo type\-id.  
  
 El compilador aceptará un [static\_cast](../cpp/static-cast-operator.md) en la mayoría de los sitios en los que acepte `safe_cast`.  Sin embargo, `safe_cast` genera MSIL comprobable de forma garantizada, mientras que `static_cast` podría generar MSIL no comprobable.  Vea [Código puro y comprobable](../dotnet/pure-and-verifiable-code-cpp-cli.md) y [Peverify.exe \(PEVerify Tool\)](../Topic/Peverify.exe%20\(PEVerify%20Tool\).md) para más información sobre códigos comprobables.  
  
 Al igual que `static_cast`, `safe_cast` invoca conversiones definidas por el usuario.  
  
 Para obtener más información sobre las conversiones, vea [Operadores de conversión](../cpp/casting-operators.md).  
  
 `safe_cast` no aplica un **const\_cast** \(desechar **const**\).  
  
 `safe_cast` se encuentra en el espacio de nombres cli.  Vea [Espacios de nombres de plataforma, predeterminado y CLI](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) para más información.  
  
 Para obtener más información sobre **safe\_cast**, vea:  
  
-   [Conversiones de estilo C con \/clr \(C\+\+\/CLI\)](../windows/c-style-casts-with-clr-cpp-cli.md)  
  
-   [Cómo: Usar safe\_cast en C\+\+\/CLI](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)  
  
-   [Cómo: Convertir hacia abajo con safe\_cast](../misc/how-to-downcast-with-safe-cast.md)  
  
-   [Cómo: Usar los tipos safe\_cast y genéricos](../misc/how-to-use-safe-cast-and-generic-types.md)  
  
-   [Cómo: Usar las conversiones safe\_cast y definidas por el usuario](../misc/how-to-use-safe-cast-and-user-defined-conversions.md)  
  
-   [Cómo: Usar los tipos safe\_cast y de conversión boxing](../misc/how-to-use-safe-cast-and-boxing.md)  
  
-   [Cómo: Usar los tipos safe\_cast y unboxing](../misc/how-to-use-safe-cast-and-unboxing.md)  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 **Ejemplo**  
  
 Un ejemplo de un sitio en que el compilador no aceptará un `static_cast`, pero sí un `safe_cast`, es en conversiones entre tipos de interfaz no relacionadas.  Con `safe_cast`, el compilador no emitirá un error de conversión y realizará una comprobación en tiempo de ejecución para ver si tal conversión es posible.  
  
```cpp  
// safe_cast.cpp  
// compile with: /clr  
using namespace System;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main() {  
   I1^ i1 = gcnew X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // fail at runtime, no common type  
   }   
   catch(InvalidCastException^) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 **Resultado**  
  
  **Se capturó una excepción esperada.**   
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)