---
title: Almacenamiento local para el subproceso (TLS)
ms.date: 08/09/2019
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
ms.openlocfilehash: 888a33161cd33b20d5f40a07f9b54235f06b8bd8
ms.sourcegitcommit: 57e26bdd7839fce3c4154a61e987d165f0ba6f5b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2020
ms.locfileid: "84301971"
---
# <a name="thread-local-storage-tls"></a>Almacenamiento local para el subproceso (TLS)

El almacenamiento local para el subproceso (TLS) es el método por el que cada subproceso de un determinado proceso con subprocesos puede asignar ubicaciones en las que almacenar los datos específicos de esos subprocesos. Los datos específicos de subprocesos enlazados dinámicamente (en tiempo de ejecución) se admiten por medio de la API de TLS ([TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)). Win32 y el compilador de Microsoft C++ ahora admiten datos enlazados estáticamente (en tiempo de carga) por subproceso, además de la implementación de API existente.

## <a name="compiler-implementation-for-tls"></a><a name="_core_compiler_implementation_for_tls"></a>Implementación del compilador para TLS

**C++ 11:**  El `thread_local` especificador de clase de almacenamiento es el método recomendado para especificar el almacenamiento local de subprocesos para objetos y miembros de clase. Para obtener más información, vea [clases de almacenamiento (C++)](../cpp/storage-classes-cpp.md).

MSVC también proporciona un atributo específico de Microsoft, [subproceso](../cpp/thread.md), como modificador de clase de almacenamiento extendido. Use la palabra clave **__declspec** para declarar una variable de **subproceso** . Por ejemplo, el código siguiente declara una variable local de subproceso de entero y la inicializa con un valor:

```C
__declspec( thread ) int tls_i = 1;
```

## <a name="rules-and-limitations"></a>Reglas y limitaciones

Deben tenerse en cuenta las siguientes instrucciones cuando se declaran objetos y variables locales para el subproceso enlazados estáticamente. Estas instrucciones se aplican tanto al [subproceso](../cpp/thread.md) como a [thread_local](../cpp/storage-classes-cpp.md):

- El atributo **Thread** solo se puede aplicar a las declaraciones y definiciones de datos y clases. No se puede usar en declaraciones o definiciones de función. Por ejemplo, el código siguiente genera un error del compilador:

    ```C
    __declspec( thread )void func();     // This will generate an error.
    ```

- El modificador de **subproceso** solo se puede especificar en elementos de datos con extensión **estática** . Esto incluye objetos de datos globales (tanto **estáticos** como **externos**), objetos estáticos locales y miembros de datos estáticos de clases de C++. Los objetos de datos automáticos no se pueden declarar con el atributo **Thread** . El código siguiente genera errores del compilador:

    ```C
    void func1()
    {
        __declspec( thread )int tls_i;            // This will generate an error.
    }

    int func2(__declspec( thread )int tls_i )     // This will generate an error.
    {
        return tls_i;
    }
    ```

- Todas las declaraciones y la definición de un objeto local de subproceso deben especificar el atributo **Thread** . Por ejemplo, el siguiente código genera un error:

    ```C
    #define Thread  __declspec( thread )
    extern int tls_i;        // This will generate an error, since the
    int __declspec( thread )tls_i;        // declaration and definition differ.
    ```

- No se puede usar el atributo **Thread** como modificador de tipo. Por ejemplo, el código siguiente genera un error del compilador:

    ```C
    char __declspec( thread ) *ch;        // Error
    ```

- Dado que se permite la declaración de objetos de C++ que usan el atributo **Thread** , los dos ejemplos siguientes son semánticamente equivalentes:

    ```cpp
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

- La dirección de un objeto local de subproceso no se considera constante y cualquier expresión que contenga una dirección de este tipo no se considera una expresión constante. En el estándar C, el efecto es impedir el uso de la dirección de una variable local de subproceso como inicializador para un objeto o puntero. Por ejemplo, el compilador de C marca el código siguiente como erróneo:

    ```C
    __declspec( thread ) int tls_i;
    int *p = &tls_i;       //This will generate an error in C.
    ```

   Esta restricción no se aplica en C++. Como C++ permite la inicialización dinámica de todos los objetos, puede inicializar un objeto mediante una expresión que utiliza la dirección de una variable local para el subproceso. Se realiza igual que la construcción de objetos locales de subproceso. Por ejemplo, el código mostrado anteriormente no genera un error cuando se compila como un archivo de código fuente de C++. La dirección de una variable local de subproceso solo es válida siempre y cuando el subproceso en el que se tomó la dirección todavía exista.

- Standard C permite la inicialización de un objeto o una variable con una expresión que implique una referencia a sí misma, pero solo para objetos de extensión no estática. Aunque C++ generalmente permite la inicialización dinámica de objetos con una expresión que implique una referencia a sí misma, este tipo de inicialización no se permite con objetos locales de subproceso. Por ejemplo:

    ```C
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++
    int j = j;                               // OK in C++, error in C
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++
    ```

   Una `sizeof` expresión que incluye el objeto que se está inicializando no representa una referencia a sí misma y está habilitada en C y C++.

   C++ no permite la inicialización dinámica de datos de subprocesos debido a posibles mejoras futuras en el servicio de almacenamiento local para el subproceso.

- En los sistemas operativos Windows anteriores a Windows Vista, `__declspec( thread )` tiene algunas limitaciones. Si un archivo DLL declara cualquier dato u objeto como `__declspec( thread )` , puede producirse un error de protección si se carga dinámicamente. Una vez cargado el archivo DLL con [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw), se produce un error del sistema cada vez que el código hace referencia a los `__declspec( thread )` datos. Como el espacio para variables globales de un subproceso se asigna en tiempo de ejecución, el tamaño de este espacio se basa en un cálculo de los requisitos de la aplicación más los requisitos de todas las DLL que se vinculan estáticamente. Cuando se usa `LoadLibrary` , no se puede extender este espacio para permitir las variables locales de subproceso declaradas con `__declspec( thread )` . Use las API de TLS, como [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc), en el archivo DLL para asignar TLS si el archivo dll se puede cargar con `LoadLibrary` .

## <a name="see-also"></a>Consulte también

[Subprocesamiento múltiple con C y Win32](multithreading-with-c-and-win32.md)
