---
title: safe_cast (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
ms.openlocfilehash: 199fda710a077998c6b10f101f6ebc15573e675e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516640"
---
# <a name="safecast-ccli-and-ccx"></a>safe_cast (C++/CLI y C++/CX)

La operación **safe_cast**, si es correcta, devuelve la expresión especificada como el tipo especificado; en caso contrario, produce una `InvalidCastException`.

## <a name="all-runtimes"></a>Todos los runtimes

(No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes).

### <a name="syntax"></a>Sintaxis

```cpp
[default]:: safe_cast< type-id >( expression )
```

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

**safe_cast** permite cambiar el tipo de una expresión especificada. En situaciones donde se espera claramente una variable o parámetro convertible a un tipo determinado, puede usar **safe_cast** sin un bloque **try-catch** para detectar errores de programación durante el desarrollo. Para obtener más información, consulte [Convertir (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh755802.aspx).

### <a name="syntax"></a>Sintaxis

```cpp
[default]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>Parámetros

*type-id*<br/>
Tipo al que se va a convertir *expression*. Identificador de un tipo de valor o referencia, un tipo de valor o una referencia de seguimiento a una referencia o tipo de valor.

*expression*<br/>
Expresión que evalúa a un identificador de un tipo de valor o referencia, un tipo de valor o una referencia de seguimiento a una referencia o tipo de valor.

### <a name="remarks"></a>Comentarios

**safe_cast** genera una `InvalidCastException` si no puede convertir *expression* al tipo especificado por *type-id*. Para detectar la `InvalidCastException`, especifique la opción del compilador [/EH (Modelo de control de excepciones)](../build/reference/eh-exception-handling-model.md) y use una instrucción **try/catch**.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

### <a name="examples"></a>Ejemplos

En el ejemplo de código siguiente se muestra cómo usar **safe_cast** con Windows Runtime.

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

**safe_cast** permite cambiar el tipo de una expresión y generar código MSIL comprobable.

### <a name="syntax"></a>Sintaxis

```cpp
[cli]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>Parámetros

*type-id*<br/>
Identificador de un tipo de valor o referencia, un tipo de valor o una referencia de seguimiento a una referencia o tipo de valor.

*expression*<br/>
Expresión que evalúa a un identificador de un tipo de valor o referencia, un tipo de valor o una referencia de seguimiento a una referencia o tipo de valor.

### <a name="remarks"></a>Comentarios

La expresión `safe_cast<`*type-id*`>(`*expression*`)` convierte el operando *expression* a un objeto de tipo *type-id*.

El compilador aceptará un [static_cast](../cpp/static-cast-operator.md) en la mayoría de los sitios en los que acepte **safe_cast**.  Sin embargo, **safe_cast** genera MSIL comprobable de forma garantizada, mientras que **static_cast** podría generar MSIL no comprobable.  Consulte el artículo sobre [el código puro y comprobable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) y [Peverify.exe (Herramienta PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) para más información sobre códigos comprobables.

Al igual que **static_cast**, **safe_cast** invoca conversiones definidas por el usuario.

Para obtener más información sobre las conversiones, consulte [Operadores de conversión](../cpp/casting-operators.md).

**safe_cast** no aplica un **const_cast** (desechar **const**).

**safe_cast** se encuentra en el espacio de nombres cli.  Consulte [Platform, default, and cli Namespaces](platform-default-and-cli-namespaces-cpp-component-extensions.md) (Espacios de nombres de plataforma, predeterminado y cli) para obtener más información.

Para obtener más información sobre **safe_cast**, consulte:

- [C-Style Casts with /clr (C++/CLI)](c-style-casts-with-clr-cpp-cli.md) [Conversiones de estilo C con /clr (C++/CLI)]

- [Cómo: Usar safe_cast en C++/CLI](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

Un ejemplo de un sitio en que el compilador no aceptará un **static_cast**, pero sí un **safe_cast**, es en conversiones entre tipos de interfaz no relacionadas.  Con **safe_cast**, el compilador no emitirá un error de conversión y realizará una comprobación en tiempo de ejecución para ver si tal conversión es posible.

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

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)
