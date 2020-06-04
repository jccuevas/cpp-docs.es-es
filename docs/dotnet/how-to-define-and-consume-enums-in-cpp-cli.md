---
title: 'Cómo: Definir y usar enumeraciones en C++/CLI'
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: cf3bb23069b2692c0ca4ce270a5b8060195becf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370171"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>Cómo: Definir y usar enumeraciones en C++/CLI

En este tema se describen las enumeraciones en C++/CLI.

## <a name="specifying-the-underlying-type-of-an-enum"></a>Especificar el tipo subyacente de una enumeración

De forma predeterminada, el tipo `int`subyacente de una enumeración es .  Sin embargo, puede especificar el tipo que `int` `short`se `long` `__int32`va a firmar o los formularios sin firmar de , , , , o `__int64`.  También se puede usar `char`.

```cpp
// mcppv2_enum_3.cpp
// compile with: /clr
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};

int main() {
   // fully qualified names, enumerator not injected into scope
   day_char d = day_char::sun, e = day_char::mon;
   System::Console::WriteLine(d);
   char f = (char)d;
   System::Console::WriteLine(f);
   f = (char)e;
   System::Console::WriteLine(f);
   e = day_char::tue;
   f = (char)e;
   System::Console::WriteLine(f);
}
```

**Salida**

```Output
sun
0
1
2
```

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>Cómo convertir entre enumeraciones administradas y estándar

No hay una conversión estándar entre una enumeración y un tipo entero; se requiere un yeso.

```cpp
// mcppv2_enum_4.cpp
// compile with: /clr
enum class day {sun, mon, tue, wed, thu, fri, sat};
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum

int main() {
   day a = day::sun;
   day2 = sun;
   if ((int)a == day2)
   // or...
   // if (a == (day)day2)
      System::Console::WriteLine("a and day2 are the same");
   else
      System::Console::WriteLine("a and day2 are not the same");
}
```

**Salida**

```Output
a and day2 are the same
```

## <a name="operators-and-enums"></a>Operadores y enums

Los siguientes operadores son válidos en enumeraciones en C++/CLI:

|Operator|
|--------------|
|• !- \<  >  \<>?|
|+ -|
|&#124; de &|
|++ --|
|sizeof|

Los operadores &#124; , & + + + , se definen solo para las enumeraciones con tipos subyacentes integrales, sin incluir bool.  Ambos operandos deben ser del tipo de enumeración.

El compilador no realiza ninguna comprobación estática o dinámica del resultado de una operación de enumeración; una operación puede dar lugar a un valor que no está en el intervalo de enumeradores válidos de la enumeración.

> [!NOTE]
> C++11 introduce tipos de clase enum en código no administrado que son significativamente diferentes de las clases de enumeración administradas en C++/CLI. En particular, el tipo de clase enum C++11 no admite los mismos operadores que el tipo de clase enum administrada en C++/CLI, y el código fuente C++/CLI debe proporcionar un especificador de accesibilidad en declaraciones de clase de enumeración administradas para distinguirlos de las declaraciones de clase enum no administradas (C++11). Para obtener más información acerca de las clases enum en C++/CLI, C++/CX y C++11, consulte [enum class](../extensions/enum-class-cpp-component-extensions.md).

```cpp
// mcppv2_enum_5.cpp
// compile with: /clr
private enum class E { a, b } e, mask;
int main() {
   if ( e & mask )   // C2451 no E->bool conversion
      ;

   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)
      ;

   if ( ( e & mask ) != E() )   // OK
      ;
}
```

```cpp
// mcppv2_enum_6.cpp
// compile with: /clr
private enum class day : int {sun, mon};
enum : bool {sun = true, mon = false} day2;

int main() {
   day a = day::sun, b = day::mon;
   day2 = sun;

   System::Console::WriteLine(sizeof(a));
   System::Console::WriteLine(sizeof(day2));
   a++;
   System::Console::WriteLine(a == b);
}
```

**Salida**

```Output
4
1
True
```

## <a name="see-also"></a>Consulte también

[enum class](../extensions/enum-class-cpp-component-extensions.md)
