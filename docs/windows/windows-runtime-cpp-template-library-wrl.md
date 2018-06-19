---
title: Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 40d2ecbcfcd4121727bfe34bf2ffd571722b8a68
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891628"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Biblioteca de plantillas de Windows Runtime C++ (WRL)
La biblioteca de plantillas de C++ de Windows Runtime (WRL) es una biblioteca de plantillas que proporciona una manera de bajo nivel de crear y usar componentes de Windows Runtime.

> [!NOTE]
> WRL ahora ha sido reemplazada por C + / WinRT, una proyección de 17 del lenguaje C++ estándar para Windows Runtime APIs. C++ / WinRT está disponible en el SDK de Windows 10 desde la versión 1803 en adelante. C++ / WinRT se implementa por completo en archivos de encabezado y diseñado para proporcionarle acceso de primera clase a la API de Windows modernas.

> Con C++ / WinRT, se puede utilizar y crear mediante cualquier compilador de 17 C ++ compatible con los estándares de Windows en tiempo de ejecución APIs. C++ / WinRT normalmente se comporta mejor y genera archivos binarios más pequeños que cualquier otra opción de idioma para el tiempo de ejecución de Windows. Se seguirá siendo compatible con C++ / CX y WRL, pero se recomienda encarecidamente que las nuevas aplicaciones utilizar C++ / WinRT. Para obtener más información, consulte [C++ / WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index).   
  
## <a name="benefits"></a>Ventajas  
 La biblioteca de plantillas de C++ de Windows en tiempo de ejecución permite más fácil implementar y consumir los componentes de modelo de objetos componentes (COM). Proporciona técnicas de mantenimiento como el recuento de referencias para administrar la duración de los objetos y probar los valores `HRESULT` para determinar si una operación se realizó correctamente o no. Para usar correctamente la biblioteca de plantillas de C++ de Windows en tiempo de ejecución, debe seguir detenidamente estas reglas y técnicas.  
  
 C++ / CX es una forma lenguaje de alto nivel para usar componentes de Windows en tiempo de ejecución. La biblioteca de plantillas de C++ de Windows en tiempo de ejecución tanto C++ / CX simplifican la escritura de código para el tiempo de ejecución de Windows mediante la realización automática de tareas de mantenimiento en su nombre.  
  
 La biblioteca de plantillas de C++ de Windows en tiempo de ejecución y C++ / CX ofrecen diversas ventajas. Estas son algunas razones que podrían usar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución en lugar de C++ / CX:  
  
-   Biblioteca de plantillas de C++ de Windows en tiempo de ejecución agrega poco nivel de abstracción sobre el Windows en tiempo de ejecución aplicación interfaz binaria (ABI), lo que le ofrece la capacidad de controlar el código subyacente para adquirir una mejor crear o utilizar Windows Runtime APIs.  
  
-   C++ / CX representa COM `HRESULT` valores como excepciones. Si ha heredado una base de código que usa COM, o uno que no usa excepciones, es posible que la biblioteca de plantillas de C++ de Windows en tiempo de ejecución es una forma más natural para trabajar con el tiempo de ejecución de Windows ya no es necesario utilizar excepciones.  
  
    > [!NOTE]
    >  La biblioteca de plantillas de C++ de Windows en tiempo de ejecución utiliza `HRESULT` valores y no produce excepciones. Además, la biblioteca de plantillas de C++ de Windows en tiempo de ejecución utiliza punteros inteligentes y el modelo RAII para garantizar que los objetos se destruyen correctamente cuando el código de aplicación produce una excepción. Para obtener más información sobre los punteros inteligentes y RAII, vea [punteros inteligentes](../cpp/smart-pointers-modern-cpp.md) y [recursos propios de objetos (RAII)](../cpp/objects-own-resources-raii.md).  
  
-   El propósito y el diseño de la biblioteca de plantillas de C++ de Windows en tiempo de ejecución está inspirado por la Active Template Library (ATL), que es un conjunto de clases de C++ basadas en plantillas que simplifica la programación de objetos COM. Porque la biblioteca de plantillas de C++ de Windows en tiempo de ejecución utiliza C++ estándar para encapsular el tiempo de ejecución de Windows, más fácilmente puede trasladar e interactuar con diversos componentes COM existentes escritos en ATL en el tiempo de ejecución de Windows. Si ya conoce ATL, es posible que la programación de la biblioteca de plantillas de C++ de Windows en tiempo de ejecución es más fácil.  
  
