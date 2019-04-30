---
title: Procedimiento Completar operaciones asincrónicas mediante WRL
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
ms.openlocfilehash: 09c341e5e3d4f6007d5d5f66b7c06e1f0af5a65c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398347"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>Procedimiento Completar operaciones asincrónicas mediante WRL

Este documento muestra cómo usar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución (WRL) para iniciar operaciones asincrónicas y realizar el trabajo cuando las operaciones se completan.

En este documento se muestran dos ejemplos. El primer ejemplo inicia un temporizador asincrónico y espera a que caduque el temporizador. En este ejemplo, especifique la acción asincrónica cuando se crea el objeto de temporizador. El segundo ejemplo ejecuta un subproceso de trabajo en segundo plano. En este ejemplo se muestra cómo trabajar con un método en tiempo de ejecución de Windows que devuelve un `IAsyncInfo` interfaz. El [devolución de llamada](callback-function-wrl.md) función es una parte importante de los dos ejemplos porque permite especificar un controlador de eventos para procesar los resultados de las operaciones asincrónicas.

Para obtener un ejemplo más básico que crea una instancia de un componente y recupera un valor de propiedad, vea [Cómo: Activar y usar un componente de Windows en tiempo de ejecución](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).

> [!TIP]
> Estos ejemplos usan expresiones lambda para definir las devoluciones de llamada. También puede usar los objetos de función (functors), punteros de función, o [std:: Function](../../standard-library/function-class.md) objetos. Para obtener más información sobre las expresiones lambda de C++, vea [expresiones Lambda](../../cpp/lambda-expressions-in-cpp.md).

## <a name="example-working-with-a-timer"></a>Ejemplo: Trabajar con un temporizador

Los pasos siguientes, inicia un temporizador asincrónico y esperar a que caduque el temporizador. A continuación se muestra el ejemplo completo.

> [!WARNING]
> Aunque normalmente se usa la biblioteca de plantillas de C++ de Windows en tiempo de ejecución en una aplicación de plataforma Universal de Windows (UWP), en este ejemplo se usa una aplicación de consola para ilustración. Las funciones como `wprintf_s` no están disponibles en una aplicación para UWP. Para obtener más información sobre los tipos y funciones que puede usar en una aplicación para UWP, consulte [funciones de CRT no admitidas en aplicaciones de la plataforma Universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) y [Win32 y COM para aplicaciones UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

1. Incluir (`#include`) cualquier necesaria en tiempo de ejecución de Windows, biblioteca de plantillas C++ de Windows en tiempo de ejecución o encabezados de la biblioteca estándar de C++.

   [!code-cpp[wrl-consume-async#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]

   `Windows.System.Threading.h` declara los tipos que son necesarios para usar un temporizador asincrónico.

   Se recomienda que use la directiva `using namespace` en el archivo .cpp para que el código sea más legible.

2. Inicializar el tiempo de ejecución de Windows.

   [!code-cpp[wrl-consume-async#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]

3. Crear un generador de activación para el `ABI::Windows::System::Threading::IThreadPoolTimer` interfaz.

   [!code-cpp[wrl-consume-async#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]

   El tiempo de ejecución de Windows usa los nombres completos para identificar los tipos. El `RuntimeClass_Windows_System_Threading_ThreadPoolTimer` parámetro es una cadena que se proporciona el tiempo de ejecución de Windows y contiene el nombre de clase en tiempo de ejecución.

4. Crear un [eventos](event-class-wrl.md) objeto que se sincroniza la devolución de llamada de temporizador para la aplicación principal.

   [!code-cpp[wrl-consume-async#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]

   > [!NOTE]
   > Este evento es de demostración solo como parte de una aplicación de consola. En este ejemplo se utiliza el evento para asegurarse de que una operación asincrónica se complete antes de la aplicación se cierra. En la mayoría de las aplicaciones, normalmente no esperar operaciones asincrónicas en completarse.

5. Crear un `IThreadPoolTimer` objeto que expira después de dos segundos. Use la `Callback` función para crear el controlador de eventos (un `ABI::Windows::System::Threading::ITimerElapsedHandler` objeto).

   [!code-cpp[wrl-consume-async#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]

6. Imprimir un mensaje en la consola y esperar la devolución de llamada de temporizador en completarse. Todos los objetos `ComPtr` y RAII salen del ámbito y se liberan automáticamente.

   [!code-cpp[wrl-consume-async#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]

Este es el ejemplo completo:

[!code-cpp[wrl-consume-async#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]

### <a name="compiling-the-code"></a>Compilar el código

Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `wrl-consume-async.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

`cl.exe wrl-consume-async.cpp runtimeobject.lib`

## <a name="example-working-with-a-background-thread"></a>Ejemplo: Trabajar con un subproceso en segundo plano

Los pasos siguientes iniciar un subproceso de trabajo y definen la acción realizada por ese subproceso. A continuación se muestra el ejemplo completo.

> [!TIP]
> Este ejemplo muestra cómo trabajar con el `ABI::Windows::Foundation::IAsyncAction` interfaz. Este patrón se puede aplicar a cualquier interfaz que implementa `IAsyncInfo`: `IAsyncAction`, `IAsyncActionWithProgress`, `IAsyncOperation`, y `IAsyncOperationWithProgress`.

1. Incluir (`#include`) cualquier necesaria en tiempo de ejecución de Windows, biblioteca de plantillas C++ de Windows en tiempo de ejecución o encabezados de la biblioteca estándar de C++.

   [!code-cpp[wrl-consume-asyncOp#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]

   Windows.System.Threading.h declara los tipos que son necesarios para usar un subproceso de trabajo.

   Se recomienda que use el `using namespace` la directiva en el archivo .cpp para que el código sea más legible.

2. Inicializar el tiempo de ejecución de Windows.

   [!code-cpp[wrl-consume-asyncOp#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]

3. Crear un generador de activación para el `ABI::Windows::System::Threading::IThreadPoolStatics` interfaz.

   [!code-cpp[wrl-consume-asyncOp#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]

4. Crear un [eventos](event-class-wrl.md) objeto que se sincroniza la finalización del subproceso de trabajo a la aplicación principal.

   [!code-cpp[wrl-consume-asyncOp#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]

   > [!NOTE]
   > Este evento es de demostración solo como parte de una aplicación de consola. En este ejemplo se utiliza el evento para asegurarse de que una operación asincrónica se complete antes de la aplicación se cierra. En la mayoría de las aplicaciones, normalmente no esperar operaciones asincrónicas en completarse.

5. Llame a la `IThreadPoolStatics::RunAsync` método para crear un subproceso de trabajo. Use el `Callback` función para definir la acción.

   [!code-cpp[wrl-consume-asyncOp#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]

   El `IsPrime` función está definida en el ejemplo completo que sigue.

6. Imprimir un mensaje en la consola y espere a que el subproceso complete. Todos los objetos `ComPtr` y RAII salen del ámbito y se liberan automáticamente.

   [!code-cpp[wrl-consume-asyncOp#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]

Este es el ejemplo completo:

[!code-cpp[wrl-consume-asyncOp#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]

### <a name="compiling-the-code"></a>Compilar el código

Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `wrl-consume-asyncOp.cpp` y, a continuación, ejecute el siguiente comando un **Visual Studio Command Prompt** ventana.

`cl.exe wrl-consume-asyncOp.cpp runtimeobject.lib`

## <a name="see-also"></a>Vea también

[Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](windows-runtime-cpp-template-library-wrl.md)