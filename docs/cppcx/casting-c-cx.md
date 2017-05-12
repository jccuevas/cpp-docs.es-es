---
title: "Convertir (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
caps.latest.revision: 15
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 15
---
# Convertir (C++/CX)
Se aplican cuatro operadores de conversión diferentes a los tipos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]: [static\_cast \(Operador\)](../cpp/static-cast-operator.md), [dynamic\_cast \(Operador\)](../cpp/dynamic-cast-operator.md), [safe\_cast \(Operador\)](~/windows/safe-cast-cpp-component-extensions.md) y [reinterpret\_cast \(Operador\)](../cpp/reinterpret-cast-operator.md).`safe_cast` y `static_cast` producen una excepción cuando no se puede realizar la conversión; el [operador static\_cast](../cpp/static-cast-operator.md) también realiza la comprobación de tipos en tiempo de compilación.`dynamic_cast` devuelve `nullptr` si no puede convertir el tipo. Aunque `reinterpret_cast` devuelve un valor no NULL, puede no ser válido. Por eso, recomendamos que no uses `reinterpret_cast` a menos que sepas que la conversión se realizará correctamente. Además, recomendamos no usar conversiones de estilo C en el código de [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) porque son idénticas a `reinterpret_cast`.  
  
 El compilador y el runtime también realizan conversiones implícitamente. Por ejemplo, en operaciones de conversión boxing cuando se pasa un tipo de valor o un tipo integrado como argumentos a un método cuyo tipo de parámetro es `Object^`. En teoría, una conversión implícita nunca debe producir una excepción en tiempo de ejecución; si el compilador no puede realizar una conversión implícita, genera un error en tiempo de compilación.  
  
 [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] es una abstracción sobre COM, que usa códigos de error HRESULT en lugar de excepciones. En general, [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) indica un error COM de bajo nivel de E\_NOINTERFACE.  
  
## static\_cast  
 `static_cast` se comprueba en tiempo de compilación para determinar si hay una relación de herencia entre los dos tipos. La conversión produce un error del compilador si los tipos no están relacionados.  
  
 `static_cast` en una clase ref también provoca la realización de una comprobación en tiempo de ejecución. Un operador `static_cast` en una clase de referencia puede superar la comprobación en tiempo de compilación pero no en tiempo de ejecución. En este caso se produce una excepción `Platform::InvalidCastException`. En general, no es necesario controlar estas excepciones porque casi siempre indican errores de programación que puedes eliminar durante las fases de desarrollo y pruebas.  
  
 Utiliza `static_cast` si el código declara explícitamente una relación entre los dos tipos, y por lo tanto, estás seguro de que la conversión se realizará correctamente.  
  
```  
interface class A{}; public ref class Class1 sealed : A { }; ... A^ obj = ref new Class1(); // Class1 is an A // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed. Class1^ c = static_cast<Class1^>(obj);  
  
```  
  
## safe\_cast  
 El operador `safe_cast` forma parte de [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)]. Realiza una comprobación de tipo en tiempo de ejecución y produce una excepción `Platform::InvalidCastException` si se produce un error en la conversión. Usa `safe_cast` cuando un error en tiempo de ejecución indique una condición excepcional. El propósito principal de `safe_cast` es ayudar a identificar errores de programación durante las fases de desarrollo y pruebas en el punto donde aparecen. No tienes que controlar la excepción porque la propia excepción no controlada identifica el punto de error.  
  
 Utiliza safe\_cast si el código no declara la relación pero estás seguro de que la conversión se va a realizar correctamente.  
  
```  
  
// A and B are not related interface class A{}; interface class B{}; public ref class Class1 sealed : A, B { }; ... A^ obj = ref new Class1(); // You know that obj’s backing type implements A and B, but // the compiler can’t tell this by comparing A and B. The run-time type check succeeds. B^ obj2 = safe_cast<B^>(obj);  
  
```  
  
## dynamic\_cast  
 Usa `dynamic_cast` cuando conviertas un objeto \(más concretamente, '^'\) a un tipo más derivado, creas que el objeto de destino puede ser a veces `nullptr` o se pueda producir un error en la conversión y desees controlar esa condición como una ruta de acceso de código normal en lugar de como una excepción. Por ejemplo, en la plantilla de proyecto **Aplicación vacía de la Tienda Windows**, el método `OnLaunched` de `app.xamp.cpp` usa `dynamic_cast` para comprobar si la ventana de la aplicación tiene contenido. No es un error si no tiene contenido; es una condición esperada.`Windows::Current::Content` es `Windows::UI::XAML::UIElement` y la conversión es a `Windows::UI.XAML::Controls::Frame`, que es un tipo más derivado en la jerarquía de herencia.  
  
