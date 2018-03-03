---
title: Almacenamiento Local (TLS) para el subproceso | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 47e6be3645e03892d17e45256a5a003d982d973f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="thread-local-storage-tls"></a>Almacenamiento local para el subproceso (TLS)
El almacenamiento local para el subproceso (TLS) es el método por el que cada subproceso de un determinado proceso con subproceso puede asignar ubicaciones en las que almacenar los datos específicos de esos subproceso. Datos específicos del subproceso de límite (tiempo de ejecución) se admiten dinámicamente por medio de la API de TLS ([TlsAlloc](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686801), [TlsGetValue](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686812), [TlsSetValue](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686818), y [TlsFree](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686804)). Para obtener más información acerca de cómo se implementa el almacenamiento local de subprocesos en Windows, consulte [almacenamiento Local de subprocesos (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686749\(v=vs.85\).aspx).  Win32 y el compilador de Visual C++ ahora son compatibles con datos por subproceso que se enlazan estáticamente (en tiempo de carga) además de la implementación existente de la API.  
  
##  <a name="_core_compiler_implementation_for_tls"></a>Implementación del compilador para TLS  
 **C ++ 11:** el `thread_local` especificador de clase de almacenamiento es la manera recomendada para especificar el almacenamiento local de subprocesos para los objetos y miembros de clase. Para obtener más información, consulte [clases de almacenamiento (C++)](../cpp/storage-classes-cpp.md).  
  
 Visual C++ también proporciona un atributo específico de Microsoft, [subproceso](../cpp/thread.md), como modificador de clase de almacenamiento extendida. Use la `__declspec` palabra clave para declarar un **subproceso** variable. Por ejemplo, el código siguiente declara una variable local de subproceso de entero y la inicializa con un valor:  
  
```  
__declspec( thread ) int tls_i = 1;  
```  
  
## <a name="rules-and-limitations"></a>Reglas y limitaciones  
 Deben tenerse en cuenta las siguientes instrucciones cuando se declaran objetos y variables locales para el subproceso enlazados estáticamente. Estas instrucciones aplican tanto a [subproceso](../cpp/thread.md)y en su mayor parte también a [thread_local](../cpp/storage-classes-cpp.md):  
  
-   El atributo `thread` se puede aplicar solo a definiciones y declaraciones de clases y datos. No se puede utilizar en declaraciones o definiciones de función. Por ejemplo, el código siguiente genera un error del compilador:  
  
    ```  
  
    __declspec( thread )void func();     // This will generate an error.  
    ```  
  
-   El modificador `thread` puede especificarse únicamente en elementos de datos con la extensión `static`. Entre ellos se incluyen objetos de datos globales (tanto `static` como `extern`), objetos estáticos locales y miembros de datos estáticos de clases C++. Los objetos de datos automáticos no pueden declararse con el atributo `thread`. El código siguiente genera errores del compilador:  
  
    ```  
  
    void func1()  
    {  
        __declspec( thread )int tls_i;            // This will generate an error.  
    }  
  
    int func2(__declspec( thread )int tls_i )    // This will generate an error.  
    {  
        return tls_i;  
    }  
    ```  
  
-   Todas las declaraciones y la definición de un objeto local para el subproceso deben especificar el atributo `thread`. Por ejemplo, el siguiente código genera un error:  
  
    ```  
    #define Thread  __declspec( thread )  
    extern int tls_i;        // This will generate an error, since the  
    int __declspec( thread )tls_i;        // declaration and definition differ.  
    ```  
  
-   El atributo `thread` no se puede utilizar como modificador de tipo. Por ejemplo, el código siguiente genera un error del compilador:  
  
    ```  
    char __declspec( thread ) *ch;        // Error  
    ```  
  
-   Dado que se permite declarar objetos C++ que usan el atributo `thread`, los dos ejemplos siguientes son semánticamente equivalentes:  
  
    ```  
  
    __declspec( thread ) class B  
    {  
    // Code  
    } BObject;  // OK--BObject is declared thread local.  
  
    class B  
    {  
    // Code  
    };  
    __declspec( thread ) B BObject;  // OK--BObject is declared thread local.  
    ```  
  
-   La dirección de un objeto local para el subproceso no se considera constante, así como tampoco se considera una expresión constante ninguna expresión en la que intervenga una dirección de ese tipo. En C estándar, el efecto de esto es prohibir el uso de la dirección de una variable local para el subproceso como inicializador para un objeto o puntero. Por ejemplo, el compilador de C marca el código siguiente como erróneo:  
  
    ```  
  
    __declspec( thread )int tls_i;  
    int *p = &tls_i;       //This will generate an error in C.  
    ```  
  
     Esta restricción no se aplica a C++. Como C++ permite la inicialización dinámica de todos los objetos, puede inicializar un objeto mediante una expresión que utiliza la dirección de una variable local para el subproceso. Esto se hace del mismo modo que la construcción de objetos locales para el subproceso. Por ejemplo, el código mostrado anteriormente no genera un error cuando se compila como un archivo de origen de C++. Tenga en cuenta que la dirección de una variable local para el subproceso solo será válida mientras exista el subproceso en el que se obtuvo la dirección.  
  
-   C estándar permite la inicialización de un objeto o de una variable con una expresión que contenga una referencia a sí misma, pero solo para objetos cuyo tamaño no sea estático. Aunque, en general, C++ permite esa inicialización dinámica de objetos con una expresión que contenga una referencia a sí misma, este tipo de inicialización no se permite con objetos locales para el subproceso. Por ejemplo:  
  
    ```  
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++   
    int j = j;                               // OK in C++, error in C  
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++  
    ```  
  
     Tenga en cuenta que una expresión `sizeof` que incluye el objeto que se está inicializando no representa una referencia a sí misma y se permite en C y en C++.  
  
     C++ no permite este tipo de inicialización dinámica de datos de subproceso debido a posibles mejoras futuras en el servicio de almacenamiento local para el subproceso.  
  
-   En sistemas operativos de Windows anteriores a [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)], `__declspec`(thread) tiene algunas limitaciones. Si una DLL declara cualquier dato u objeto como `__declspec`(thread), puede producir un error de protección si se carga dinámicamente. Después de carga el archivo DLL mediante [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175), se producirá un error del sistema siempre que el código hace referencia el `__declspec`datos (subproceso). Como el espacio para variables globales de un subproceso se asigna en tiempo de ejecución, el tamaño de este espacio se basa en un cálculo de los requisitos de la aplicación más los requisitos de todas las DLL que se vinculan estáticamente. Cuando se utiliza `LoadLibrary`, no se puede extender este espacio para albergar las variables locales para el subproceso declaradas con `__declspec`(thread). Use las API de TLS, como [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801), en la DLL para asignar TLS en caso de que se pueden cargar el archivo DLL con `LoadLibrary`.  
  
## <a name="see-also"></a>Vea también  
 [Multithreading con C y Win32](../parallel/multithreading-with-c-and-win32.md)   
