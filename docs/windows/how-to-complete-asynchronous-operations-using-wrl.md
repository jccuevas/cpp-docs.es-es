---
title: "C&#243;mo: Completar operaciones asincr&#243;nicas mediante WRL | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Completar operaciones asincr&#243;nicas mediante WRL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este documento se muestra cómo utilizar [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\) para iniciar operaciones asincrónicas y para realizar el trabajo cuando las operaciones completan.  
  
 En este documento se muestran dos ejemplos.  El primer ejemplo inicia un temporizador asincrónico y espera el temporizador expire.  En este ejemplo, se especifica la acción asincrónico cuando se crea el objeto de temporizador.  El segundo ejemplo ejecuta un subproceso de trabajo en segundo plano.  En este ejemplo se muestra cómo ejecutar un método de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] que devuelve una interfaz de `IAsyncInfo` .  La función de [Devolución de llamada](../windows/callback-function-windows-runtime-cpp-template-library.md) es una parte importante de ambos ejemplos porque les permite especificar un controlador de eventos para procesar los resultados de las operaciones asincrónicas.  
  
 Para obtener un ejemplo básico que crea una instancia de ese componente y recuperar un valor de propiedad, vea [Cómo: Activar y usar un componente de Windows en tiempo de ejecución](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).  
  
