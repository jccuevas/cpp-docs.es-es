---
title: Tipos administrados (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], managed
- managed data types [C++]
- .NET Framework [C++], managed types
- data types [C++], .NET feature access
- main function, in managed applications
- managed code, main() function
- .NET Framework [C++], C++ equivalents
- __nogc type declarations
- __value keyword, issues when nesting
- equality, testing for
- versioning, diagnosing conflicts
- versioning
- exceptions, diagnosing odd behavior
- compatibility, between assemblies
ms.assetid: 679b8ed3-d966-4a0c-b627-2a3f3ec96b74
ms.openlocfilehash: fe3b5e3a887e4a440c3570750c569ec6c71ea611
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595967"
---
# <a name="managed-types-ccli"></a>Tipos administrados (C++/CLI)

Visual C++ permite el acceso a las características de .NET a través de los tipos administrados, que proporcionan compatibilidad para las características de common language runtime y están sujetos a las ventajas y las restricciones de tiempo de ejecución.

## <a name="main_functions"></a> Tipos administrados y la función main

Al escribir una aplicación con **/CLR**, los argumentos de la **main()** función no puede ser de un tipo administrado.

Un ejemplo de una firma correcta es:

```cpp
// managed_types_and_main.cpp
// compile with: /clr
int main(int, char*[], char*[]) {}
```

## <a name="dotnet"></a> Equivalentes de .NET framework para tipos nativos de C++

La siguiente tabla muestra las palabras clave para los tipos integrados de Visual C++, que son alias de tipos predefinidos en el **sistema** espacio de nombres.

|Tipo de Visual C++|Tipo de .NET Framework|
|-----------------------|-------------------------|
|**bool**|**System.Boolean**|
|**firmado char** (consulte [/j](../build/reference/j-default-char-type-is-unsigned.md) para obtener más información)|**System.SByte**|
|**unsigned char**|**System.Byte**|
|**wchar_t**|**System.Char**|
|**Double** y **long double**|**System.Double**|
|**float**|**System.Single**|
|**int**, **firmado int**, **largo**, y **long con signo**|**System.Int32**|
|**int sin signo** y **unsigned long**|**System.UInt32**|
|**__int64** y **firmado __int64**|**System.Int64**|
|**unsigned __int64**|**System.UInt64**|
|**short** y **firmado resumen**|**System.Int16**|
|**unsigned short**|**System.UInt16**|
|**void**|**System.Void**|

## <a name="version_issues"></a> Problemas de versión con tipos de valor anidados en tipos nativos

Considere la posibilidad de un componente de ensamblado firmado (nombre seguro) usado para compilar un ensamblado de cliente. El componente contiene un tipo de valor que se usa en el cliente como el tipo de un miembro de una unión nativa, una clase o una matriz. Si una versión futura del componente cambia el tamaño o el diseño del tipo de valor, se debe volver a compilar el cliente.

Crear un archivo de claves con [sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) (`sn -k mykey.snk`).

### <a name="example"></a>Ejemplo

El ejemplo siguiente es el componente.

```cpp
// nested_value_types.cpp
// compile with: /clr /LD
using namespace System::Reflection;
[assembly:AssemblyVersion("1.0.0.*"),
assembly:AssemblyKeyFile("mykey.snk")];

public value struct S {
   int i;
   void Test() {
      System::Console::WriteLine("S.i = {0}", i);
   }
};
```

### <a name="example"></a>Ejemplo

En este ejemplo es el cliente:

```cpp
// nested_value_types_2.cpp
// compile with: /clr
#using <nested_value_types.dll>

struct S2 {
   S MyS1, MyS2;
};

int main() {
   S2 MyS2a, MyS2b;
   MyS2a.MyS1.i = 5;
   MyS2a.MyS2.i = 6;
   MyS2b.MyS1.i = 10;
   MyS2b.MyS2.i = 11;

   MyS2a.MyS1.Test();
   MyS2a.MyS2.Test();
   MyS2b.MyS1.Test();
   MyS2b.MyS2.Test();
}
```

### <a name="output"></a>Salida

```Output
S.i = 5
S.i = 6
S.i = 10
S.i = 11
```

### <a name="comments"></a>Comentarios

Sin embargo, si agrega otro miembro a `struct S` en nested_value_types.cpp, (por ejemplo, `double d;`) y volver a compilar el componente sin volver a compilar el cliente, el resultado es una excepción no controlada (de tipo <xref:System.IO.FileLoadException?displayProperty=fullName>).

## <a name="test_equality"></a> Cómo: probar la igualdad

En el ejemplo siguiente, una prueba de igualdad que usa Extensiones administradas para C++ se basa en lo que hacen referencia los identificadores.

### <a name="example"></a>Ejemplo

