---
title: "Cómo: controlar eventos mediante WRL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a3341992ce2b10897fca165a787e568b5e0bc660
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-handle-events-using-wrl"></a>Cómo: Controlar eventos mediante WRL
Este documento muestra cómo usar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución (WRL) para suscribirse a y controlar los eventos de un objeto en tiempo de ejecución de Windows.  
  
 Para obtener un ejemplo más básico que crea una instancia de dicho componente y recupera un valor de propiedad, vea [Cómo: activar y usar un componente de Windows en tiempo de ejecución](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).  
  
## <a name="subscribing-to-and-handling-events"></a>Suscribirse a y control de eventos  
 Los siguientes pasos inicio un `ABI::Windows::System::Threading::IDeviceWatcher` de objetos y usar controladores de eventos para supervisar el progreso. El `IDeviceWatcher` interfaz permite enumerar los dispositivos de forma asincrónica o en segundo plano y recibir una notificación cuando se agregan, quitan o cambiar dispositivos. El [devolución de llamada](../windows/callback-function-windows-runtime-cpp-template-library.md) función es una parte importante de este ejemplo, porque le permite especificar los controladores de eventos que procesan los resultados de la operación en segundo plano. A continuación se muestra el ejemplo completo.  
  
> [!WARNING]
>  Aunque normalmente se utiliza la biblioteca de plantillas de C++ de Windows en tiempo de ejecución en una aplicación de plataforma Universal de Windows, en este ejemplo se utiliza una aplicación de consola a modo de ilustración. Las funciones como `wprintf_s` no están disponibles en una aplicación de la plataforma Universal de Windows. Para obtener más información sobre los tipos y funciones que puede utilizar en una aplicación de plataforma Universal de Windows, vea [funciones de CRT no admitidas con/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx) y [aplicaciones Win32 y COM para la tienda Windows](http://msdn.microsoft.com/library/windows/apps/br205757.aspx).  
  
1.  Incluir (`#include`) los necesarios en tiempo de ejecución de Windows, biblioteca de plantillas de C++ de Windows en tiempo de ejecución o encabezados de la biblioteca estándar de C++.  
  
     [!code-cpp[wrl-consume-event#2](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]  
  
     Windows.Devices.Enumeration.h declara los tipos necesarios para enumerar los dispositivos.  
  
     Se recomienda que use la directiva `using namespace` en el archivo .cpp para que el código sea más legible.  
  
2.  Declare las variables locales de la aplicación. Este ejemplo contiene el recuento del número de dispositivos enumerados y tokens de registro que permiten su posterior cancelar la suscripción a eventos.  
  
     [!code-cpp[wrl-consume-event#7](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]  
  
3.  Inicializar el Runtime de Windows.  
  
     [!code-cpp[wrl-consume-event#3](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]  
  
4.  Crear un [eventos](../windows/event-class-windows-runtime-cpp-template-library.md) objeto que se sincroniza la finalización del proceso de enumeración a la aplicación principal.  
  
     [!code-cpp[wrl-consume-event#4](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  Este evento es de demostración únicamente como parte de una aplicación de consola. Este ejemplo utiliza el evento para asegurar que una operación asincrónica se complete antes de la aplicación se cierra. En la mayoría de las aplicaciones, normalmente no esperar operaciones asincrónicas que se complete.  
  
5.  Cree un generador de activación para el `IDeviceWatcher` interfaz.  
  
     [!code-cpp[wrl-consume-event#5](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]  
  
     El tiempo de ejecución de Windows utiliza nombres completos para identificar tipos. El `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation` parámetro es una cadena que se proporciona en tiempo de ejecución de Windows y contiene el nombre de clase en tiempo de ejecución.  
  
6.  Crear la `IDeviceWatcher` objeto.  
  
     [!code-cpp[wrl-consume-event#6](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]  
  
7.  Use la `Callback` función para suscribirse a la `Added`, `EnumerationCompleted`, y `Stopped` eventos.  
  
     [!code-cpp[wrl-consume-event#8](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]  
  
     El `Added` controlador de eventos incrementa el recuento de dispositivos enumerados. Se detiene el proceso de enumeración cuando se encuentran diez dispositivos.  
  
     El `Stopped` controlador de eventos quita los controladores de eventos y establece el evento de finalización.  
  
     El `EnumerationCompleted` controlador de eventos detiene el proceso de enumeración. Se controlar este evento en caso de que hay menos de diez dispositivos.  
  
    > [!TIP]
    >  Este ejemplo utiliza una expresión lambda para definir las devoluciones de llamada. También puede utilizar objetos de función (funciones), punteros a función, o [std:: Function](../standard-library/function-class.md) objetos. Para obtener más información sobre las expresiones lambda, vea [Expresiones lambda](../cpp/lambda-expressions-in-cpp.md).  
  
8.  Inicie el proceso de enumeración.  
  
     [!code-cpp[wrl-consume-event#9](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]  
  
9. Espere a que el proceso de enumeración completar y, a continuación, imprimir un mensaje. Todos los objetos `ComPtr` y RAII salen del ámbito y se liberan automáticamente.  
  
     [!code-cpp[wrl-consume-event#10](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]  
  
 Aquí se muestra el ejemplo completo:  
  
 [!code-cpp[wrl-consume-event#1](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo que se denomina `wrl-consume-events.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe events.cpp consumir wrl runtimeobject.lib**  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)