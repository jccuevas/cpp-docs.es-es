---
title: Biblioteca de plantillas de Windows Runtime C++ (WRL)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
ms.openlocfilehash: 484718ee044b752c381d54b471a33e58ca470d80
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520665"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Biblioteca de plantillas de Windows Runtime C++ (WRL)

La biblioteca de plantillas de C++ de Windows Runtime (WRL) es una biblioteca de plantillas que proporciona una manera de bajo nivel de crear y usar componentes de Windows Runtime.

> [!NOTE]
> WRL ahora es reemplazada por C / c++ / WinRT, una proyección de 17 del lenguaje C ++ estándar para Windows Runtime APIs. C++ / c++ / WinRT está disponible en el SDK de Windows 10 desde la versión 1803 en adelante. C++ / c++ / WinRT se implementa completamente en archivos de encabezado y ha diseñado para proporcionar acceso de primera clase a la API de Windows moderna.
>
> Con C / c++ / WinRT, puede consumir y crear con cualquier compilador de 17 C ++ conforme a los estándares de Windows en tiempo de ejecución APIs. C++ / c++ / WinRT normalmente funcione mejor y genera archivos binarios más pequeños que ninguna otra opción de idioma para el tiempo de ejecución de Windows. Se seguirá admitiendo C++ / c++ / CX y WRL, pero se recomienda encarecidamente que utilicen las nuevas aplicaciones C++ / c++ / WinRT. Para obtener más información, consulte [C++ / c++ / WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index).

## <a name="benefits"></a>Ventajas

La biblioteca de plantillas C++ de Windows en tiempo de ejecución le permite implementar y consumir los componentes del modelo de objetos componentes (COM) más fácilmente. Proporciona técnicas de mantenimiento como recuento de referencias para administrar la vigencia de objetos y probar los valores HRESULT para determinar si una operación se realizó correctamente o no. Para usar correctamente la biblioteca de plantillas C++ de Windows en tiempo de ejecución, debe seguir detenidamente estas reglas y técnicas.

C++ / c++ / CX es una manera de alto nivel, en función de lenguaje a usar los componentes de Windows en tiempo de ejecución. Tanto la biblioteca de plantillas C++ de Windows en tiempo de ejecución y C++ / c++ / CX simplifican la escritura de código para el tiempo de ejecución de Windows por automáticamente tareas de mantenimiento en su nombre.

La biblioteca de plantillas C++ de Windows en tiempo de ejecución y C++ / c++ / CX ofrecen diversas ventajas. Estos son algunos motivos que desea usar la biblioteca de plantillas C++ de Windows en tiempo de ejecución en lugar de C++ / c++ / CX:

- Biblioteca de plantillas C++ de Windows en tiempo de ejecución agrega poco nivel de abstracción sobre el Windows en tiempo de ejecución binaria de aplicación interfaz (ABI), lo que le ofrece la capacidad de controlar el código subyacente para adquirir una mejor crear o usar APIs de Windows Runtime.

- C++ / c++ / CX representa los valores HRESULT de COM como excepciones. Si ha heredado una base de código que usa COM, o uno que no usa excepciones, es posible que la biblioteca de plantillas C++ de Windows en tiempo de ejecución es una manera más natural para trabajar con el tiempo de ejecución de Windows ya no es necesario utilizar excepciones.

   > [!NOTE]
   > La biblioteca de plantillas C++ de Windows en tiempo de ejecución utiliza los valores HRESULT y no inicia excepciones. Además, la biblioteca de plantillas C++ de Windows en tiempo de ejecución utiliza punteros inteligentes y el modelo RAII para ayudar a garantizar que los objetos se destruyen correctamente cuando el código de aplicación produce una excepción. Para obtener más información sobre los punteros inteligentes y RAII, vea [punteros inteligentes](../cpp/smart-pointers-modern-cpp.md) y [recursos propios de los objetos (RAII)](../cpp/objects-own-resources-raii.md).

- El propósito y el diseño de la biblioteca de plantillas C++ de Windows en tiempo de ejecución está inspirado por la Active Template Library (ATL), que es un conjunto de clases C++ basadas en plantillas que simplifican la programación de objetos COM. Como biblioteca de plantillas C++ de Windows en tiempo de ejecución utiliza el estándar de C++ para ajustar el tiempo de ejecución de Windows, puede puerto más fácilmente e interactuar con muchos componentes COM existentes escritos en ATL para el tiempo de ejecución de Windows. Si ya conoce ATL, es posible que la programación de la biblioteca de plantillas C++ de Windows en tiempo de ejecución es más fácil.

## <a name="getting-started"></a>Introducción