```cpp
// mcppv2_equality_test.cpp
// compile with: /clr /LD
using namespace System;

bool Test1() {
   String ^ str1 = "test";
   String ^ str2 = "test";
   return (str1 == str2);
}
```

El IL para este programa muestra que el valor devuelto se implementa mediante una llamada a op_Equality.

```MSIL
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,
                                                               string)
```

## <a name="diagnose_fix"></a> Cómo: diagnosticar y resolver los problemas de compatibilidad de ensamblados

En este tema se explica qué puede ocurrir cuando la versión de un ensamblado al que hace referencia en tiempo de compilación no coincide con la versión del ensamblado al que hace referencia en tiempo de ejecución y cómo evitar el problema.

Cuando se compila un ensamblado, se pueden hacer referencia a otros ensamblados con el `#using` sintaxis. Durante la compilación, se tiene acceso a estos ensamblados por el compilador. Información de estos ensamblados se usa para tomar decisiones de optimización.

Sin embargo, si se cambia y se vuelve a compilar el ensamblado de referencia y no vuelve a compilar el ensamblado de referencia que depende de él, los ensamblados, es posible que no sea todavía compatible. Las decisiones de optimización que eran válidas en primer lugar pueden no ser correctas con respecto a la nueva versión del ensamblado. Varios errores en tiempo de ejecución podrían producirse debido a estas incompatibilidades. No hay ninguna excepción específica que se producirán en estos casos. La manera en que se notifica el error en tiempo de ejecución depende de la naturaleza del cambio de código que causó el problema.

Estos errores no deben ser un problema en el código de producción final siempre y cuando se vuelve a generar toda la aplicación para la versión de lanzamiento del producto. Los ensamblados que se lanzan al público deben marcarse con un número de versión oficial que se asegurará de que se evitan estos problemas. Para obtener más información, vea [Versiones de los ensamblados](/dotnet/framework/app-domains/assembly-versioning).

### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>Diagnosticar y corregir un error de incompatibilidad

1. Si detecta las excepciones en tiempo de ejecución u otras condiciones de error que se producen en el código que hace referencia a otro ensamblado y tiene ninguna otra causa identificado, puede estar tratando con un ensamblado actualizado.

1. En primer lugar, aislar y reproduzca la excepción u otra condición de error. Un problema que se produce debido a una excepción obsoleta debería ser reproducible.

1. Compruebe la marca de tiempo de cualquier ensamblado al que hace referencia en la aplicación.

1. Si las marcas de tiempo de todos los ensamblados que se hace referencia son posteriores a la marca de tiempo de la última compilación de la aplicación, la aplicación está obsoleta. Si esto ocurre, vuelva a compilar la aplicación con el ensamblado más reciente y realizar los cambios de código necesarios.

1. Vuelva a ejecutar la aplicación, realice los pasos que reproducen el problema y comprobación que no se produce la excepción.

### <a name="example"></a>Ejemplo

El programa siguiente ilustra el problema al reducir la accesibilidad de un método y al intentar obtener acceso a ese método en otro ensamblado sin volver a compilar. Intente compilar `changeaccess.cpp` primero. Esto es el ensamblado que se hace referencia que cambiará. A continuación, compile `referencing.cpp`. La compilación se realiza correctamente. Ahora, reducir la accesibilidad del método llamado. Volver a compilar `changeaccess.cpp` con la marca `/DCHANGE_ACCESS`. Esto hace que el método protegido, en lugar de privado, por lo que ya puede llamarse legalmente. Sin recompilar `referencing.exe`, vuelva a ejecutar la aplicación. Una excepción <xref:System.MethodAccessException> dará como resultado.

```cpp
// changeaccess.cpp
// compile with: /clr:safe /LD
// After the initial compilation, add /DCHANGE_ACCESS and rerun
// referencing.exe to introduce an error at runtime. To correct
// the problem, recompile referencing.exe

public ref class Test {
#if defined(CHANGE_ACCESS)
protected:
#else
public:
#endif

  int access_me() {
    return 0;
  }

};
```

```cpp
// referencing.cpp
// compile with: /clr:safe
#using <changeaccess.dll>

// Force the function to be inline, to override the compiler's own
// algorithm.
__forceinline
int CallMethod(Test^ t) {
  // The call is allowed only if access_me is declared public
  return t->access_me();
}

int main() {
  Test^ t = gcnew Test();
  try
  {
    CallMethod(t);
    System::Console::WriteLine("No exception.");
  }
  catch (System::Exception ^ e)
  {
    System::Console::WriteLine("Exception!");
  }
  return 0;
}
```

## <a name="see-also"></a>Vea también

[Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Interoperabilidad con otros lenguajes de .NET (C++/CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)<br/>
[Tipos administrados (C++/CLI)](../dotnet/managed-types-cpp-cli.md)<br/>
[#using (directiva)](../preprocessor/hash-using-directive-cpp.md)
