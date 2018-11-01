---
title: Convertir (C++/CX)
ms.date: 06/19/2018
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
ms.openlocfilehash: 65d489d14c91b462e5a2bbe8bd60fce2657904a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454826"
---
# <a name="casting-ccx"></a>Convertir (C++/CX)

Se aplican cuatro operadores de conversión diferentes a los tipos en tiempo de ejecución de Windows: [static_cast (operador)](../cpp/static-cast-operator.md), [dynamic_cast (operador)](../cpp/dynamic-cast-operator.md), **safe_cast (operador)**, y [ reinterpret_cast (operador)](../cpp/reinterpret-cast-operator.md). **safe_cast** y **static_cast** produce una excepción cuando no se puede realizar la conversión; [static_cast (operador)](../cpp/static-cast-operator.md) también realiza la comprobación de tipos en tiempo de compilación. **dynamic_cast** devuelve **nullptr** si se produce un error al convertir el tipo. Aunque **reinterpret_cast** devuelve un valor distinto de null, que no sea válido. Por este motivo, recomendamos que no use **reinterpret_cast** a menos que sepa que la conversión se realizará correctamente. Además, se recomienda que no usar conversiones de estilo C en su C / c++ / CX código porque son idénticas a **reinterpret_cast**.

El compilador y el runtime también realizan conversiones implícitamente. Por ejemplo, en operaciones de conversión boxing cuando se pasa un tipo de valor o un tipo integrado como argumentos a un método cuyo tipo de parámetro es `Object^`. En teoría, una conversión implícita nunca debe producir una excepción en tiempo de ejecución; si el compilador no puede realizar una conversión implícita, genera un error en tiempo de compilación.

En tiempo de ejecución de Windows es una abstracción sobre COM, que usa códigos de error HRESULT en lugar de excepciones. En general, [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) indica un error COM de bajo nivel de E_NOINTERFACE.

## <a name="staticcast"></a>static_cast

Un **static_cast** se comprueba en tiempo de compilación para determinar si hay una relación de herencia entre los dos tipos. La conversión produce un error del compilador si los tipos no están relacionados.

Un **static_cast** en ref clase también provoca que se realizará una comprobación de tiempo de ejecución. Un **static_cast** en ref clase puede pasar la comprobación de tiempo de compilación pero no en tiempo de ejecución; en este caso un `Platform::InvalidCastException` se produce. En general, no es necesario controlar estas excepciones porque casi siempre indican errores de programación que puedes eliminar durante las fases de desarrollo y pruebas.

Use **static_cast** si el código declara explícitamente una relación entre los dos tipos, y por lo tanto, está seguro de que la conversión debería funcionar.

```cpp
    interface class A{};
    public ref class Class1 sealed : A { };
    // ...
    A^ obj = ref new Class1(); // Class1 is an A
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.
    Class1^ c = static_cast<Class1^>(obj);
```

## <a name="safecast"></a>safe_cast

El **safe_cast** operador forma parte de Windows en tiempo de ejecución. Realiza una comprobación de tipo en tiempo de ejecución y produce una excepción `Platform::InvalidCastException` si se produce un error en la conversión. Use **safe_cast** cuando un error de tiempo de ejecución indica una condición excepcional. El propósito principal de **safe_cast** es ayudar a identificar errores de programación durante el desarrollo y pruebas de fases en el punto donde se producen. No tienes que controlar la excepción porque la propia excepción no controlada identifica el punto de error.

Utiliza safe_cast si el código no declara la relación pero estás seguro de que la conversión se va a realizar correctamente.

```cpp
    // A and B are not related
    interface class A{};
    interface class B{};
    public ref class Class1 sealed : A, B { };
    // ...
    A^ obj = ref new Class1();

    // You know that obj’s backing type implements A and B, but
    // the compiler can’t tell this by comparing A and B. The run-time type check succeeds.
    B^ obj2 = safe_cast<B^>(obj);
```

## <a name="dynamiccast"></a>dynamic_cast

Use **dynamic_cast** cuando se convierte un objeto (más concretamente, **^**) a un tipo más derivado, creas que el destino de objeto puede ser a veces **nullptr** o que la conversión puede producir un error, y desea controlar esa condición como una ruta de acceso del código normal en lugar de una excepción. Por ejemplo, en el **aplicación vacía (Windows Universal)** plantilla de proyecto, el `OnLaunched` método app.xamp.cpp usa **dynamic_cast** para comprobar si la ventana de la aplicación tiene contenido. No es un error si no tiene contenido; es una condición esperada. `Windows::Current::Content` es `Windows::UI::XAML::UIElement` y la conversión es a `Windows::UI.XAML::Controls::Frame`, que es un tipo más derivado en la jerarquía de herencia.