```  
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ args) { auto rootFrame = dynamic_cast<Frame^>(Window::Current->Content); // Do not repeat app initialization when the window already has content, // just ensure that the window is active if (rootFrame == nullptr) { // Create a Frame to act as the navigation context and associate it with // a SuspensionManager key rootFrame = ref new Frame(); ...  
```  
  
 Otro uso de `dynamic_cast` es para sondear `Object^` con el fin de determinar si contiene un tipo de valor al que se le ha aplicado la conversión boxing. En este caso, intentas `dynamic_cast<Platform::Box>` o `dynamic_cast<Platform::IBox>`.  
  
 **dynamic\_cast y referencias de seguimiento \(%\)**  
  
 También puedes aplicar `dynamic_cast` a una referencia de seguimiento, pero en este caso la conversión se comporta como `safe_cast`. Produce una excepción `Platform::InvalidCastException` en el error porque una referencia de seguimiento no puede tener un valor de `nullptr`.  
  
## reinterpret\_cast  
 Te recomendamos que no utilices [reinterpret\_cast](../cpp/reinterpret-cast-operator.md) debido a que en este caso no se realiza una comprobación en tiempo de compilación ni una comprobación en tiempo de ejecución. En el peor de los casos, `reinterpret_cast` permite que los errores de programación pasen desapercibidos en tiempo de desarrollo y produce errores imperceptibles o catastróficos en el comportamiento del programa. Por tanto, recomendamos usar `reinterpret_cast` solo en esos casos raros en los que debes convertir entre tipos no relacionados y sabes que la conversión se realizará correctamente. Un ejemplo de uso poco frecuente es convertir un tipo de [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] a su tipo de ABI subyacente. Esto significa que estás tomando el control del recuento de referencias del objeto. Para ello, te recomendamos utilizar el puntero inteligente [ComPtr \(Clase\)](../windows/comptr-class.md). De lo contrario, debes llamar específicamente a Release en la interfaz. En el ejemplo siguiente se muestra cómo se puede convertir una clase ref en `IInspectable*`.  
  
```  
  
#include <wrl.h> using namespace Microsoft::WRL; auto winRtObject = ref new SomeWinRTType(); ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(obj2); ...  
  
```  
  
 Si usas `reinterpret_cast` para convertir de una interfaz de [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] a otra, haces que el objeto se libere dos veces. Por tanto, usa esta conversión solo cuando conviertas a una interfaz que no sea de [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)].  
  
 **Tipos de ABI.**  
  
-   Los tipos de ABI residen en encabezados en Windows SDK. Afortunadamente, los nombres de los encabezados coinciden con los de los espacios de nombres. Por ejemplo, `windows.storage.h`.  
  
-   Los tipos de ABI residen en un espacio de nombres ABI especial. Por ejemplo, `ABI::Windows::Storage::Streams::IBuffer*`.  
  
-   Las conversiones entre un tipo de interfaz de [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] y su tipo de ABI equivalente siempre son seguras. Es decir, de `IBuffer^` a `ABI::IBuffer*`.  
  
-   Una clase en tiempo de ejecución de [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] se debe convertir siempre a `IInspectable*` o a su interfaz predeterminada, si se conoce.  
  
-   Después de convertir a tipos de ABI, eres el propietario de la duración del tipo y debes seguir las reglas de COM. Recomendamos usar `WRL::ComPtr` para simplificar la administración de la duración de los punteros de ABI.  
  
 En la tabla siguiente se resumen los casos en los que es seguro utilizar `reinterpret_cast`. En todos ellos, la conversión es segura en ambas direcciones.  
  
|||  
|-|-|  
|HSTRING|String^|  
|HSTRING\*|String^\*|  
|IInspectable\*|Object^|  
|IInspectable\*\*|Object^\*|  
|IInspectable\-derived\-type\*|same\-interface\-from\-winmd^|  
|IInspectable\-derived\-type\*\*|same\-interface\-from\-winmd^\*|  
|IDefault\-interface\-of\-RuntimeClass\*|same\-RefClass\-from\-winmd^|  
|IDefault\-interface\-of\-RuntimeClass\*\*|same\-RefClass\-from\-winmd^\*|  
  
## Vea también  
 [Sistema de tipos](../cppcx/type-system-c-cx.md)   
 [Referencia del lenguaje Visual C\+\+](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)