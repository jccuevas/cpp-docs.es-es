---
title: "Excepciones (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
caps.latest.revision: 22
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 22
---
# Excepciones (C++/CX)
El control de errores en [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) se basa en excepciones. En el nivel más fundamental, los componentes de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] notifican errores como valores HRESULT. En [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)], estos valores se convierten en excepciones fuertemente tipadas que contienen un valor HRESULT y, en [!INCLUDE[win81](../cppcx/includes/win81-md.md)], una descripción de cadena a la que se puede tener acceso mediante programación.  Las excepciones se implementan como un objeto `ref class` que deriva de `Platform::Exception`.  El espacio de nombres `Platform` define clases de excepción distintas para los valores HRESULT más comunes; todos los demás valores se notifican mediante la clase `Platform::COMException`. Todas las clases de excepción tienen un campo [Exception::HResult Property](../cppcx/exception-hresult-property.md) que puedes utilizar para recuperar el HRESULT original. En [!INCLUDE[win81](../cppcx/includes/win81-md.md)], también puedes examinar en el depurador información de la pila de llamadas para código de usuario que puede ayudarte a localizar el origen inicial de la excepción, aunque se haya originado en código escrito en un lenguaje distinto de C\+\+.  
  
## Excepciones  
 En tu programa de C\+\+, puedes producir y detectar una excepción que proceda de una operación de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)], una excepción que se derive de `std::exception` o un tipo definido por el usuario. Tiene que producir una excepción de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] solo cuando cruce el límite de la interfaz binaria de aplicación \(ABI\); por ejemplo, cuando el código que detecta tu excepción se escriba en JavaScript. Cuando una excepción de C\+\+ que no es de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] alcanza el límite de la ABI, la excepción se traduce a una excepción `Platform::FailureException`, que representa un HRESULT E\_FAIL. Para obtener más información acerca de la ABI, consulta [Crear componentes de Windows en tiempo de ejecución en C\+\+](../Topic/Creating%20Windows%20Runtime%20Components%20in%20C++.md).  
  
 Puedes declarar una excepción [Platform::Exception](../cppcx/platform-exception-class.md) utilizando uno de los dos constructores que toman un parámetro HRESULT, o un parámetro HRESULT y un parámetro [Platform::String](../cppcx/platform-string-class.md)^ que se pueden pasar a través de la ABI a cualquier aplicación de la Tienda Windows que los controle. O bien puedes declarar una excepción utilizando una de las dos sobrecargas del [método Exception::CreateException](../cppcx/exception-createexception-method.md) que toman un parámetro HRESULT, o un parámetro HRESULT y un parámetro `Platform::String^`.  
  
## Excepciones estándar  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] admite un conjunto de excepciones estándar que representan errores típicos de HRESULT. Cada excepción estándar deriva de [Platform::COMException](../cppcx/platform-comexception-class.md), que a su vez deriva de `Platform::Exception`. Cuando produces una excepción en el límite de ABI, debes producir una de las excepciones estándar.  
  
 No puedes derivar tu propio tipo de excepción de `Platform::Exception`. Para producir una excepción personalizada, debes utilizar un HRESULT definido por el usuario para construir un objeto `COMException`.  
  
 En la tabla siguiente se enumeran las excepciones estándar.  
  
