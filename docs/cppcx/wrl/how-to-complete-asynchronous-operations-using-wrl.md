---
title: 'Cómo: Completar operaciones asincrónicas mediante WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
ms.openlocfilehash: 8e7e52342cf73a56c6c33d4d1f998f446d632ddd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213946"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>Cómo: Completar operaciones asincrónicas mediante WRL

En este documento se muestra cómo usar la C++ biblioteca de plantillas de Windows Runtime (WRL) para iniciar operaciones asincrónicas y realizar el trabajo cuando se completan las operaciones.

En este documento se muestran dos ejemplos. En el primer ejemplo se inicia un temporizador asincrónico y se espera a que el temporizador expire. En este ejemplo, se especifica la acción asincrónica al crear el objeto de temporizador. En el segundo ejemplo se ejecuta un subproceso de trabajo en segundo plano. En este ejemplo se muestra cómo trabajar con un método Windows Runtime que devuelve una interfaz `IAsyncInfo`. La función de [devolución de llamada](callback-function-wrl.md) es una parte importante de ambos ejemplos porque les permite especificar un controlador de eventos para procesar los resultados de las operaciones asincrónicas.

Para obtener un ejemplo más básico que crea una instancia de un componente y recupera un valor de propiedad, consulte [Cómo: activar y usar un componente de Windows Runtime](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).

> [!TIP]
> En estos ejemplos se usan expresiones lambda para definir las devoluciones de llamada. También puede usar objetos de función (funciones funcs), punteros de función o objetos [STD:: function](../../standard-library/function-class.md) . Para obtener más información C++ sobre las expresiones lambda, vea [expresiones lambda](../../cpp/lambda-expressions-in-cpp.md).

## <a name="example-working-with-a-timer"></a>Ejemplo: trabajar con un temporizador

En los pasos siguientes se inicia un temporizador asincrónico y se espera a que expire el temporizador. A continuación se muestra el ejemplo completo.

> [!WARNING]
> Aunque normalmente se usa la biblioteca C++ de plantillas de Windows Runtime en una aplicación plataforma universal de Windows (UWP), en este ejemplo se usa una aplicación de consola para la ilustración. Las funciones como `wprintf_s` no están disponibles en una aplicación de UWP. Para obtener más información sobre los tipos y las funciones que puede usar en una aplicación de UWP, consulte [funciones de CRT no admitidas en aplicaciones de plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) y [Win32 y com para aplicaciones de UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

1. Incluya (`#include`) cualquier Windows Runtime necesario, Windows Runtime C++ biblioteca de plantillas o C++ encabezados de la biblioteca estándar.

   [!code-cpp[wrl-consume-async#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]

   `Windows.System.Threading.h` declara los tipos necesarios para utilizar un temporizador asincrónico.

   Se recomienda que use la directiva `using namespace` en el archivo .cpp para que el código sea más legible.

2. Inicialice el Windows Runtime.

   [!code-cpp[wrl-consume-async#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]

3. Cree un generador de activación para la interfaz `ABI::Windows::System::Threading::IThreadPoolTimer`.

   [!code-cpp[wrl-consume-async#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]

   El Windows Runtime usa nombres completos para identificar tipos. El parámetro `RuntimeClass_Windows_System_Threading_ThreadPoolTimer` es una cadena proporcionada por el Windows Runtime y contiene el nombre de clase en tiempo de ejecución necesario.

4. Cree un objeto de [evento](event-class-wrl.md) que sincronice la devolución de llamada del temporizador a la aplicación principal.

   [!code-cpp[wrl-consume-async#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]

   > [!NOTE]
   > Este evento es solo para la demostración como parte de una aplicación de consola. En este ejemplo se usa el evento para asegurarse de que una operación asincrónica se completa antes de que se cierre la aplicación. En la mayoría de las aplicaciones, normalmente no espera a que se completen las operaciones asincrónicas.

5. Cree un objeto `IThreadPoolTimer` que expire después de dos segundos. Utilice la función `Callback` para crear el controlador de eventos (un objeto `ABI::Windows::System::Threading::ITimerElapsedHandler`).

   [!code-cpp[wrl-consume-async#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]

6. Imprima un mensaje en la consola y espere a que se complete la devolución de llamada del temporizador. Todos los objetos `ComPtr` y RAII salen del ámbito y se liberan automáticamente.

   [!code-cpp[wrl-consume-async#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]

Este es el ejemplo completo:

[!code-cpp[wrl-consume-async#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]

### <a name="compiling-the-code"></a>Compilar el código

Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `wrl-consume-async.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

`cl.exe wrl-consume-async.cpp runtimeobject.lib`

## <a name="example-working-with-a-background-thread"></a>Ejemplo: trabajar con un subproceso en segundo plano

En los pasos siguientes se inicia un subproceso de trabajo y se define la acción que realiza ese subproceso. A continuación se muestra el ejemplo completo.

> [!TIP]
> En este ejemplo se muestra cómo trabajar con la interfaz `ABI::Windows::Foundation::IAsyncAction`. Puede aplicar este patrón a cualquier interfaz que implemente `IAsyncInfo`: `IAsyncAction`, `IAsyncActionWithProgress`, `IAsyncOperation`y `IAsyncOperationWithProgress`.

1. Incluya (`#include`) cualquier Windows Runtime necesario, Windows Runtime C++ biblioteca de plantillas o C++ encabezados de la biblioteca estándar.

   [!code-cpp[wrl-consume-asyncOp#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]

   Windows. System. Threading. h declara los tipos necesarios para usar un subproceso de trabajo.

   Se recomienda usar la Directiva `using namespace` en el archivo. cpp para que el código sea más legible.

2. Inicialice el Windows Runtime.

   [!code-cpp[wrl-consume-asyncOp#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]

3. Cree un generador de activación para la interfaz `ABI::Windows::System::Threading::IThreadPoolStatics`.

   [!code-cpp[wrl-consume-asyncOp#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]

4. Cree un objeto de [evento](event-class-wrl.md) que sincronice la finalización del subproceso de trabajo a la aplicación principal.

   [!code-cpp[wrl-consume-asyncOp#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]

   > [!NOTE]
   > Este evento es solo para la demostración como parte de una aplicación de consola. En este ejemplo se usa el evento para asegurarse de que una operación asincrónica se completa antes de que se cierre la aplicación. En la mayoría de las aplicaciones, normalmente no espera a que se completen las operaciones asincrónicas.

5. Llame al método `IThreadPoolStatics::RunAsync` para crear un subproceso de trabajo. Utilice la función `Callback` para definir la acción.

   [!code-cpp[wrl-consume-asyncOp#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]

   La función `IsPrime` se define en el ejemplo completo siguiente.

6. Imprima un mensaje en la consola y espere a que se complete el subproceso. Todos los objetos `ComPtr` y RAII salen del ámbito y se liberan automáticamente.

   [!code-cpp[wrl-consume-asyncOp#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]

Este es el ejemplo completo:

[!code-cpp[wrl-consume-asyncOp#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]

### <a name="compiling-the-code"></a>Compilar el código

Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `wrl-consume-asyncOp.cpp` y, a continuación, ejecute el siguiente comando en una ventana **del símbolo del sistema de Visual Studio** .

`cl.exe wrl-consume-asyncOp.cpp runtimeobject.lib`

## <a name="see-also"></a>Consulte también

[Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](windows-runtime-cpp-template-library-wrl.md)
