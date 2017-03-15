---
title: "C&#243;mo: Controlar eventos mediante WRL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# C&#243;mo: Controlar eventos mediante WRL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este documento se muestra cómo utilizar [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\) para suscribirse y para controlar los eventos de un objeto de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] .  
  
 Para obtener un ejemplo básico que crea una instancia de ese componente y recuperar un valor de propiedad, vea [Cómo: Activar y usar un componente de Windows en tiempo de ejecución](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).  
  
## La suscripción a y controlar eventos  
 Los pasos siguientes inician un objeto de `ABI::Windows::System::Threading::IDeviceWatcher` y controladores de eventos de uso a supervisar progreso.  La interfaz de `IDeviceWatcher` permite enumerar los dispositivos de forma asincrónica, o en segundo plano, y recibe la notificación cuando se agregan, se quitan, o se cambian los dispositivos.  La función de [Devolución de llamada](../windows/callback-function-windows-runtime-cpp-template-library.md) es una parte importante de este ejemplo porque permite especificar controladores de eventos que procesan los resultados de la operación de fondo.  A continuación se muestra el ejemplo completo.  
  
> [!WARNING]
>  Aunque use normalmente [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] en una aplicación de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] , este ejemplo utiliza una aplicación de consola a la ilustración.  Las funciones como `wprintf_s` no están disponibles de una aplicación de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] .  Para obtener más información sobre los tipos y funciones que puede utilizar en una aplicación de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] , vea [Funciones CRT no compatibles con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx) y [Win32 y COM para las aplicaciones del almacén de Windows](http://msdn.microsoft.com/library/windows/apps/br205757.aspx).  
  
1.  Incluya \(`#include`\) cualquier encabezado de biblioteca de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)], [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] o estándar de C\+\+ necesario.  
  
     [!code-cpp[wrl-consume-event#2](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]  
  
     Windows.Devices.Enumeration.h declara los tipos necesarios para enumerar los dispositivos.  
  
     Se recomienda que use la directiva `using namespace` en el archivo .cpp para que el código sea más legible.  
  
2.  Declare las variables locales de la aplicación.  Este ejemplo contiene el recuento del número de dispositivos enumerados y tokens de registro que permiten cancelar la suscripción después de eventos.  
  
     [!code-cpp[wrl-consume-event#7](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]  
  
3.  Inicializa [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].  
  
     [!code-cpp[wrl-consume-event#3](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]  
  
4.  Cree un objeto de [Evento](../windows/event-class-windows-runtime-cpp-template-library.md) que sincronice el proceso de enumeración a la aplicación principal.  
  
     [!code-cpp[wrl-consume-event#4](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  Este evento es para la demostración solo como parte de una aplicación de consola.  Este ejemplo utiliza el evento para asegurarse de que una operación async completa antes de salir de la aplicación.  En la mayoría de las aplicaciones, no suele esperar operaciones async para completar.  
  
5.  Cree un generador de activación para la interfaz de `IDeviceWatcher` .  
  
     [!code-cpp[wrl-consume-event#5](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]  
  
     [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] utiliza nombres completos para identificar tipos.  El parámetro de `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation` es una cadena proporcionada por [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] y contiene el nombre de clase necesario en tiempo de ejecución.  
  
6.  Cree el objeto de `IDeviceWatcher` .  
  
     [!code-cpp[wrl-consume-event#6](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]  
  
7.  Utilice la función de `Callback` para suscribirse a `Added`, a `EnumerationCompleted`, y eventos de `Stopped` .  
  
     [!code-cpp[wrl-consume-event#8](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]  
  
     El controlador de eventos `Added` incrementa el recuento de dispositivos enumerados.  Detiene el proceso de enumeración después de que se encuentren diez dispositivos.  
  
     El controlador de eventos `Stopped` quitar los controladores de eventos y establece el evento de finalización.  
  
     El controlador de eventos `EnumerationCompleted` detiene el proceso de enumeración.  Manejamos este evento cuando hay menos que diez dispositivos.  
  
    > [!TIP]
    >  Este ejemplo utiliza una expresión lambda para definir las devoluciones de llamada.  También puede utilizar los objetos de función \(functors\), punteros a función, o los objetos de [std::function](../standard-library/function-class.md) .  Para obtener más información sobre las expresiones lambda, vea [Expresiones lambda](../cpp/lambda-expressions-in-cpp.md).  
  
8.  Inicia el proceso de enumeración.  
  
     [!code-cpp[wrl-consume-event#9](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]  
  
9. Espere a que el proceso de enumeración para completar y después para imprimir un mensaje.  Todos los objetos `ComPtr` y RAII salen del ámbito y se liberan automáticamente.  
  
     [!code-cpp[wrl-consume-event#10](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]  
  
 A continuación se muestra el ejemplo completo:  
  
 [!code-cpp[wrl-consume-event#1](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]  
  
## Compilar el código  
 Para compilar el código, cópielo y péguelo en un proyecto de Visual Studio, o péguelo en un archivo denominado `wrl-consume-events.cpp` y después se ejecute el siguiente comando en una ventana de símbolo del sistema de Visual Studio.  
  
 **cl.exe wrl\-consume\-events.cpp runtimeobject.lib**  
  
## Vea también  
 [Biblioteca de plantillas de Windows Runtime C\+\+ \(WRL\)](../Topic/Windows%20Runtime%20C++%20Template%20Library%20\(WRL\).md)