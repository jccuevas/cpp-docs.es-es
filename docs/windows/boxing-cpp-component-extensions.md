---
title: Conversión boxing (C++ / c++ / CLI y c++ / CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- boxing, C++
ms.assetid: b5fd2c98-c578-4f83-8257-6dd663478665
ms.openlocfilehash: 2308265b223304f30c8715d12d14e89bcb7344de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475444"
---
# <a name="boxing--ccli-and-ccx"></a>Conversión boxing (C++ / c++ / CLI y c++ / CX)

Se llama a la conversión de tipos de valor a los objetos *boxing*, y se llama a la conversión de objetos a los tipos de valor *unboxing*.

## <a name="all-runtimes"></a>Todos los runtimes

(No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

C++ / c++ / CX admite la sintaxis abreviada para tipos de valor de conversión boxing y unboxing de tipos de referencia. Se aplica la conversión boxing a un tipo de valor cuando este se asigna a una variable de tipo `Object`. Se aplica una conversión unboxing a una variable `Object` cuando esta se asigna a una variable de tipo de valor y el tipo al que se le ha aplicado la conversión unboxing se especifica entre paréntesis; es decir, cuando la variable de objeto se convierte en un tipo de valor.

```cpp
  Platform::Object^
  object_variable  = value_variable;
value_variable = (value_type) object_variable;
```

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

### <a name="examples"></a>Ejemplos

En el siguiente ejemplo de código, se aplica una conversión boxing y unboxing a un valor `DateTime`. En primer lugar, el ejemplo se obtiene un `DateTime` valor que representa la fecha y hora actual y lo asigna a un `DateTime` variable. El `DateTime` es aplicar la conversión boxing asignándolo a una `Object` variable. Por último, el valor con conversión boxing se aplica la conversión unboxing asignando a otro `DateTime` variable.

Para probar el ejemplo, cree un `BlankApplication` del proyecto, reemplace el `BlankPage::OnNavigatedTo()` método y, a continuación, especifique los puntos de interrupción en el corchete de cierre y la asignación de variable `str1`. Cuando el ejemplo alcance el corchete de cierre, examine `str1`.

```cpp
void BlankPage::OnNavigatedTo(NavigationEventArgs^ e)
{
    using namespace Windows::Globalization::DateTimeFormatting;

    Windows::Foundation::DateTime dt, dtAnother;
    Platform::Object^ obj1;

    Windows::Globalization::Calendar^ c =
        ref new Windows::Globalization::Calendar;
    c->SetToNow();
    dt = c->GetDateTime();
    auto dtf = ref new DateTimeFormatter(
                           YearFormat::Full,
                           MonthFormat::Numeric,
                           DayFormat::Default,
                           DayOfWeekFormat::None);
    String^ str1 = dtf->Format(dt);
    OutputDebugString(str1->Data());
    OutputDebugString(L"\r\n");

    // Box the value type and assign to a reference type.
    obj1 = dt;
    // Unbox the reference type and assign to a value type.
    dtAnother = (Windows::Foundation::DateTime) obj1;

    // Format the DateTime for display.
    String^ str2 = dtf->Format(dtAnother);
    OutputDebugString(str2->Data());
}
```

Para obtener más información, consulte [conversión Boxing (C++ / c++ / CX)](https://msdn.microsoft.com/library/windows/apps/hh969554.aspx).

## <a name="common-language-runtime"></a>Common Language Runtime

Tipos de valor de los cuadros del compilador <xref:System.Object>. Esto es posible por una conversión definida por el compilador que convierte tipos de valor en <xref:System.Object>.

Aplicar conversiones boxing y unboxing permite tratar a los tipos de valor como objetos. Los tipos de valor, incluidos los tipos de estructura y los tipos integrados, como int, se pueden convertir a y desde el tipo <xref:System.Object>.

Para obtener más información, consulte:

- [Cómo: Solicitar explícitamente la conversión boxing](../dotnet/how-to-explicitly-request-boxing.md)

- [Cómo: Usar gcnew para crear tipos de valor y usar la conversión boxing implícita](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)

- [Cómo: Aplicar la conversión unboxing](../dotnet/how-to-unbox.md)

- [Conversiones estándar y conversión boxing implícita](../dotnet/standard-conversions-and-implicit-boxing.md)

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el siguiente ejemplo se muestra cómo funciona la conversión boxing implícita.

```cpp
// vcmcppv2_explicit_boxing2.cpp
// compile with: /clr
using namespace System;

ref class A {
public:
   void func(System::Object^ o){Console::WriteLine("in A");}
};

value class V {};

interface struct IFace {
   void func();
};

value class V1 : public IFace {
public:
   virtual void func() {
      Console::WriteLine("Interface function");
   }
};

value struct V2 {
   // conversion operator to System::Object
   static operator System::Object^(V2 v2) {
      Console::WriteLine("operator System::Object^");
      return (V2^)v2;
   }
};

void func1(System::Object^){Console::WriteLine("in void func1(System::Object^)");}
void func1(V2^){Console::WriteLine("in func1(V2^)");}

void func2(System::ValueType^){Console::WriteLine("in func2(System::ValueType^)");}
void func2(System::Object^){Console::WriteLine("in func2(System::Object^)");}

int main() {
   // example 1 simple implicit boxing
   Int32^ bi = 1;
   Console::WriteLine(bi);

   // example 2 calling a member with implicit boxing
   Int32 n = 10;
   Console::WriteLine("xx = {0}", n.ToString());

   // example 3 implicit boxing for function calls
   A^ a = gcnew A;
   a->func(n);

   // example 4 implicit boxing for WriteLine function call
   V v;
   Console::WriteLine("Class {0} passed using implicit boxing", v);
   Console::WriteLine("Class {0} passed with forced boxing", (V^)(v));   // force boxing

   // example 5 casting to a base with implicit boxing
   V1 v1;
   IFace ^ iface = v1;
   iface->func();

   // example 6 user-defined conversion preferred over implicit boxing for function-call parameter matching
   V2 v2;
   func1(v2);   // user defined conversion from V2 to System::Object preferred over implicit boxing
                // Will call void func1(System::Object^);

   func2(v2);   // OK: Calls "static V2::operator System::Object^(V2 v2)"
   func2((V2^)v2);   // Using explicit boxing: calls func2(System::ValueType^)
}
```

```Output
1

xx = 10

in A

Class V passed using implicit boxing

Class V passed with forced boxing

Interface function

in func1(V2^)

in func2(System::ValueType^)

in func2(System::ValueType^)
```

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](../windows/component-extensions-for-runtime-platforms.md)