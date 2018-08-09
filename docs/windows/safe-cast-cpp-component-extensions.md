---
title: safe_cast (extensiones de componentes de C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
dev_langs:
- C++
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 94973b62b83b8b574b8747febf2204251f1642d8
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017547"
---
# <a name="safecast-c-component-extensions"></a>safe_cast (Extensiones de componentes de C++)
El **safe_cast** operación devuelve la expresión especificada como el tipo especificado, si se realiza correctamente; en caso contrario, produce `InvalidCastException`.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 (No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes.)  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
```  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 **safe_cast** le permite cambiar el tipo de una expresión especificada. En situaciones donde se espera claramente una variable o parámetro convertible a un tipo determinado, puede usar **safe_cast** sin un **try-catch** bloque para detectar errores de programación durante el desarrollo. Para obtener más información, consulte [conversión (C++ / c++ / CX)](http://msdn.microsoft.com/library/windows/apps/hh755802.aspx).  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
```  
  
### <a name="parameters"></a>Parámetros  
 *identificador de tipo*  
 El tipo de conversión *expresión* a. Identificador de un tipo de valor o referencia, un tipo de valor o una referencia de seguimiento a una referencia o tipo de valor.  
  
 *Expresión*  
 Expresión que evalúa a un identificador de un tipo de valor o referencia, un tipo de valor o una referencia de seguimiento a una referencia o tipo de valor.  
  
### <a name="remarks"></a>Comentarios  
 **safe_cast** produce `InvalidCastException` si no se puede convertir *expresión* al tipo especificado por *identificador de tipo*. Para detectar `InvalidCastException`, especifique el [/EH (modelo de control de excepciones)](../build/reference/eh-exception-handling-model.md) opción del compilador y use un **try/catch** instrucción.  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: `/ZW`  
  
### <a name="examples"></a>Ejemplos  
  
 En el ejemplo de código siguiente se muestra cómo usar **safe_cast** con el tiempo de ejecución de Windows.  
  
```cpp  
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
  
```Output  
Caught expected exception: InvalidCastException  
```  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **safe_cast** le permite cambiar el tipo de una expresión y generar código MSIL comprobable.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
[cli]:: safe_cast<  
type-id  
>(  
expression  
)  
```  
  
### <a name="parameters"></a>Parámetros  
 *identificador de tipo*  
 Identificador de un tipo de valor o referencia, un tipo de valor o una referencia de seguimiento a una referencia o tipo de valor.  
  
 *Expresión*  
 Expresión que evalúa a un identificador de un tipo de valor o referencia, un tipo de valor o una referencia de seguimiento a una referencia o tipo de valor.  
  
### <a name="remarks"></a>Comentarios  
 La expresión `safe_cast<` *identificador de tipo*`>(`*expresión* `)` convierte la expresión de operando a un objeto de tipo de identificador de tipo.  
  
 El compilador aceptará un [static_cast](../cpp/static-cast-operator.md) en la mayoría de los lugares que aceptará un **safe_cast**.  Sin embargo, **safe_cast** garantiza que genera MSIL comprobable, mientras que un **static_cast** podría generar MSIL no comprobable.  Consulte [código puro y comprobable (C++ / c++ / CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) y [Peverify.exe (herramienta PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) para obtener más información sobre códigos comprobables.  
  
 Al igual que **static_cast**, **safe_cast** invoca conversiones definidas por el usuario.  
  
 Para obtener más información sobre las conversiones, vea [operadores de conversión](../cpp/casting-operators.md).  
  
 **safe_cast** no se aplica un **const_cast** (desechar **const**).  
  
 **safe_cast** está en el espacio de nombres cli.  Consulte [de plataforma, predeterminado y cli de espacios de nombres](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) para obtener más información.  
  
 Para obtener más información sobre **safe_cast**, consulte:  
  
-   [Conversiones de estilo C con /clr (C++ / c++ / CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)  
  
-   [Cómo: Usar safe_cast en C++/CLI](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)  

### <a name="requirements"></a>Requisitos  
 Opción del compilador: `/clr`  
  
### <a name="examples"></a>Ejemplos  
  
 Un ejemplo de donde el compilador no aceptará un **static_cast** pero aceptará un **safe_cast** es en conversiones entre tipos de interfaz no relacionadas.  Con **safe_cast**, el compilador no emitirá un error de conversión y realizará una comprobación en tiempo de ejecución para ver si es posible la conversión  
  
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
  
```Output  
Caught expected exception  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)