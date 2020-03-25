---
title: 'Cómo: Controlar eventos mediante WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
ms.openlocfilehash: 0e13212d7cb481bc72a903a31fb170fd1ff8b7ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213933"
---
# <a name="how-to-handle-events-using-wrl"></a>Cómo: Controlar eventos mediante WRL

En este documento se muestra cómo usar la C++ biblioteca de plantillas de Windows Runtime (WRL) para suscribirse a los eventos de un objeto Windows Runtime y controlarlos.

Para obtener un ejemplo más básico que crea una instancia de ese componente y recupera un valor de propiedad, consulte [Cómo: activar y usar un componente de Windows Runtime](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).

## <a name="subscribing-to-and-handling-events"></a>Suscripción y control de eventos

En los pasos siguientes se inicia un objeto `ABI::Windows::System::Threading::IDeviceWatcher` y se usan controladores de eventos para supervisar el progreso. La interfaz de `IDeviceWatcher` permite enumerar dispositivos de forma asincrónica o en segundo plano, y recibir una notificación cuando se agregan, quitan o cambian dispositivos. La función de [devolución de llamada](callback-function-wrl.md) es una parte importante de este ejemplo porque le permite especificar controladores de eventos que procesan los resultados de la operación en segundo plano. A continuación se muestra el ejemplo completo.

> [!WARNING]
> Aunque normalmente se usa la biblioteca C++ de plantillas de Windows Runtime en una aplicación plataforma universal de Windows, en este ejemplo se usa una aplicación de consola para la ilustración. Las funciones como `wprintf_s` no están disponibles en una aplicación Plataforma universal de Windows. Para obtener más información sobre los tipos y las funciones que se pueden usar en una aplicación Plataforma universal de Windows, vea [funciones de CRT no admitidas en las aplicaciones de plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) y [Win32 y com para aplicaciones UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

1. Incluya (`#include`) cualquier Windows Runtime necesario, Windows Runtime C++ biblioteca de plantillas o C++ encabezados de la biblioteca estándar.

   [!code-cpp[wrl-consume-event#2](../codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]

   `Windows.Devices.Enumeration.h` declara los tipos que son necesarios para enumerar los dispositivos.

   Se recomienda que use la directiva `using namespace` en el archivo .cpp para que el código sea más legible.

2. Declare las variables locales de la aplicación. Este ejemplo contiene el número de dispositivos enumerados y tokens de registro que permiten cancelar la suscripción a los eventos más adelante.

   [!code-cpp[wrl-consume-event#7](../codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]

3. Inicialice el Windows Runtime.

   [!code-cpp[wrl-consume-event#3](../codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]

4. Cree un objeto de [evento](event-class-wrl.md) que sincronice la finalización del proceso de enumeración a la aplicación principal.

   [!code-cpp[wrl-consume-event#4](../codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]

   > [!NOTE]
   > Este evento es solo para la demostración como parte de una aplicación de consola. En este ejemplo se usa el evento para asegurarse de que una operación asincrónica se completa antes de que se cierre la aplicación. En la mayoría de las aplicaciones, normalmente no espera a que se completen las operaciones asincrónicas.

5. Cree un generador de activación para la interfaz `IDeviceWatcher`.

   [!code-cpp[wrl-consume-event#5](../codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]

   El Windows Runtime usa nombres completos para identificar tipos. El parámetro `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation` es una cadena proporcionada por el Windows Runtime y contiene el nombre de clase en tiempo de ejecución necesario.

6. Cree el objeto `IDeviceWatcher`.

   [!code-cpp[wrl-consume-event#6](../codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]

7. Utilice la función `Callback` para suscribirse a los eventos `Added`, `EnumerationCompleted`y `Stopped`.

   [!code-cpp[wrl-consume-event#8](../codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]

   El controlador de eventos `Added` incrementa el número de dispositivos enumerados. Detiene el proceso de enumeración después de encontrar diez dispositivos.

   El controlador de eventos `Stopped` quita los controladores de eventos y establece el evento de finalización.

   El controlador de eventos `EnumerationCompleted` detiene el proceso de enumeración. Este evento se controla en caso de que haya menos de diez dispositivos.

   > [!TIP]
   > En este ejemplo se usa una expresión lambda para definir las devoluciones de llamada. También puede usar objetos de función (funciones funcs), punteros de función o objetos [STD:: function](../../standard-library/function-class.md) . Para obtener más información sobre las expresiones lambda, vea [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md).

8. Inicie el proceso de enumeración.

   [!code-cpp[wrl-consume-event#9](../codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]

9. Espere a que el proceso de enumeración finalice y, a continuación, imprima un mensaje. Todos los objetos `ComPtr` y RAII salen del ámbito y se liberan automáticamente.

   [!code-cpp[wrl-consume-event#10](../codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]

Este es el ejemplo completo:

[!code-cpp[wrl-consume-event#1](../codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]

## <a name="compiling-the-code"></a>Compilar el código

Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `wrl-consume-events.cpp` y, a continuación, ejecute el siguiente comando en una ventana **del símbolo del sistema de Visual Studio** .

`cl.exe wrl-consume-events.cpp runtimeobject.lib`

## <a name="see-also"></a>Consulte también

[Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](windows-runtime-cpp-template-library-wrl.md)
