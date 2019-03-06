---
title: clase Enum (C++ / c++ / CLI y c++ / CX)
ms.date: 10/12/2018
ms.topic: reference
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
ms.openlocfilehash: aee3d4f44c18074ca536ff028565bbbd0e37d04c
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417429"
---
# <a name="enum-class--ccli-and-ccx"></a>clase Enum (C++ / c++ / CLI y c++ / CX)

Declara una enumeración en el ámbito de espacio de nombres, que es un tipo definido por el usuario que está compuesto de un conjunto de constantes con nombre llamadas enumeradores.

## <a name="all-runtimes"></a>Todos los runtimes

### <a name="remarks"></a>Comentarios

C++ / c++ / CX y c++ / compatibilidad con la CLI **clase enum pública** y **clase enum privada** que son similares a la estándar de C++ **clase enum** pero con la adición de la accesibilidad especificador. En **/CLR**, C ++ 11 **clase enum** tipo está permitido pero generará la advertencia c4472, que pretende garantizar que realmente desea el tipo de enumeración ISO y no C++ / c++ / CX y c++ / tipo de CLI. Para obtener más información acerca de la norma ISO de C++ **enum** palabra clave, consulte [enumeraciones](../cpp/enumerations-cpp.md).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

### <a name="syntax"></a>Sintaxis

```cpp
      access
      enum class
      enumeration-identifier
      [:underlying-type] { enumerator-list } [var];
accessenum structenumeration-identifier[:underlying-type] { enumerator-list } [var];
```

### <a name="parameters"></a>Parámetros

*access*<br/>
La accesibilidad de la enumeración, que puede ser **pública** o **privada**.

*enumeration-identifier*<br/>
Nombre de la enumeración.

*underlying-type*<br/>
(Opcional) Tipo de datos subyacente de la enumeración.

(Opcional. Windows en tiempo de ejecución solo) el tipo subyacente de la enumeración, que puede ser **bool**, **char**, `char16`, `int16`, `uint16`, **int**, `uint32`, `int64`, o `uint64`.

*enumerator-list*<br/>
Lista de nombres de enumerador separados con comas.

El valor de cada enumerador es una expresión constante definida implícitamente por el compilador o explícitamente mediante la notación, *enumerator*`=`*constant-expression*. De forma predeterminada, el valor del primer enumerador es cero si se define implícitamente. El valor de cada enumerador implícitamente definido subsiguiente es el valor del enumerador anterior + 1.

*var*<br/>
(Opcional) Nombre de una variable del tipo de enumeración.

### <a name="remarks"></a>Comentarios

Para obtener más información y ejemplos, vea [Enumeraciones](../cppcx/enums-c-cx.md).

Observe que el compilador emite mensajes de error si la expresión constante que define el valor de un enumerador no se puede representar mediante *underlying-type*.  Sin embargo, el compilador no indica un error para un valor que es inadecuado para el tipo subyacente. Por ejemplo:

- Si *underlying-type* es numérico y un enumerador especifica el valor máximo para ese tipo, el valor de la siguiente enumeración definida implícitamente no se puede representar.

- Si *tipo subyacente* es **bool**, y hay más de dos enumeradores implícitamente definido, los enumeradores después de que no se puede representar los dos primeros.

- Si *underlying-type* es `char16`y el valor de enumeración va de 0xD800 a 0xDFFF, el valor se puede representar. Sin embargo, el valor es lógicamente incorrecto porque representa la mitad del par suplente Unicode y no debe aparecer de forma aislada.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>Sintaxis

```cpp
      access
      enum class
      name [:type] { enumerator-list } var;
accessenum structname [:type] { enumerator-list } var;
```

### <a name="parameters"></a>Parámetros

*access*<br/>
Accesibilidad de la enumeración. Puede ser **pública** o **privada**.

*enumerator-list*<br/>
Una lista delimitada por comas de los identificadores (enumeradores) en la enumeración.

*name*<br/>
Nombre de la enumeración. Las enumeraciones administradas anónimas no se permiten.

