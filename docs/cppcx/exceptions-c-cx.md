---
title: Excepciones (C++/CX)
ms.date: 07/02/2019
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
ms.openlocfilehash: ade406dc5db6022978f83715555c425caef4375b
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740176"
---
# <a name="exceptions-ccx"></a>Excepciones (C++/CX)

El control de C++errores en/CX se basa en excepciones. En el nivel más fundamental, los componentes de Windows Runtime notifican errores como valores HRESULT. En C++/CX, estos valores se convierten en excepciones fuertemente tipadas que contienen un valor HRESULT y una descripción de cadena a la que se puede tener acceso mediante programación.  Las excepciones se implementan como un objeto `ref class` que deriva de `Platform::Exception`.  El espacio de nombres `Platform` define clases de excepción distintas para los valores HRESULT más comunes; todos los demás valores se notifican mediante la clase `Platform::COMException` . Todas las clases de excepción tienen un campo [Exception::HResult](platform-exception-class.md#hresult) que puedes utilizar para recuperar el HRESULT original. También puede examinar la información de la pila de llamadas del código de usuario en el depurador que puede ayudar a identificar el origen de la excepción, aunque se haya originado en código escrito en un lenguaje C++distinto de.

## <a name="exceptions"></a>Excepciones

En el C++ programa, puede producir y detectar una excepción que proceda de una operación Windows Runtime, una excepción que se derive de `std::exception`o un tipo definido por el usuario. Solo tiene que iniciar una excepción Windows Runtime cuando cruce el límite de la interfaz binaria de aplicación (ABI), por ejemplo, cuando el código que detecta la excepción se escribe en JavaScript. Cuando una excepción no Windows Runtime C++ alcanza el límite de la ABI, la excepción se traduce en `Platform::FailureException` una excepción, que representa un HRESULT E_FAIL. Para obtener más información acerca de la ABI, consulta [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Puede declarar una [plataforma:: Exception](platform-exception-class.md) utilizando uno de los dos constructores que toman un parámetro HRESULT, o un parámetro HRESULT y un parámetro [Platform:: String](platform-string-class.md)^ que se puede pasar a través de la ABI a cualquier Windows Runtime aplicación que lo controle. O bien puedes declarar una excepción utilizando una de las dos sobrecargas del [método Exception::CreateException](platform-exception-class.md#createexception) que toman un parámetro HRESULT, o un parámetro HRESULT y un parámetro `Platform::String^` .

## <a name="standard-exceptions"></a>Excepciones estándar

C++/CX admite un conjunto de excepciones estándar que representan errores típicos de HRESULT. Cada excepción estándar deriva de [Platform::COMException](platform-comexception-class.md), que a su vez deriva de `Platform::Exception`. Cuando produces una excepción en el límite de ABI, debes producir una de las excepciones estándar.

No puedes derivar tu propio tipo de excepción de `Platform::Exception`. Para producir una excepción personalizada, debes utilizar un HRESULT definido por el usuario para construir un objeto `COMException` .

En la tabla siguiente se enumeran las excepciones estándar.

|NOMBRE|HRESULT subyacente|DESCRIPCIÓN|
|----------|------------------------|-----------------|
|COMException|*hresult definido por el usuario*|Se produce cuando se devuelve un HRESULT no reconocido de una llamada al método COM.|
|AccessDeniedException|E\_ACCESSDENIED|Se produce cuando se deniega el acceso a un recurso o a una característica.|
|ChangedStateException|E\_CAMBIO\_DE ESTADO|Se produce cuando los métodos de un iterador de colección o de una vista de colección se invocan después de que la colección principal haya cambiado, invalidando de este modo los resultados del método.|
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|Se produce cuando una clase COM no se ha registrado.|
|DisconnectedException|RPC\_E\_DESCONECTADO|Se produce cuando un objeto se desconecta de sus clientes.|
|FailureException|E\_FAIL|Se produce cuando una operación no es correcta.|
|InvalidArgumentException|E\_INVALIDARG|Se produce cuando uno de los argumentos que se proporcionan a un método no es válido.|
|InvalidCastException|E\_NOINTERFACE|Se produce cuando un tipo no puede convertirse a otro tipo.|
|NotImplementedException|E\_NOTIMPL|Se produce si un método de interfaz no se ha implementado en una clase.|
|NullReferenceException|PUNTERO\_E|Se produce cuando se intenta desreferenciar una referencia de un objeto null.|
|ObjectDisposedException|RO\_E\_CERRADO|Se produce cuando se realiza una operación en un objeto desechado.|
|OperationCanceledException|E\_ANULAR|Se produce cuando se anula una operación.|
|OutOfBoundsException|ENLACES\_E|Se produce cuando una operación intenta tener acceso a datos que están fuera del intervalo válido.|
|OutOfMemoryException|E\_OUTOFMEMORY|Se produce cuando la memoria es insuficiente para completar la operación.|
|WrongThreadException|SUBPROCESO\_RPC\_E\_INCORRECTO|Se produce cuando un subproceso llama mediante un puntero de interfaz que es para un objeto proxy que no pertenece al contenedor del subproceso.|

## <a name="hresult-and-message-properties"></a>Propiedades HResult y Message

Todas las excepciones tienen una propiedad [HResult](platform-comexception-class.md#hresult) y una propiedad [Message](platform-comexception-class.md#message) . La propiedad [Exception::HResult](platform-exception-class.md#hresult) obtiene el valor HRESULT numérico subyacente de la excepción. La propiedad [Exception::Message](platform-exception-class.md#message) obtiene la cadena proporcionada por el sistema que describe la excepción. En Windows 8, el mensaje solo está disponible en el depurador y es de solo lectura. Esto significa que no puedes cambiarlo cuando vuelvas a producir la excepción. En Windows 8.1, puedes tener acceso a la cadena de mensaje mediante programación y proporcionar un nuevo mensaje si vuelves a producir la excepción. En el depurador hay disponible una mejor información de la pila de llamadas, incluidas pilas de llamadas para llamadas de método asincrónico.

### <a name="examples"></a>Ejemplos

En este ejemplo se muestra cómo iniciar una excepción Windows Runtime para las operaciones sincrónicas:

[!code-cpp[cx_exceptions#01](codesnippet/CPP/exceptiontest/class1.cpp#01)]

En el ejemplo siguiente se muestra cómo detectar la excepción.

[!code-cpp[cx_exceptions#02](codesnippet/CPP/exceptiontest/class1.cpp#02)]

Para detectar las excepciones que se producen durante una operación asincrónica, utilice la clase de tarea y agregue una continuación de control de errores. La continuación de control de errores vuelve a calcular las referencias de las excepciones que se producen en otros subprocesos al subproceso que realiza la llamada para poder controlar todas las excepciones posibles en solo un punto de tu código. Para más información, vea [Programación asincrónica en C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).

## <a name="unhandlederrordetected-event"></a>Evento UnhandledErrorDetected

En Windows 8.1 puede suscribirse al evento estático [Windows:: ApplicationModel:: Core:: CoreApplication:: UnhandledErrorDetected](/uwp/api/windows.applicationmodel.core.icoreapplicationunhandlederror.unhandlederrordetected) , que proporciona acceso a errores no controlados que están a punto de detener el proceso. Independientemente de dónde se originó el error, llega a este controlador como un objeto [Windows::ApplicationModel::Core::UnhandledError](/uwp/api/windows.applicationmodel.core.unhandlederror) que se pasa con los argumentos del evento. Cuando llamas a `Propagate` en el objeto, se crea y se produce una excepción `Platform::*Exception` del tipo correspondiente al código de error. En los bloques catch, puedes guardar el estado del usuario si es necesario y, a continuación, permitir que termine el proceso llamando a `throw`o realizar alguna acción para devolver el programa a un estado conocido. En el ejemplo siguiente se muestra el patrón básico:

En App. Xaml. h:

```cpp
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);
```

En App. Xaml. cpp:

```cpp
// Subscribe to the event, for example in the app class constructor:
Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected += ref new EventHandler<UnhandledErrorDetectedEventArgs^>(this, &App::OnUnhandledException);

// Event handler implementation:
void App::OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e)
{
    auto err = e->UnhandledError;

    if (!err->Handled) //Propagate has not been called on it yet.
{
    try
    {
        err->Propagate();
    }
    // Catch any specific exception types if you know how to handle them
    catch (AccessDeniedException^ ex)
    {
        // TODO: Log error and either take action to recover
        // or else re-throw exception to continue fail-fast
    }
}
```

### <a name="remarks"></a>Comentarios

C++/CX no utiliza la `finally` cláusula.

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++/CX](visual-c-language-reference-c-cx.md)<br/>
[Referencia de espacios de nombres](namespaces-reference-c-cx.md)