> [!TIP]
>  Estos ejemplos usan expresiones lambda para definir las devoluciones de llamada.  También puede utilizar los objetos de función \(functors\), punteros a función, o los objetos de [std::function](../standard-library/function-class.md) .  Para obtener más información sobre las expresiones lambda de C\+\+, vea [Expresiones lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## Ejemplo: Trabajar con un temporizador  
 Los pasos siguientes inician un temporizador asincrónico y esperan el temporizador expire.  A continuación se muestra el ejemplo completo.  
  
> [!WARNING]
>  Aunque use normalmente [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] en una aplicación de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] , este ejemplo utiliza una aplicación de consola a la ilustración.  Las funciones como `wprintf_s` no están disponibles de una aplicación de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] .  Para obtener más información sobre los tipos y funciones que puede utilizar en una aplicación de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] , vea [Funciones CRT no compatibles con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx) y [Win32 y COM para las aplicaciones del almacén de Windows](http://msdn.microsoft.com/library/windows/apps/br205757.aspx).  
  
1.  Incluya \(`#include`\) cualquier encabezado de biblioteca de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)], [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] o estándar de C\+\+ necesario.  
  
     [!code-cpp[wrl-consume-async#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]  
  
     Windows.System.Threading.h declara los tipos necesarios para usar un temporizador asincrónico.  
  
     Se recomienda que use la directiva `using namespace` en el archivo .cpp para que el código sea más legible.  
  
2.  Inicializa [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].  
  
     [!code-cpp[wrl-consume-async#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]  
  
3.  Cree un generador de activación para la interfaz de `ABI::Windows::System::Threading::IThreadPoolTimer` .  
  
     [!code-cpp[wrl-consume-async#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]  
  
     [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] utiliza nombres completos para identificar tipos.  El parámetro de `RuntimeClass_Windows_System_Threading_ThreadPoolTimer` es una cadena proporcionada por [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] y contiene el nombre de clase necesario en tiempo de ejecución.  
  
4.  Cree un objeto de [Evento](../windows/event-class-windows-runtime-cpp-template-library.md) que sincronice la devolución de temporizador a la aplicación principal.  
  
     [!code-cpp[wrl-consume-async#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  Este evento es para la demostración solo como parte de una aplicación de consola.  Este ejemplo utiliza el evento para asegurarse de que una operación async completa antes de salir de la aplicación.  En la mayoría de las aplicaciones, no suele esperar operaciones async para completar.  
  
5.  Cree un objeto de `IThreadPoolTimer` que expire después de dos segundos.  Utilice la función de `Callback` para crear el controlador de eventos \(un objeto de `ABI::Windows::System::Threading::ITimerElapsedHandler` \).  
  
     [!code-cpp[wrl-consume-async#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]  
  
6.  Imprimir un mensaje en la consola y esperan la devolución del temporizador para completar.  Todos los objetos `ComPtr` y RAII salen del ámbito y se liberan automáticamente.  
  
     [!code-cpp[wrl-consume-async#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]  
  
 A continuación se muestra el ejemplo completo:  
  
 [!code-cpp[wrl-consume-async#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]  
  
### Compilar el código  
 Para compilar el código, cópielo y péguelo en un proyecto de Visual Studio, o péguelo en un archivo denominado `wrl-consume-async.cpp` y después se ejecute el siguiente comando en una ventana de símbolo del sistema de Visual Studio.  
  
 **cl.exe wrl\-consume\-async.cpp runtimeobject.lib**  
  
## Ejemplo: Trabajar con un subproceso de fondo  
 Los pasos siguientes se inicia un subproceso de trabajo y definen la acción que realiza ese subproceso.  A continuación se muestra el ejemplo completo.  
  
> [!TIP]
>  En este ejemplo se muestra cómo ejecutar la interfaz de `ABI::Windows::Foundation::IAsyncAction` .  Puede aplicar este modelo a las interfaces que implementa `IAsyncInfo`: `IAsyncAction`, `IAsyncActionWithProgress`, `IAsyncOperation`, y `IAsyncOperationWithProgress`.  
  
1.  Incluya \(`#include`\) cualquier encabezado de biblioteca de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)], [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] o estándar de C\+\+ necesario.  
  
     [!code-cpp[wrl-consume-asyncOp#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]  
  
     Windows.System.Threading.h declara los tipos necesarios para utilizar un subproceso de trabajo.  
  
     Recomendamos utilizar la directiva de `using namespace` en el archivo .cpp para hacer el código más legible.  
  
2.  Inicializa [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].  
  
     [!code-cpp[wrl-consume-asyncOp#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]  
  
3.  Cree un generador de activación para la interfaz de `ABI::Windows::System::Threading::IThreadPoolStatics` .  
  
     [!code-cpp[wrl-consume-asyncOp#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]  
  
4.  Cree un objeto de [Evento](../windows/event-class-windows-runtime-cpp-template-library.md) que sincronice el subproceso de trabajo a la aplicación principal.  
  
     [!code-cpp[wrl-consume-asyncOp#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]  
  
    > [!NOTE]
    >  Este evento es para la demostración solo como parte de una aplicación de consola.  Este ejemplo utiliza el evento para asegurarse de que una operación async completa antes de salir de la aplicación.  En la mayoría de las aplicaciones, no suele esperar operaciones async para completar.  
  
5.  Llame al método de `IThreadPoolStatics::RunAsync` para crear un subproceso de trabajo.  Utilice la función de `Callback` para definir la acción.  
  
     [!code-cpp[wrl-consume-asyncOp#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]  
  
     La función de `IsPrime` se define en el ejemplo completo que sigue.  
  
6.  Imprime un mensaje en la consola y espere el subproceso para completar.  Todos los objetos `ComPtr` y RAII salen del ámbito y se liberan automáticamente.  
  
     [!code-cpp[wrl-consume-asyncOp#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]  
  
 A continuación se muestra el ejemplo completo:  
  
 [!code-cpp[wrl-consume-asyncOp#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]  
  
### Compilar el código  
 Para compilar el código, cópielo y péguelo en un proyecto de Visual Studio, o péguelo en un archivo denominado `wrl-consume-asyncOp.cpp` y después se ejecute el siguiente comando en una ventana de símbolo del sistema de Visual Studio.  
  
 **cl.exe wrl\-consume\-asyncOp.cpp runtimeobject.lib**  
  
## Vea también  
 [Biblioteca de plantillas de Windows Runtime C\+\+ \(WRL\)](../Topic/Windows%20Runtime%20C++%20Template%20Library%20\(WRL\).md)