```cpp
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ args)
{
    auto rootFrame = dynamic_cast<Frame^>(Window::Current->Content);

    // Do not repeat app initialization when the window already has content,
    // just ensure that the window is active
    if (rootFrame == nullptr)
    {
        // Create a Frame to act as the navigation context and associate it with
        // a SuspensionManager key
        rootFrame = ref new Frame();
        // ...
    }
}
```

Otro uso de **dynamic_cast** es para sondear un `Object^` para determinar si contiene un tipo de valor con conversión boxing. En este caso, intentas `dynamic_cast<Platform::Box>` o `dynamic_cast<Platform::IBox>`.

## <a name="dynamiccast-and-tracking-references-"></a>dynamic_cast y referencias de seguimiento (%)

También puede aplicar un **dynamic_cast** a una referencia de seguimiento, pero en este caso, la conversión se comporta como **safe_cast**. Produce `Platform::InvalidCastException` en caso de error porque una referencia de seguimiento no puede tener un valor de **nullptr**.

## <a name="reinterpretcast"></a>reinterpret_cast

Te recomendamos que no utilices [reinterpret_cast](../cpp/reinterpret-cast-operator.md) debido a que en este caso no se realiza una comprobación en tiempo de compilación ni una comprobación en tiempo de ejecución. En el peor de los casos, un **reinterpret_cast** hace posible errores pasen desapercibidos en tiempo de desarrollo y provocar errores imperceptibles o catastróficos en el comportamiento del programa de programación. Por lo tanto, recomendamos que use **reinterpret_cast** solo en esos casos raros cuando debe convertir entre tipos no relacionados y sabe que la conversión se realizará correctamente. Un ejemplo de uso poco frecuente consiste en convertir un tipo en tiempo de ejecución de Windows a su tipo ABI subyacente, esto significa que estás tomando el control el recuento de referencias para el objeto. Para ello, te recomendamos utilizar el puntero inteligente [ComPtr Class](../cpp/com-ptr-t-class.md) . De lo contrario, debes llamar específicamente a Release en la interfaz. En el ejemplo siguiente se muestra cómo se puede convertir una clase ref en `IInspectable*`.

```cpp
#include <wrl.h>
using namespace Microsoft::WRL;
auto winRtObject = ref new SomeWinRTType();
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);
// ...
```

Si usas **reinterpret_cast** para convertir de interfaz de oneWindows en tiempo de ejecución a otra, haces que el objeto se libere dos veces. Por lo tanto, use esta conversión solo si va a convertir en una interfaz de extensiones de componentes que no son de Visual C++.

## <a name="abi-types"></a>Tipos de ABI.

- Los tipos de ABI residen en encabezados en Windows SDK. Afortunadamente, los nombres de los encabezados coinciden con los de los espacios de nombres. Por ejemplo, `windows.storage.h`.

- Los tipos de ABI residen en un espacio de nombres ABI especial. Por ejemplo, `ABI::Windows::Storage::Streams::IBuffer*`.

- Las conversiones entre un tipo de interfaz de Windows en tiempo de ejecución y su tipo de ABI equivalente siempre son seguras, es decir, `IBuffer^` a `ABI::IBuffer*`.

- Una clase en tiempo de ejecución de Windows en tiempo de ejecución siempre debe convertirse en `IInspectable*` o su interfaz de forma predeterminada, si se conoce.

- Después de convertir a tipos de ABI, eres el propietario de la duración del tipo y debes seguir las reglas de COM. Recomendamos usar `WRL::ComPtr` para simplificar la administración de la duración de los punteros de ABI.

En la tabla siguiente se resume los casos en los que es seguro usar **reinterpret_cast**. En todos ellos, la conversión es segura en ambas direcciones.

|||
|-|-|
|`HSTRING`|`String^`|
|`HSTRING*`|`String^*`|
|`IInspectable*`|`Object^`|
|`IInspectable**`|`Object^*`|
|`IInspectable-derived-type*`|`same-interface-from-winmd^`|
|`IInspectable-derived-type**`|`same-interface-from-winmd^*`|
|`IDefault-interface-of-RuntimeClass*`|`same-RefClass-from-winmd^`|
|`IDefault-interface-of-RuntimeClass**`|`same-RefClass-from-winmd^*`|

## <a name="see-also"></a>Vea también

- [Sistema de tipos](../cppcx/type-system-c-cx.md)
- [Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)
- [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)
