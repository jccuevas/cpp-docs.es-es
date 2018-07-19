---
title: 'Cómo: completar operaciones asincrónicas mediante WRL | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fff0a6e98dd6fdd28b1fbc2e9146d5b68975e0f0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881530"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>Cómo: Completar operaciones asincrónicas mediante WRL
Este documento muestra cómo usar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución (WRL) para iniciar operaciones asincrónicas y realizar el trabajo cuando las operaciones se completan.  
  
 En este documento se muestran dos ejemplos. El primer ejemplo inicia un temporizador asincrónico y espera a que caduque el temporizador. En este ejemplo, puede especificar la acción asincrónica cuando se crea el objeto de temporizador. El segundo ejemplo ejecuta un subproceso de trabajo de segundo plano. Este ejemplo muestra cómo trabajar con un método en tiempo de ejecución de Windows que devuelve un `IAsyncInfo` interfaz. El [devolución de llamada](../windows/callback-function-windows-runtime-cpp-template-library.md) función es una parte importante de los dos ejemplos porque permite especificar un controlador de eventos para procesar los resultados de las operaciones asincrónicas.  
  
 Para obtener un ejemplo más básico que crea una instancia de un componente y recupera un valor de propiedad, vea [Cómo: activar y usar un componente de Windows en tiempo de ejecución](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).  
  
