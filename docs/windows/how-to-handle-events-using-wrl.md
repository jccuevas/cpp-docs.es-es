---
title: 'Cómo: controlar eventos mediante WRL | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eada53c74c967c4df093e094a611a726ef79d99d
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012539"
---
# <a name="how-to-handle-events-using-wrl"></a>Cómo: Controlar eventos mediante WRL
Este documento muestra cómo usar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución (WRL) para suscribirse y controlar los eventos de un objeto en tiempo de ejecución de Windows.  
  
 Para obtener un ejemplo más básico que crea una instancia de ese componente y recupera un valor de propiedad, vea [Cómo: activar y usar un componente de Windows en tiempo de ejecución](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).  
  
## <a name="subscribing-to-and-handling-events"></a>Suscribirse a y control de eventos  
 Los siguientes pasos inicio un `ABI::Windows::System::Threading::IDeviceWatcher` de objetos y usar controladores de eventos para supervisar el progreso. El `IDeviceWatcher` interfaz permite enumerar los dispositivos de forma asincrónica o en segundo plano y recibir una notificación cuando los dispositivos se agregado, quitados o cambiados. El [devolución de llamada](../windows/callback-function-windows-runtime-cpp-template-library.md) función es una parte importante de este ejemplo porque le permite especificar controladores de eventos que procesan los resultados de la operación en segundo plano. A continuación se muestra el ejemplo completo.  
  
> [!WARNING]
>  Aunque normalmente se usa la biblioteca de plantillas de C++ de Windows en tiempo de ejecución en una aplicación plataforma Universal de Windows, en este ejemplo se usa una aplicación de consola para ilustración. Las funciones como `wprintf_s` no están disponibles en una aplicación plataforma Universal de Windows. Para obtener más información sobre los tipos y funciones que puede usar en una aplicación plataforma Universal de Windows, consulte [funciones de CRT no admitidas en aplicaciones de la plataforma Universal de Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) y [Win32 y COM para aplicaciones UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).  
  
1.  Incluir (`#include`) cualquier necesaria en tiempo de ejecución de Windows, biblioteca de plantillas C++ de Windows en tiempo de ejecución o encabezados de la biblioteca estándar de C++.  
  
     [!code-cpp[wrl-consume-event#2](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]  
  
     `Windows.Devices.Enumeration.h` declara los tipos que son necesarios para enumerar los dispositivos.  
  
     Se recomienda que use la directiva `using namespace` en el archivo .cpp para que el código sea más legible.  
  
2.  Declare las variables locales para la aplicación. En este ejemplo contiene el recuento del número de dispositivos enumerados y tokens de registro que habilitarla más adelante cancelar la suscripción a eventos.  
  
     [!code-cpp[wrl-consume-event#7](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]  
  
3.  Inicializar el tiempo de ejecución de Windows.  
  
     [!code-cpp[wrl-consume-event#3](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]  
  
4.  Crear un [eventos](../windows/event-class-windows-runtime-cpp-template-library.md) objeto que se sincroniza la finalización del proceso de enumeración a la aplicación principal.  
  
     [!code-cpp[wrl-consume-event#4](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  Este evento es de demostración solo como parte de una aplicación de consola. En este ejemplo se utiliza el evento para asegurarse de que una operación asincrónica se complete antes de la aplicación se cierra. En la mayoría de las aplicaciones, normalmente no esperar operaciones asincrónicas en completarse.  
  
5.  Crear un generador de activación para el `IDeviceWatcher` interfaz.  
  
     [!code-cpp[wrl-consume-event#5](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]  
  
     El tiempo de ejecución de Windows usa los nombres completos para identificar los tipos. El `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation` parámetro es una cadena que se proporciona el tiempo de ejecución de Windows y contiene el nombre de clase en tiempo de ejecución.  
  
6.  Crear el `IDeviceWatcher` objeto.  
  
     [!code-cpp[wrl-consume-event#6](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]  
  
7.  Use la `Callback` función para suscribirse a la `Added`, `EnumerationCompleted`, y `Stopped` eventos.  
  
     [!code-cpp[wrl-consume-event#8](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]  
  
     El `Added` controlador de eventos incrementa el recuento de dispositivos enumerados. Se detiene el proceso de enumeración cuando se encuentran diez dispositivos.  
  
     El `Stopped` quita los controladores de eventos de controlador de eventos y establece el evento de finalización.  
  
     El `EnumerationCompleted` controlador de eventos detiene el proceso de enumeración. Se controle este evento en caso de que hay menos de diez dispositivos.  
  
    > [!TIP]
    >  Este ejemplo utiliza una expresión lambda para definir las devoluciones de llamada. También puede usar los objetos de función (functors), punteros de función, o [std:: Function](../standard-library/function-class.md) objetos. Para obtener más información sobre las expresiones lambda, vea [Expresiones lambda](../cpp/lambda-expressions-in-cpp.md).  
  
8.  Inicie el proceso de enumeración.  
  
     [!code-cpp[wrl-consume-event#9](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]  
  
9. Espere a que el proceso de enumeración completar y, a continuación, imprimir un mensaje. Todos los objetos `ComPtr` y RAII salen del ámbito y se liberan automáticamente.  
  
     [!code-cpp[wrl-consume-event#10](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]  
  
 Este es el ejemplo completo:  
  
 [!code-cpp[wrl-consume-event#1](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `wrl-consume-events.cpp` y, a continuación, ejecute el siguiente comando un **Visual Studio Command Prompt** ventana.  
  
 `cl.exe wrl-consume-events.cpp runtimeobject.lib`  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)