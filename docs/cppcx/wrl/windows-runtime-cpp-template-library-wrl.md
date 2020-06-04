---
title: Biblioteca de plantillas de Windows Runtime C++ (WRL)
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
ms.openlocfilehash: 41b8b45f89e94b8de2ddcb9c87bfd72122db8e1a
ms.sourcegitcommit: 27d9db019f6d84c94de9e6aff0170d918cee6738
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "75676943"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Biblioteca de plantillas de Windows Runtime C++ (WRL)

La biblioteca de plantillas de C++ de Windows Runtime (WRL) es una biblioteca de plantillas que proporciona una manera de bajo nivel de crear y usar componentes de Windows Runtime.

> [!NOTE]
> WRL se ha sustituido por C++/WinRT, una proyección de lenguaje c++ 17 estándar para api de Windows Runtime. C++/WinRT está disponible en el SDK de Windows 10 de la versión 1803 en adelante. C++/WinRT se implementa completamente en los archivos de encabezado y está diseñado para proporcionar acceso de primera clase a la API moderna de Windows.
>
> Con C++/WinRT, puede consumir y crear Windows Runtime API con cualquier compilador de c++ 17 compatible con los estándares. C++ / c++ / WinRT normalmente funciona mejor y genera archivos binarios más pequeños que ninguna otra opción de idioma para el tiempo de ejecución de Windows. Seguiremos admitiendo C++/CX y WRL, pero recomendamos encarecidamente que las nuevas aplicaciones usen C++/WinRT. Para obtener más información, consulte [C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index).

## <a name="benefits"></a>Ventajas

La biblioteca C++ de plantillas de Windows Runtime permite implementar y consumir componentes del modelo de objetos componentes (com) más fácilmente. Proporciona técnicas de mantenimiento como el recuento de referencias para administrar la duración de los objetos y probar los valores HRESULT para determinar si una operación se realizó correctamente o no. Para usar correctamente la biblioteca C++ de plantillas de Windows Runtime, debe seguir detenidamente estas reglas y técnicas.

C++/CX es una forma de alto nivel basada en el lenguaje de usar Windows Runtime componentes. Tanto la biblioteca C++ de plantillas de C++Windows Runtime como/CX simplifican la escritura de código para la Windows Runtime mediante la realización automática de tareas de mantenimiento en su nombre.

La biblioteca C++ de plantillas de C++Windows Runtime y/CX proporcionan diferentes ventajas. Estas son algunas de las razones por las que podría querer C++ usar el Windows Runtime biblioteca de C++plantillas en lugar de/CX:

- Windows Runtime C++ biblioteca de plantillas agrega poca abstracción sobre la Windows Runtime la interfaz binaria de aplicaciones (ABI), lo que le ofrece la posibilidad de controlar el código subyacente para crear o usar Windows Runtime API mejor.

- C++/CX representa los valores HRESULT de COM como excepciones. Si ha heredado una base de código que usa COM, o una que no usa excepciones, puede que la biblioteca de C++ plantillas de Windows Runtime sea una forma más natural de trabajar con la Windows Runtime porque no tiene que utilizar excepciones.

   > [!NOTE]
   > La biblioteca C++ de plantillas de Windows Runtime usa Valores HRESULT y no inicia excepciones. Además, la biblioteca de C++ plantillas de Windows Runtime utiliza punteros inteligentes y el patrón RAII para ayudar a garantizar que los objetos se destruyen correctamente cuando el código de la aplicación produce una excepción. Para obtener más información sobre los punteros inteligentes y RAII, vea [punteros inteligentes](../../cpp/smart-pointers-modern-cpp.md) y [objetos propios (RAII)](../../cpp/objects-own-resources-raii.md).

- El propósito y el diseño de la C++ biblioteca de plantillas Windows Runtime está inspirado en el Active Template Library (ATL), que es un conjunto de clases C++ basadas en plantillas que simplifican la programación de objetos com. Dado que C++ Windows Runtime biblioteca de plantillas C++ utiliza el estándar para encapsular el Windows Runtime, puede portar más fácilmente e interactuar con muchos componentes com existentes escritos en ATL en la Windows Runtime. Si ya conoce ATL, es posible que descubra que Windows Runtime C++ la programación de la biblioteca de plantillas es más fácil.