> [!TIP]
>  Estos ejemplos utilizan expresiones lambda para definir las devoluciones de llamada. También puede utilizar objetos de función (funciones), punteros a función, o [std:: Function](../standard-library/function-class.md) objetos. Para obtener más información acerca de las expresiones lambda de C++, vea [expresiones Lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## <a name="example-working-with-a-timer"></a>Ejemplo: Trabajar con un temporizador  
 Los pasos siguientes inicia un temporizador asincrónico y esperan a que caduque el temporizador. A continuación se muestra el ejemplo completo.  
  
> [!WARNING]
>  Aunque normalmente se utiliza la biblioteca de plantillas de C++ de Windows en tiempo de ejecución en una aplicación de plataforma Universal de Windows (UWP), en este ejemplo se utiliza una aplicación de consola a modo de ilustración. Las funciones como `wprintf_s` no están disponibles en una aplicación de UWP. Para obtener más información sobre los tipos y funciones que pueden usar en una aplicación UWP, vea [funciones de CRT no admitidas en aplicaciones de la plataforma Universal de Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) y [Win32 y COM para aplicaciones UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).  
  
1.  Incluir (`#include`) los necesarios en tiempo de ejecución de Windows, biblioteca de plantillas de C++ de Windows en tiempo de ejecución o encabezados de la biblioteca estándar de C++.  
  
     [!code-cpp[wrl-consume-async#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]  
  
     Windows.System.Threading.h declara los tipos que son necesarios para usar un temporizador asincrónico.  
  
     Se recomienda que use la directiva `using namespace` en el archivo .cpp para que el código sea más legible.  
  
2.  Inicializar el Runtime de Windows.  
  
     [!code-cpp[wrl-consume-async#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]  
  
3.  Cree un generador de activación para el `ABI::Windows::System::Threading::IThreadPoolTimer` interfaz.  
  
     [!code-cpp[wrl-consume-async#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]  
  
     El tiempo de ejecución de Windows utiliza nombres completos para identificar tipos. El `RuntimeClass_Windows_System_Threading_ThreadPoolTimer` parámetro es una cadena que se proporciona en tiempo de ejecución de Windows y contiene el nombre de clase en tiempo de ejecución.  
  
4.  Crear un [eventos](../windows/event-class-windows-runtime-cpp-template-library.md) objeto que se sincroniza la devolución de llamada de temporizador para la aplicación principal.  
  
     [!code-cpp[wrl-consume-async#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  Este evento es de demostración únicamente como parte de una aplicación de consola. Este ejemplo utiliza el evento para asegurar que una operación asincrónica se complete antes de la aplicación se cierra. En la mayoría de las aplicaciones, normalmente no esperar operaciones asincrónicas que se complete.  
  
5.  Crear un `IThreadPoolTimer` objeto que expire después de dos segundos. Use la `Callback` función para crear el controlador de eventos (una `ABI::Windows::System::Threading::ITimerElapsedHandler` objeto).  
  
     [!code-cpp[wrl-consume-async#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]  
  
6.  Imprimir un mensaje en la consola y espere a que la devolución de llamada de temporizador que se complete. Todos los objetos `ComPtr` y RAII salen del ámbito y se liberan automáticamente.  
  
     [!code-cpp[wrl-consume-async#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]  
  
 Aquí se muestra el ejemplo completo:  
  
 [!code-cpp[wrl-consume-async#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]  
  
### <a name="compiling-the-code"></a>Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo que se denomina `wrl-consume-async.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe async.cpp consumir wrl runtimeobject.lib**  
  
## <a name="example-working-with-a-background-thread"></a>Ejemplo: Trabajar con un subproceso en segundo plano  
 Los siguientes pasos iniciar un subproceso de trabajo y definen la acción realizada por ese subproceso. A continuación se muestra el ejemplo completo.  
  
> [!TIP]
>  Este ejemplo muestra cómo trabajar con el `ABI::Windows::Foundation::IAsyncAction` interfaz. Puede aplicar este patrón para cualquier interfaz que implemente `IAsyncInfo`: `IAsyncAction`, `IAsyncActionWithProgress`, `IAsyncOperation`, y `IAsyncOperationWithProgress`.  
  
1.  Incluir (`#include`) los necesarios en tiempo de ejecución de Windows, biblioteca de plantillas de C++ de Windows en tiempo de ejecución o encabezados de la biblioteca estándar de C++.  
  
     [!code-cpp[wrl-consume-asyncOp#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]  
  
     Windows.System.Threading.h declara los tipos que son necesarios para usar un subproceso de trabajo.  
  
     Se recomienda que realice la `using namespace` la directiva en el archivo .cpp para que el código sea más legible.  
  
2.  Inicializar el Runtime de Windows.  
  
     [!code-cpp[wrl-consume-asyncOp#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]  
  
3.  Cree un generador de activación para el `ABI::Windows::System::Threading::IThreadPoolStatics` interfaz.  
  
     [!code-cpp[wrl-consume-asyncOp#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]  
  
4.  Crear un [eventos](../windows/event-class-windows-runtime-cpp-template-library.md) objeto que se sincroniza la finalización del subproceso de trabajo en la aplicación principal.  
  
     [!code-cpp[wrl-consume-asyncOp#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]  
  
    > [!NOTE]
    >  Este evento es de demostración únicamente como parte de una aplicación de consola. Este ejemplo utiliza el evento para asegurar que una operación asincrónica se complete antes de la aplicación se cierra. En la mayoría de las aplicaciones, normalmente no esperar operaciones asincrónicas que se complete.  
  
5.  Llame a la `IThreadPoolStatics::RunAsync` método para crear un subproceso de trabajo. Use la `Callback` función para definir la acción.  
  
     [!code-cpp[wrl-consume-asyncOp#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]  
  
     El `IsPrime` función se define en el ejemplo completo que sigue.  
  
6.  Imprimir un mensaje en la consola y espere a que el subproceso que se complete. Todos los objetos `ComPtr` y RAII salen del ámbito y se liberan automáticamente.  
  
     [!code-cpp[wrl-consume-asyncOp#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]  
  
 Aquí se muestra el ejemplo completo:  
  
 [!code-cpp[wrl-consume-asyncOp#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]  
  
### <a name="compiling-the-code"></a>Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo que se denomina `wrl-consume-asyncOp.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe asyncOp.cpp consumir wrl runtimeobject.lib**  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)