## <a name="getting-started"></a>Introducción  
 Aquí tiene algunos recursos que pueden ayudarle a trabajar con la biblioteca de plantillas de C++ de Windows en tiempo de ejecución inmediatamente.  
  
 [La biblioteca de Windows en tiempo de ejecución (WRL)](http://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)  
 En este vídeo de Channel 9, obtener más información acerca de cómo la biblioteca de plantillas de C++ de Windows en tiempo de ejecución ayuda a que escribir aplicaciones de la plataforma Universal de Windows (UWP) y cómo crear y utilizar componentes en tiempo de ejecución de Windows.  
  
 [Cómo: activar y usar un componente de tiempo de ejecución de Windows](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)  
 Muestra cómo utilizar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución para inicializar el Runtime de Windows y activar y usar un componente en tiempo de ejecución de Windows.  
  
 [Cómo: completar operaciones asincrónicas](../windows/how-to-complete-asynchronous-operations-using-wrl.md)  
 Muestra cómo utilizar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución para iniciar operaciones asincrónicas y realizar el trabajo cuando las operaciones se completan.  
  
 [Cómo: controlar eventos](../windows/how-to-handle-events-using-wrl.md)  
 Muestra cómo utilizar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución para suscribirse al y controlar los eventos de un objeto en tiempo de ejecución de Windows.  
  
 [Tutorial: Crear una aplicación de UWP mediante WRL y Media Foundation](../windows/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)  
 Obtenga información acerca de cómo crear una aplicación UWP que use [Microsoft Media Foundation](http://msdn.microsoft.com/library/windows/apps/ms694197).  
  
 [Cómo: crear un componente COM clásico](../windows/how-to-create-a-classic-com-component-using-wrl.md)  
 Muestra cómo utilizar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución para crear un componente COM básico y cómo registrar y utilizar el componente COM de una aplicación de escritorio.  
  
 [Procedimiento para crear instancias de componentes WRL directamente](../windows/how-to-instantiate-wrl-components-directly.md)  
 Obtenga información acerca de cómo utilizar el [Microsoft::WRL::Make](../windows/make-function.md) y [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) funciones para crear instancias de un componente desde el módulo que lo define.  
  
 [Procedimiento para usar winmdidl.exe y midlrt.exe para crear archivos .h desde metadatos de Windows](../windows/use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)  
 Muestra cómo utilizar componentes personalizados de Windows en tiempo de ejecución desde la WRL mediante la creación de un archivo IDL a partir de los metadatos .winmd.  
  
 [Tutorial: Conectar mediante tareas y solicitudes HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 Muestra cómo utilizar el [IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908) y [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71) interfaces junto con otras tareas para enviar solicitudes HTTP GET y POST a un servicio web en una aplicación de UWP.  
  
 [Ejemplo de optimizador de recorridos de mapas de Bing](http://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)  
 Usa el `HttpRequest` clase que se define en [Tutorial: conectar usando tareas y solicitudes HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) en el contexto de una aplicación UWP completa.  
  
 [Ejemplo de creación un componente DLL en tiempo de ejecución de Windows con C++](http://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)  
 Muestra cómo utilizar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución para crear un componente DLL en proceso y usarlo desde C++ / CX, JavaScript y C#.  
  
 [Ejemplo de juego de laberinto de DirectX](http://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)  
 Muestra cómo utilizar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución para administrar la vigencia de los componentes COM como DirectX y Media Foundation en el contexto de un completo juego en 3D.  
  
 [Enviar notificaciones del sistema de ejemplo de aplicaciones de escritorio](http://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)  
 Muestra cómo usar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución para trabajar con notificaciones del sistema desde una aplicación de escritorio.  
  
## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Biblioteca de plantillas C++ de Windows en tiempo de ejecución en comparación con ATL  
 Biblioteca de plantillas de C++ de Windows en tiempo de ejecución se parece a Active Template Library (ATL) porque se puede usar para crear rápidos objetos COM pequeños. Biblioteca de plantillas de C++ de Windows en tiempo de ejecución y ATL también comparten conceptos tales como definición de objetos en los módulos, registro explícito de interfaces y abra la creación de objetos mediante generadores. Es posible que se encuentra cómodo con la biblioteca de plantillas de C++ de Windows en tiempo de ejecución si está familiarizado con ATL.  
  
 Biblioteca de plantillas de C++ de Windows en tiempo de ejecución es compatible con las funcionalidades COM que es necesaria para aplicaciones UWP. Por consiguiente, y a diferencia de ATL, omite la compatibilidad directa para características COM como:  
  
-   agregación  
  
-   implementaciones estándar  
  
-   interfaces duales (`IDispatch`)  
  
-   interfaces de enumerador estándar  
  
-   puntos de conexión  
  
-   interfaces divisibles  
  
-   incrustación OLE  
  
-   Controles ActiveX  
  
-   COM+  
  
## <a name="concepts"></a>Conceptos  
 Biblioteca de plantillas de C++ de Windows en tiempo de ejecución proporciona tipos que representan algunos conceptos básicos. En las siguientes secciones se describen estos tipos.  
  
### <a name="comptr"></a>ComPtr  
 [ComPtr](../windows/comptr-class.md) es un *puntero inteligente* tipo que representa la interfaz especificada por el parámetro de plantilla. Utilice `ComPtr` para declarar una variable que pueda tener acceso a los miembros de un objeto que se derive de la interfaz. `ComPtr` mantiene automáticamente un recuento de referencias para el puntero de la interfaz subyacente y la libera cuando el recuento de referencias llega a cero.  
  
### <a name="runtimeclass"></a>RuntimeClass  
 [RuntimeClass](../windows/runtimeclass-class.md) representa una clase con instancias que hereda un conjunto de interfaces especificadas. Un `RuntimeClass` objeto puede proporcionar una combinación de compatibilidad para una o varias interfaces de Windows en tiempo de ejecución COM o una referencia débil a un componente.  
  
### <a name="module"></a>Module  
 [Módulo](../windows/module-class.md) representa una colección de objetos relacionados. Un objeto `Module` administra los generadores de clases, que crean objetos, y el registro, que habilita otras aplicaciones para utilizar un objeto.  
  
### <a name="callback"></a>Callback  
 El [devolución de llamada](../windows/callback-function-windows-runtime-cpp-template-library.md) función crea un objeto cuya función miembro es un controlador de eventos (un método de devolución de llamada). Utilice la función `Callback` para escribir operaciones asincrónicas.  
  
### <a name="eventsource"></a>EventSource  
 [EventSource](../windows/eventsource-class.md) se utiliza para administrar *delegar* controladores de eventos. Usar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución para implementar un delegado y utilizar `EventSource` para agregar, quitar o invocar a delegados.  
  
### <a name="asyncbase"></a>AsyncBase  
 [AsyncBase](../windows/asyncbase-class.md) proporciona métodos virtuales que representan el modelo de programación asincrónico de Windows en tiempo de ejecución. Invalide los miembros de esta clase para crear una clase personalizada que pueda iniciar, detener o comprobar el progreso de una operación asincrónica.  
  
### <a name="ftmbase"></a>FtmBase  
 [FtmBase](../windows/ftmbase-class.md) representa un objeto de contador de referencias de subprocesamiento libre. `FtmBase` crea una tabla de interfaz global (GIT) y ayuda a administrar los objetos proxy y de cálculo de referencias.  
  
### <a name="weakref"></a>WeakRef  
 [WeakRef](../windows/weakref-class.md) es un tipo de puntero inteligente que representa un *referencia débil*, que hace referencia a un objeto que puede ser o no accesible. Un `WeakRef` objeto se puede usar solo el tiempo de ejecución de Windows y no COM clásico.  
  
 Un objeto `WeakRef` normalmente representa un objeto cuya existencia se controla mediante una aplicación o un subproceso externo. Por ejemplo, un objeto `WeakRef` puede hacer referencia a un objeto de archivo. Cuando se abre el archivo, `WeakRef` es válido y se puede tener acceso al archivo de referencia. Pero cuando se cierra el archivo, `WeakRef` no es válido y no se tiene acceso al archivo.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|||  
|-|-|  
|[API clave por categoría](../windows/key-wrl-apis-by-category.md)|Destaca los tipos, funciones y macros de biblioteca de plantillas de C++ de Windows en tiempo de ejecución principal.|  
|[Referencia](../windows/wrl-reference.md)|Contiene información de referencia de la biblioteca de plantillas de C++ de Windows en tiempo de ejecución.|  
|[Referencia rápida (en tiempo de ejecución de Windows y Visual C++)](http://go.microsoft.com/fwlink/p/?linkid=229180)|Describe brevemente C++ / características CX que admiten el tiempo de ejecución de Windows.|  
|[Utilizar componentes de Windows en tiempo de ejecución en Visual C++](http://go.microsoft.com/fwlink/p/?linkid=229155)|Muestra cómo utilizar C++ / CX para crear un componente básico de Windows en tiempo de ejecución.|