## <a name="getting-started"></a>Introducción

A continuación se muestran algunos recursos que pueden ayudarle a trabajar con C++ la biblioteca de plantillas de Windows Runtime inmediatamente.

[Biblioteca de Windows Runtime (WRL)](https://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)<br/>
En este vídeo de Channel 9, obtenga más información sobre cómo C++ Windows Runtime biblioteca de plantillas le ayuda a escribir aplicaciones plataforma universal de Windows (UWP) y cómo crear y consumir componentes Windows Runtime.

[Cómo: activar y usar un componente de Windows Runtime](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)<br/>
Muestra cómo usar la biblioteca de C++ plantillas de Windows Runtime para inicializar el Windows Runtime y activar y utilizar un componente de Windows Runtime.

[Cómo: completar operaciones asincrónicas](how-to-complete-asynchronous-operations-using-wrl.md)<br/>
Muestra cómo usar la biblioteca de C++ plantillas de Windows Runtime para iniciar operaciones asincrónicas y realizar el trabajo cuando se completan las operaciones.

[Cómo: controlar eventos](how-to-handle-events-using-wrl.md)<br/>
Muestra cómo utilizar la biblioteca de C++ plantillas de Windows Runtime para suscribirse a los eventos de un objeto Windows Runtime y controlarlos.

[Tutorial: Crear una aplicación de UWP mediante WRL y Media Foundation](walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)<br/>
Obtenga información sobre cómo crear una aplicación para UWP que use [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk).

[Cómo: crear un componente COM clásico](how-to-create-a-classic-com-component-using-wrl.md)<br/>
Muestra cómo usar la biblioteca de C++ plantillas de Windows Runtime para crear un componente com básico y una forma básica de registrar y utilizar el componente com de una aplicación de escritorio.

[Procedimiento para crear instancias de componentes WRL directamente](how-to-instantiate-wrl-components-directly.md)<br/>
Obtenga información sobre cómo utilizar las funciones [Microsoft::WRL::Make](make-function.md) y [Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md) para crear instancias de un componente a partir del módulo que lo define.

[Procedimiento para usar winmdidl.exe y midlrt.exe para crear archivos .h desde metadatos de Windows](use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)<br/>
Muestra cómo utilizar componentes personalizados de Windows en tiempo de ejecución desde la WRL mediante la creación de un archivo IDL a partir de los metadatos .winmd.

[Tutorial: Conectar mediante tareas y solicitudes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Muestra cómo utilizar las interfaces [IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2) e [IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback) junto con las tareas para enviar solicitudes HTTP GET y post a un servicio Web en una aplicación de UWP.

[Ejemplo del optimizador de recorridos de mapas de Bing](https://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)<br/>
Usa la clase `HttpRequest` que se define en [Tutorial: conectar usando tareas y solicitudes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) en el contexto de una aplicación UWP completa.

[Crear un componente DLL de Windows Runtime C++ con el ejemplo](https://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)<br/>
Muestra cómo usar el Windows Runtime C++ biblioteca de plantillas para crear un componente dll en proceso y consumirlo desde C++/CX, JavaScript y. C#

[Ejemplo de juego Marble Maze de DirectX](https://docs.microsoft.com/samples/microsoft/windows-appsample-marble-maze/directx-marble-maze-game-sample/)<br/>
Muestra cómo usar la biblioteca de C++ plantillas de Windows Runtime para administrar la duración de los componentes com como DirectX y Media Foundation en el contexto de un juego 3D completo.

[Ejemplo de envío de notificaciones del sistema de aplicaciones de escritorio](https://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)<br/>
Muestra cómo usar la biblioteca de C++ plantillas de Windows Runtime para trabajar con notificaciones del sistema desde una aplicación de escritorio.

## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Windows Runtime C++ biblioteca de plantillas en comparación con ATL

Windows Runtime C++ biblioteca de plantillas es similar a la Active Template Library (ATL) porque se puede utilizar para crear objetos com pequeños y rápidos. Windows Runtime C++ biblioteca de plantillas y ATL también comparten conceptos como la definición de objetos en módulos, el registro explícito de interfaces y la creación de objetos mediante generadores. Es posible que se sienta cómodo C++ con Windows Runtime biblioteca de plantillas si está familiarizado con ATL.

Windows Runtime C++ biblioteca de plantillas admite la funcionalidad de com que se requiere para las aplicaciones UWP. Por consiguiente, y a diferencia de ATL, omite la compatibilidad directa para características COM como:

- agregación

- implementaciones estándar

- interfaces duales (`IDispatch`)

- interfaces de enumerador estándar

- puntos de conexión

- interfaces divisibles

- incrustación OLE

- Controles ActiveX

- COM+

## <a name="concepts"></a>Conceptos de

Windows Runtime C++ biblioteca de plantillas proporciona tipos que representan algunos conceptos básicos. En las siguientes secciones se describen estos tipos.

### <a name="comptr"></a>ComPtr

[ComPtr](comptr-class.md) es un tipo de *puntero inteligente* que representa la interfaz especificada por el parámetro de plantilla. Utilice `ComPtr` para declarar una variable que pueda tener acceso a los miembros de un objeto que se derive de la interfaz. `ComPtr` mantiene automáticamente un recuento de referencias para el puntero de la interfaz subyacente y la libera cuando el recuento de referencias llega a cero.

### <a name="runtimeclass"></a>RuntimeClass

[RuntimeClass](runtimeclass-class.md) representa una clase de la que se ha creado una instancia que hereda un conjunto de interfaces especificadas. Un objeto `RuntimeClass` puede proporcionar una combinación de compatibilidad para una o varias interfaces COM Windows Runtime, o una referencia débil a un componente.

### <a name="module"></a>Module

[Module](module-class.md) representa una colección de objetos relacionados. Un objeto `Module` administra los generadores de clases, que crean objetos, y el registro, que habilita otras aplicaciones para utilizar un objeto.

### <a name="callback"></a>Devolución de llamada

La función [Callback](callback-function-wrl.md) crea un objeto cuya función miembro es un controlador de eventos (un método de devolución de llamada). Utilice la función `Callback` para escribir operaciones asincrónicas.

### <a name="eventsource"></a>EventSource

[EventSource](eventsource-class.md) se utiliza para administrar los controladores de eventos *delegados* . Utilice Windows Runtime C++ biblioteca de plantillas para implementar un delegado y use `EventSource` para agregar, quitar e invocar delegados.

### <a name="asyncbase"></a>AsyncBase

[AsyncBase](asyncbase-class.md) proporciona métodos virtuales que representan el Windows Runtime modelo de programación asincrónica. Invalide los miembros de esta clase para crear una clase personalizada que pueda iniciar, detener o comprobar el progreso de una operación asincrónica.

### <a name="ftmbase"></a>FtmBase

[FtmBase](ftmbase-class.md) representa un objeto de cálculo de referencias con subprocesamiento libre. `FtmBase` crea una tabla de interfaz global (GIT) y ayuda a administrar los objetos proxy y de cálculo de referencias.

### <a name="weakref"></a>WeakRef

[WeakRef](weakref-class.md) es un tipo puntero inteligente que representa una *referencia débil*y que hace referencia a un objeto al que se puede obtener o no acceso. Un objeto `WeakRef` solo se puede usar en el Windows Runtime y no en COM clásico.

Un objeto `WeakRef` normalmente representa un objeto cuya existencia se controla mediante una aplicación o un subproceso externo. Por ejemplo, un objeto `WeakRef` puede hacer referencia a un objeto de archivo. Cuando se abre el archivo, `WeakRef` es válido y se puede tener acceso al archivo de referencia. Pero cuando se cierra el archivo, `WeakRef` no es válido y no se tiene acceso al archivo.

## <a name="related-topics"></a>Temas relacionados

|||
|-|-|
|[API principales por categoría](key-wrl-apis-by-category.md)|Resalta los tipos C++ , funciones y macros principales de la biblioteca de plantillas de Windows Runtime.|
|[Referencia](wrl-reference.md)|Contiene información de referencia para la C++ biblioteca de plantillas de Windows Runtime.|
|[Referencia rápida (C++/CX)](../../cppcx/quick-reference-c-cx.md)|Describe brevemente las C++características de/CX que admiten el Windows Runtime.|
|[Usar componentes de Windows Runtime en VisualC++](/windows/uwp/winrt-components/walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp)|Muestra cómo usar C++/CX para crear un componente de Windows Runtime básico.|