*type*<br/>
(Opcional) El tipo subyacente de la *identificadores*. Esto puede ser cualquier tipo escalar, como versiones con o sin signo de **int**, **corto**, o **largo**.  **BOOL** o **char** también se permite.

*var*<br/>
(Opcional) Nombre de una variable del tipo de enumeración.

### <a name="remarks"></a>Comentarios

**enum class** y **enum struct** son declaraciones equivalentes.

Hay dos tipos de enumeraciones: administrada o C++/CX y estándar.

Una enumeración administrada o C++/CX puede definirse como sigue,

```cpp
public enum class day {sun, mon };
```

y es semánticamente equivalente a:

```cpp
ref class day {
public:
   static const int sun = 0;
   static const int mon = 1;
};
```

Una enumeración estándar puede definirse como sigue:

```cpp
enum day2 { sun, mon };
```

y es semánticamente equivalente a:

```cpp
static const int sun = 0;
static const int mon = 1;
```

Los nombres de enumerador administrados (*identifiers*) no se insertan en el ámbito en el que está definida la enumeración; todas las referencias a los enumeradores deben ser completas (*name*`::`*identifier*).  Por esta razón, no se puede definir una enumeración administrada anónima.

Los enumeradores de una enumeración estándar se insertan fuertemente en el ámbito de inclusión.  Es decir, si hay otro símbolo con el mismo nombre que un enumerador en el ámbito de inclusión, el compilador generará un error.

En Visual Studio 2002 y Visual Studio 2003, los enumeradores se insertaban (visible en el ámbito de inclusión a menos que hubiera otro identificador con el mismo nombre).

Si se define una enumeración estándar de C++ (sin **clase** o **struct**), la compilación con `/clr` hará que la enumeración se compile como una enumeración administrada.  La enumeración todavía tiene la semántica de una enumeración no administrada.  Tenga en cuenta que el compilador inserta un atributo, `Microsoft::VisualC::NativeEnumAttribute` para identificar la intención del programador de la enumeración sea una enumeración nativa.  Otros compiladores verán simplemente la enumeración estándar como enumeración administrada.

Una llamada, enumeración estándar se compila con `/clr` estarán visibles en el ensamblado como una enumeración administrada y pueden utilizarse en cualquier otro compilador administrado.   Sin embargo, una enumeración estándar sin nombre no será visible de forma pública desde el ensamblado.

En Visual Studio 2002 y Visual Studio 2003, una enumeración estándar usada como el tipo de un parámetro de función:

```cpp
// mcppv2_enum.cpp
// compile with: /clr
enum E { a, b };
void f(E) {System::Console::WriteLine("hi");}

int main() {
   E myi = b;
   f(myi);
}
```

emitiría lo siguiente en MSIL para la signatura de la función:

```cpp
void f(int32);
```

Sin embargo, en las versiones actuales del compilador, la enumeración estándar se emite como enumeración administrada con [NativeEnumAttribute] y lo siguiente en MSIL para la signatura de la función:

```cpp
void f(E)
```

Para obtener más información sobre enumeraciones nativas, vea [Declaraciones de enumeración de C++](../cpp/enumerations-cpp.md).

Para obtener más información sobre las enumeraciones CLR, vea:

- [Tipo subyacente de una enumeración](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

```cpp
// mcppv2_enum_2.cpp
// compile with: /clr
// managed enum
public enum class m { a, b };

// standard enum
public enum n { c, d };

// unnamed, standard enum
public enum { e, f } o;

int main()
{
   // consume managed enum
   m mym = m::b;
   System::Console::WriteLine("no automatic conversion to int: {0}", mym);
   System::Console::WriteLine("convert to int: {0}", (int)mym);

   // consume standard enum
   n myn = d;
   System::Console::WriteLine(myn);

   // consume standard, unnamed enum
   o = f;
   System::Console::WriteLine(o);
}
```

```Output
no automatic conversion to int: b

convert to int: 1

1

1
```

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](../windows/component-extensions-for-runtime-platforms.md)