|Nombre|HRESULT subyacente|Descripción|  
|------------|------------------------|-----------------|  
|COMException|*hresult definido por el usuario*|Se produce cuando se devuelve un HRESULT no reconocido de una llamada al método COM.|  
|AccessDeniedException|E\_ACCESSDENIED|Se produce cuando se deniega el acceso a un recurso o a una característica.|  
|ChangedStateException|E\_CHANGED\_STATE|Se produce cuando los métodos de un iterador de colección o de una vista de colección se invocan después de que la colección principal haya cambiado, invalidando de este modo los resultados del método.|  
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|Se produce cuando una clase COM no se ha registrado.|  
|DisconnectedException|RPC\_E\_DISCONNECTED|Se produce cuando un objeto se desconecta de sus clientes.|  
|FailureException|E\_FAIL|Se produce cuando una operación no es correcta.|  
|InvalidArgumentException|E\_INVALIDARG|Se produce cuando uno de los argumentos que se proporcionan a un método no es válido.|  
|InvalidCastException|E\_NOINTERFACE|Se produce cuando un tipo no puede convertirse a otro tipo.|  
|NotImplementedException|E\_NOTIMPL|Se produce si un método de interfaz no se ha implementado en una clase.|  
|NullReferenceException|E\_POINTER|Se produce cuando se intenta desreferenciar una referencia de un objeto null.|  
|ObjectDisposedException|RO\_E\_CLOSED|Se produce cuando se realiza una operación en un objeto desechado.|  
|OperationCanceledException|E\_ABORT|Se produce cuando se anula una operación.|  
|OutOfBoundsException|E\_BOUNDS|Se produce cuando una operación intenta tener acceso a datos que están fuera del intervalo válido.|  
|OutOfMemoryException|E\_OUTOFMEMORY|Se produce cuando la memoria es insuficiente para completar la operación.|  
|WrongThreadException|RPC\_E\_WRONG\_THREAD|Se produce cuando un subproceso llama mediante un puntero de interfaz que es para un objeto proxy que no pertenece al contenedor del subproceso.|  
  
## Propiedades HResult y Message  
 Todas las excepciones tienen una propiedad [HResult](../cppcx/comexception-hresult-property.md) y una propiedad [Message](../cppcx/comexception-message-property.md). La propiedad [Exception::HResult](../cppcx/exception-hresult-property.md) obtiene el valor HRESULT numérico subyacente de la excepción. La propiedad [Exception::Message](../cppcx/exception-message-property.md) obtiene la cadena proporcionada por el sistema que describe la excepción. En [!INCLUDE[win8](../cppcx/includes/win8-md.md)], el mensaje solo está disponible en el depurador y es de solo lectura. Esto significa que no puedes cambiarlo cuando vuelvas a producir la excepción. En [!INCLUDE[win81](../cppcx/includes/win81-md.md)], puedes tener acceso a la cadena de mensaje mediante programación y proporcionar un nuevo mensaje si vuelves a producir la excepción. En el depurador hay disponible una mejor información de la pila de llamadas, incluidas pilas de llamadas para llamadas de método asincrónico.  
  
## Ejemplos  
 En este ejemplo se muestra cómo producir una excepción de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] para operaciones sincrónicas:  
  
 [!code-cpp[cx_exceptions#01](../snippets/cpp/VS_Snippets_Misc/cx_exceptions/cpp/class1.cpp#01)]  
  
 En el ejemplo siguiente se muestra cómo detectar la excepción.  
  
 [!code-cpp[cx_exceptions#02](../snippets/cpp/VS_Snippets_Misc/cx_exceptions/cpp/class1.cpp#02)]  
  
 Para detectar las excepciones que se producen durante una operación asincrónica, debes utilizar la clase de tarea y agregar una continuación de control de errores. La continuación de control de errores vuelve a calcular las referencias de las excepciones que se producen en otros subprocesos al subproceso que realiza la llamada para poder controlar todas las excepciones posibles en solo un punto de tu código. Para más información, vea [Programación asincrónica en C\+\+](http://msdn.microsoft.com/library/windows/apps/Hh780559.aspx).  
  
## Evento UnhandledErrorDetected  
 En [!INCLUDE[win81](../cppcx/includes/win81-md.md)], puedes suscribirte al evento estático [Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected](http://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.coreapplication.unhandlederrordetected.aspx), que proporciona acceso a errores no controlados que están a punto de impedir que el proceso se realice correctamente. Independientemente de dónde se originó el error, llega a este controlador como un objeto [Windows::ApplicationModel::Core::UnhandledError](http://msdnstage.redmond.corp.microsoft.com/library/windows/apps/windows.applicationmodel.core.unhandlederror.aspx) que se pasa con los argumentos del evento. Cuando llamas a `Propagate` en el objeto, se crea y se produce una excepción `Platform::*Exception` del tipo correspondiente al código de error. En los bloques catch, puedes guardar el estado del usuario si es necesario y, a continuación, permitir que termine el proceso llamando a `throw` o realizar alguna acción para devolver el programa a un estado conocido. En el ejemplo siguiente se muestra el patrón básico:  
  
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
  
## Comentarios  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] no utiliza la cláusula `finally`.  
  
## Vea también  
 [Referencia del lenguaje Visual C\+\+](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)