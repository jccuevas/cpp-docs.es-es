---
title: Excepciones (C++ / CX) | Documentos de Microsoft
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
caps.latest.revision: "22"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f578271823b0253dfa3defcb126bec251749a2dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-ccx"></a>Excepciones (C++/CX)

Control de errores en C++ / CX se basa en excepciones. En el nivel más fundamental, componentes de Windows Runtime informan de errores como valores HRESULT. En C++ / CX, estos valores se convierten en excepciones fuertemente tipadas que contienen un valor HRESULT y una descripción de cadena que puede tener acceso mediante programación.  Las excepciones se implementan como un objeto `ref class` que deriva de `Platform::Exception`.  El espacio de nombres `Platform` define clases de excepción distintas para los valores HRESULT más comunes; todos los demás valores se notifican mediante la clase `Platform::COMException` . Todas las clases de excepción tienen un campo [Exception::HResult](platform-exception-class.md#hresult) que puedes utilizar para recuperar el HRESULT original. También puede examinar la información de la pila de llamadas para código de usuario en el depurador, que puede ayudar a identificar el origen de la excepción, aunque se haya originado en código escrito en un lenguaje distinto de C++.  
  
## <a name="exceptions"></a>Excepciones  
 En el programa de C++ puede producir y detectar una excepción que proceda de una operación en tiempo de ejecución de Windows, una excepción que se deriva de `std::exception`, o un tipo definido por el usuario. Tiene que producir una excepción en tiempo de ejecución de Windows solo cuando cruce el límite de interfaz binaria (ABI) de la aplicación, por ejemplo, cuando el código que detecta tu excepción se escriba en JavaScript. Cuando una excepción de C++ que no son de Windows en tiempo de ejecución alcanza el límite de ABI, la excepción se convierte en un `Platform::FailureException` excepción, lo que representa un HRESULT E_FAIL. Para obtener más información acerca de la ABI, consulta [Creating Windows Runtime Components in C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md).  
  
 Puedes declarar una excepción [Platform::Exception](platform-exception-class.md) utilizando uno de los dos constructores que toman un parámetro HRESULT, o un parámetro HRESULT y un parámetro [Platform::String](platform-string-class.md)^ que se pueden pasar a través de la ABI a cualquier aplicación de la Tienda Windows que los controle. O bien puedes declarar una excepción utilizando una de las dos sobrecargas del [método Exception::CreateException](platform-exception-class.md#createexception) que toman un parámetro HRESULT, o un parámetro HRESULT y un parámetro `Platform::String^` .  
  
## <a name="standard-exceptions"></a>Excepciones estándar  
 C++ / CX admite un conjunto de excepciones estándar que representan errores típicos de HRESULT. Cada excepción estándar deriva de [Platform::COMException](platform-comexception-class.md), que a su vez deriva de `Platform::Exception`. Cuando produces una excepción en el límite de ABI, debes producir una de las excepciones estándar.  

 No puedes derivar tu propio tipo de excepción de `Platform::Exception`. Para producir una excepción personalizada, debes utilizar un HRESULT definido por el usuario para construir un objeto `COMException` .  
  
 En la tabla siguiente se enumeran las excepciones estándar.  
  
|nombre|HRESULT subyacente|Descripción|  
|----------|------------------------|-----------------|  
|COMException|*hresult definido por el usuario*|Se produce cuando se devuelve un HRESULT no reconocido de una llamada al método COM.|  
|AccessDeniedException|E_ACCESSDENIED|Se produce cuando se deniega el acceso a un recurso o a una característica.|  
|ChangedStateException|E_CHANGED_STATE|Se produce cuando los métodos de un iterador de colección o de una vista de colección se invocan después de que la colección principal haya cambiado, invalidando de este modo los resultados del método.|  
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|Se produce cuando una clase COM no se ha registrado.|  
|DisconnectedException|RPC_E_DISCONNECTED|Se produce cuando un objeto se desconecta de sus clientes.|  
|FailureException|E_FAIL|Se produce cuando una operación no es correcta.|  
|InvalidArgumentException|E_INVALIDARG|Se produce cuando uno de los argumentos que se proporcionan a un método no es válido.|  
|InvalidCastException|E_NOINTERFACE|Se produce cuando un tipo no puede convertirse a otro tipo.|  
|NotImplementedException|E_NOTIMPL|Se produce si un método de interfaz no se ha implementado en una clase.|  
|NullReferenceException|E_POINTER|Se produce cuando se intenta desreferenciar una referencia de un objeto null.|  
|ObjectDisposedException|RO_E_CLOSED|Se produce cuando se realiza una operación en un objeto desechado.|  
|OperationCanceledException|E_ABORT|Se produce cuando se anula una operación.|  
|OutOfBoundsException|E_BOUNDS|Se produce cuando una operación intenta tener acceso a datos que están fuera del intervalo válido.|  
|OutOfMemoryException|E_OUTOFMEMORY|Se produce cuando la memoria es insuficiente para completar la operación.|  
|WrongThreadException|RPC_E_WRONG_THREAD|Se produce cuando un subproceso llama mediante un puntero de interfaz que es para un objeto proxy que no pertenece al contenedor del subproceso.|  
  
## <a name="hresult-and-message-properties"></a>Propiedades HResult y Message  
 Todas las excepciones tienen una propiedad [HResult](platform-comexception-class.md#hresult) y una propiedad [Message](platform-comexception-class.md#message) . La propiedad [Exception::HResult](platform-exception-class.md#hresult) obtiene el valor HRESULT numérico subyacente de la excepción. La propiedad [Exception::Message](platform-exception-class.md#message) obtiene la cadena proporcionada por el sistema que describe la excepción. En Windows 8, el mensaje solo está disponible en el depurador y es de solo lectura. Esto significa que no puedes cambiarlo cuando vuelvas a producir la excepción. En Windows 8.1, puedes tener acceso a la cadena de mensaje mediante programación y proporcionar un nuevo mensaje si vuelves a producir la excepción. En el depurador hay disponible una mejor información de la pila de llamadas, incluidas pilas de llamadas para llamadas de método asincrónico.  
  
### <a name="examples"></a>Ejemplos  
 Este ejemplo muestra cómo producir una excepción en tiempo de ejecución de Windows para operaciones sincrónicas:  
  
 [!code-cpp[cx_exceptions#01](codesnippet/CPP/exceptiontest/class1.cpp#01)]  
  
 En el ejemplo siguiente se muestra cómo detectar la excepción.  
  
 [!code-cpp[cx_exceptions#02](codesnippet/CPP/exceptiontest/class1.cpp#02)]  
  
 Para detectar las excepciones que se producen durante una operación asincrónica, debes utilizar la clase de tarea y agregar una continuación de control de errores. La continuación de control de errores vuelve a calcular las referencias de las excepciones que se producen en otros subprocesos al subproceso que realiza la llamada para poder controlar todas las excepciones posibles en solo un punto de tu código. Para más información, vea [Programación asincrónica en C++](http://msdn.microsoft.com/library/windows/apps/Hh780559.aspx).  
  
## <a name="unhandlederrordetected-event"></a>Evento UnhandledErrorDetected  
 En Windows 8.1, puede suscribirse a la [unhandlederrordetected](http://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.coreapplication.unhandlederrordetected.aspx) evento estático, que proporciona acceso a los errores no controlados que va a poner el proceso. Independientemente de dónde se originó el error, llega a este controlador como un objeto [Windows::ApplicationModel::Core::UnhandledError](http://msdnstage.redmond.corp.microsoft.com/library/windows/apps/windows.applicationmodel.core.unhandlederror.aspx) que se pasa con los argumentos del evento. Cuando llamas a `Propagate` en el objeto, se crea y se produce una excepción `Platform::*Exception` del tipo correspondiente al código de error. En los bloques catch, puedes guardar el estado del usuario si es necesario y, a continuación, permitir que termine el proceso llamando a `throw`o realizar alguna acción para devolver el programa a un estado conocido. En el ejemplo siguiente se muestra el patrón básico:  
  
```  
  
// In app.xaml.h:  
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);  
  
// In app.xaml.cpp  
  
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
 C++ / CX no usa el `finally` cláusula.  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje de Visual C++](visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](namespaces-reference-c-cx.md)