Estos son algunos recursos que pueden ayudarle a trabajar inmediatamente con la biblioteca de plantillas C++ de Windows en tiempo de ejecución.

[La biblioteca de Windows en tiempo de ejecución (WRL)](https://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)<br/>
En este vídeo de Channel 9, obtenga más información sobre cómo la biblioteca de plantillas C++ de Windows en tiempo de ejecución ayuda a que escribir aplicaciones de plataforma Universal de Windows (UWP) y cómo crear y consumir los componentes de Windows en tiempo de ejecución.

[Cómo: activar y usar un componente de tiempo de ejecución de Windows](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)<br/>
Se muestra cómo usar la biblioteca de plantillas C++ de Windows en tiempo de ejecución para inicializar el tiempo de ejecución de Windows y activar y usar un componente de Windows en tiempo de ejecución.

[Cómo: completar operaciones asincrónicas](../windows/how-to-complete-asynchronous-operations-using-wrl.md)<br/>
Se muestra cómo usar la biblioteca de plantillas C++ de Windows en tiempo de ejecución para iniciar operaciones asincrónicas y realizar el trabajo cuando las operaciones se completan.

[Cómo: controlar eventos](../windows/how-to-handle-events-using-wrl.md)<br/>
Se muestra cómo usar la biblioteca de plantillas C++ de Windows en tiempo de ejecución para suscribirse y controlar los eventos de un objeto en tiempo de ejecución de Windows.

[Tutorial: Crear una aplicación de UWP mediante WRL y Media Foundation](../windows/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)<br/>
Obtenga información sobre cómo crear una aplicación UWP que usa [Microsoft Media Foundation](/windows/desktop/medfound/microsoft-media-foundation-sdk).

[Cómo: crear un componente COM clásico](../windows/how-to-create-a-classic-com-component-using-wrl.md)<br/>
Se muestra cómo usar la biblioteca de plantillas C++ de Windows en tiempo de ejecución para crear un componente COM básico y una forma básica de cómo registrar y utilizar el componente COM de una aplicación de escritorio.

[Procedimiento para crear instancias de componentes WRL directamente](../windows/how-to-instantiate-wrl-components-directly.md)<br/>
Obtenga información sobre cómo utilizar las funciones [Microsoft::WRL::Make](../windows/make-function.md) y [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) para crear instancias de un componente a partir del módulo que lo define.

[Procedimiento para usar winmdidl.exe y midlrt.exe para crear archivos .h desde metadatos de Windows](../windows/use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)<br/>
Muestra cómo utilizar componentes personalizados de Windows en tiempo de ejecución desde la WRL mediante la creación de un archivo IDL a partir de los metadatos .winmd.

[Tutorial: Conectar mediante tareas y solicitudes HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Se muestra cómo usar el [IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2) y [IXMLHTTPRequest2Callback](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2callback) interfaces junto con las tareas para enviar solicitudes HTTP GET y POST a un servicio web en una aplicación para UWP.

[Ejemplo de Bing Maps Trip Optimizer](https://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)<br/>
Usa el `HttpRequest` clase que se define en [Tutorial: conectar usando tareas y solicitudes HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) en el contexto de una aplicación UWP completa.

[Creación de un componente DLL en tiempo de ejecución de Windows con el ejemplo de C++](https://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)<br/>
Muestra cómo usar la biblioteca de plantillas C++ de Windows en tiempo de ejecución para crear un componente DLL en proceso y utilizarlo desde C++ / c++ / CX, JavaScript y C#.

[Ejemplo de juego marble maze con DirectX](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)<br/>
Muestra cómo usar la biblioteca de plantillas C++ de Windows en tiempo de ejecución para administrar la duración de los componentes de COM como DirectX y Media Foundation en el contexto de un completo juego en 3D.

[Cómo enviar notificaciones de ejemplo de aplicaciones de escritorio](https://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)<br/>
Muestra cómo usar la biblioteca de plantillas C++ de Windows en tiempo de ejecución para trabajar con notificaciones del sistema de una aplicación de escritorio.

## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Biblioteca de plantillas C++ de Windows en tiempo de ejecución y ATL

Biblioteca de plantillas C++ de Windows en tiempo de ejecución se parece a Active Template Library (ATL) porque se puede usar para crear rápidamente objetos COM pequeños. Biblioteca de plantillas C++ de Windows en tiempo de ejecución y ATL también comparten conceptos tales como definición de objetos en los módulos, registro explícito de interfaces y abra la creación de objetos mediante generadores. Es posible que cómodo con la biblioteca de plantillas C++ de Windows en tiempo de ejecución si está familiarizado con ATL.

Biblioteca de plantillas C++ de Windows en tiempo de ejecución es compatible con las funcionalidades COM que es necesaria para aplicaciones UWP. Por consiguiente, y a diferencia de ATL, omite la compatibilidad directa para características COM como:

- agregación

- implementaciones estándar

- interfaces duales (`IDispatch`)

- interfaces de enumerador estándar

- puntos de conexión

- interfaces divisibles

- incrustación OLE

- Controles ActiveX

- COM+

## <a name="concepts"></a>Conceptos

Biblioteca de plantillas C++ de Windows en tiempo de ejecución proporciona tipos que representan algunos conceptos básicos. En las siguientes secciones se describen estos tipos.

### <a name="comptr"></a>ComPtr

[ComPtr](../windows/comptr-class.md) es un tipo de *puntero inteligente* que representa la interfaz especificada por el parámetro de plantilla. Utilice `ComPtr` para declarar una variable que pueda tener acceso a los miembros de un objeto que se derive de la interfaz. `ComPtr` mantiene automáticamente un recuento de referencias para el puntero de la interfaz subyacente y la libera cuando el recuento de referencias llega a cero.

### <a name="runtimeclass"></a>RuntimeClass

[RuntimeClass](../windows/runtimeclass-class.md) representa una clase de la que se ha creado una instancia que hereda un conjunto de interfaces especificadas. Un `RuntimeClass` objeto puede proporcionar una combinación de la compatibilidad con una o varias interfaces de COM en tiempo de ejecución de Windows o una referencia débil a un componente.

### <a name="module"></a>Module

[Module](../windows/module-class.md) representa una colección de objetos relacionados. Un objeto `Module` administra los generadores de clases, que crean objetos, y el registro, que habilita otras aplicaciones para utilizar un objeto.

### <a name="callback"></a>Callback

La función [Callback](../windows/callback-function-windows-runtime-cpp-template-library.md) crea un objeto cuya función miembro es un controlador de eventos (un método de devolución de llamada). Utilice la función `Callback` para escribir operaciones asincrónicas.

### <a name="eventsource"></a>EventSource

[EventSource](../windows/eventsource-class.md) se utiliza para administrar los controladores de eventos *delegados* . Usar biblioteca de plantillas C++ de Windows en tiempo de ejecución para implementar un delegado y usar `EventSource` para agregar, quitar o invocar a delegados.

### <a name="asyncbase"></a>AsyncBase

[AsyncBase](../windows/asyncbase-class.md) proporciona los métodos virtuales que representan el modelo de programación asincrónico de Windows en tiempo de ejecución. Invalide los miembros de esta clase para crear una clase personalizada que pueda iniciar, detener o comprobar el progreso de una operación asincrónica.

### <a name="ftmbase"></a>FtmBase

[FtmBase](../windows/ftmbase-class.md) representa un objeto de cálculo de referencias con subprocesamiento libre. `FtmBase` crea una tabla de interfaz global (GIT) y ayuda a administrar los objetos proxy y de cálculo de referencias.

### <a name="weakref"></a>WeakRef

[WeakRef](../windows/weakref-class.md) es un tipo puntero inteligente que representa una *referencia débil*y que hace referencia a un objeto al que se puede obtener o no acceso. Un `WeakRef` objeto se puede usar solo el tiempo de ejecución de Windows y no COM clásico.

Un objeto `WeakRef` normalmente representa un objeto cuya existencia se controla mediante una aplicación o un subproceso externo. Por ejemplo, un objeto `WeakRef` puede hacer referencia a un objeto de archivo. Cuando se abre el archivo, `WeakRef` es válido y se puede tener acceso al archivo de referencia. Pero cuando se cierra el archivo, `WeakRef` no es válido y no se tiene acceso al archivo.

## <a name="related-topics"></a>Temas relacionados

|||
|-|-|
|[API clave por categoría](../windows/key-wrl-apis-by-category.md)|Se resaltan los tipos, funciones y macros de biblioteca de plantillas C++ de Windows en tiempo de ejecución principal.|
|[Referencia](../windows/wrl-reference.md)|Contiene información de referencia para la biblioteca de plantillas C++ de Windows en tiempo de ejecución.|
|[Referencia rápida (en tiempo de ejecución de Windows y Visual C++)](../cppcx/quick-reference-c-cx.md)|Describe brevemente el C + + / características CX que admiten el tiempo de ejecución de Windows.|
|[Usar los componentes de Windows en tiempo de ejecución en Visual C++](/windows/uwp/winrt-components/walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp)|Se muestra cómo usar C++ / c++ / CX para crear un componente básico de Windows en tiempo de ejecución.|
