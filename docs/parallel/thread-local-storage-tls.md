---
title: Almacenamiento Local (TLS) para el subproceso | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6744fdd80e16e292399a261e10dc6b974af1dca4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46371932"
---
# <a name="thread-local-storage-tls"></a>Almacenamiento local para el subproceso (TLS)

El almacenamiento local para el subproceso (TLS) es el método por el que cada subproceso de un determinado proceso con subproceso puede asignar ubicaciones en las que almacenar los datos específicos de esos subproceso. Datos específicos del subproceso de límite (tiempo de ejecución) se admiten dinámicamente por medio de la API de TLS ([TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc).  Win32 y el compilador de Visual C++ ahora son compatibles con datos por subproceso que se enlazan estáticamente (en tiempo de carga) además de la implementación existente de la API.

##  <a name="_core_compiler_implementation_for_tls"></a> Implementación del compilador de TLS

**C ++ 11:** el `thread_local` especificador de clase de almacenamiento es la manera recomendada para especificar el almacenamiento local de subprocesos para los objetos y miembros de clase. Para obtener más información, consulte [clases de almacenamiento (C++)](../cpp/storage-classes-cpp.md).

Visual C++ también proporciona un atributo específico de Microsoft, [subproceso](../cpp/thread.md), como modificador de clase de almacenamiento extendida. Use la **__declspec** palabra clave para declarar un **subproceso** variable. Por ejemplo, el código siguiente declara una variable local de subproceso de entero y la inicializa con un valor:

```
__declspec( thread ) int tls_i = 1;
```

## <a name="rules-and-limitations"></a>Reglas y limitaciones

Deben tenerse en cuenta las siguientes instrucciones cuando se declaran objetos y variables locales para el subproceso enlazados estáticamente. Estas instrucciones aplican tanto a [subproceso](../cpp/thread.md)y también en su mayor parte a [thread_local](../cpp/storage-classes-cpp.md):

- El **subproceso** atributo puede aplicarse solo a definiciones y declaraciones de clase y los datos. No se puede utilizar en declaraciones o definiciones de función. Por ejemplo, el código siguiente genera un error del compilador:

    ```
    __declspec( thread )void func();     // This will generate an error.
    ```

- El **subproceso** modificador puede especificarse solamente en los elementos de datos con **estático** extensión. Esto incluye los objetos de datos globales (tanto **estático** y **extern**), objetos estáticos locales y miembros de datos estáticos de clases de C++. No se pueden declarar objetos de datos automáticos con el **subproceso** atributo. El código siguiente genera errores del compilador:

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

- Las declaraciones y la definición de un subproceso objeto local debe especificar el **subproceso** atributo. Por ejemplo, el siguiente código genera un error:

    ```
    #define Thread  __declspec( thread )
    extern int tls_i;        // This will generate an error, since the
    int __declspec( thread )tls_i;        // declaration and definition differ.
    ```

- El **subproceso** atributo no puede utilizarse como un modificador de tipo. Por ejemplo, el código siguiente genera un error del compilador:

    ```
    char __declspec( thread ) *ch;        // Error
    ```

- Dado que la declaración de C++, los objetos que utilizan el **subproceso** se permite el atributo, los dos ejemplos siguientes son semánticamente equivalentes:

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

- La dirección de un objeto local para el subproceso no se considera constante, así como tampoco se considera una expresión constante ninguna expresión en la que intervenga una dirección de ese tipo. En C estándar, el efecto de esto es prohibir el uso de la dirección de una variable local para el subproceso como inicializador para un objeto o puntero. Por ejemplo, el compilador de C marca el código siguiente como erróneo:

    ```
    __declspec( thread )int tls_i;
    int *p = &tls_i;       //This will generate an error in C.
    ```

     Esta restricción no se aplica a C++. Como C++ permite la inicialización dinámica de todos los objetos, puede inicializar un objeto mediante una expresión que utiliza la dirección de una variable local para el subproceso. Esto se hace del mismo modo que la construcción de objetos locales para el subproceso. Por ejemplo, el código mostrado anteriormente no genera un error cuando se compila como un archivo de origen de C++. Tenga en cuenta que la dirección de una variable local para el subproceso solo será válida mientras exista el subproceso en el que se obtuvo la dirección.

- C estándar permite la inicialización de un objeto o de una variable con una expresión que contenga una referencia a sí misma, pero solo para objetos cuyo tamaño no sea estático. Aunque, en general, C++ permite esa inicialización dinámica de objetos con una expresión que contenga una referencia a sí misma, este tipo de inicialización no se permite con objetos locales para el subproceso. Por ejemplo:

    ```
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++
    int j = j;                               // OK in C++, error in C
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++
    ```

     Tenga en cuenta que una expresión `sizeof` que incluye el objeto que se está inicializando no representa una referencia a sí misma y se permite en C y en C++.

     C++ no permite este tipo de inicialización dinámica de datos de subproceso debido a posibles mejoras futuras en el servicio de almacenamiento local para el subproceso.

- En los sistemas operativos de Windows anteriores a Windows Vista, `__declspec`(thread) tiene algunas limitaciones. Si una DLL declara cualquier dato u objeto como `__declspec`(thread), puede producir un error de protección si se carga dinámicamente. Después de carga el archivo DLL mediante [LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175), se producirá un error del sistema siempre que el código hace referencia a la `__declspec`datos (subproceso). Como el espacio para variables globales de un subproceso se asigna en tiempo de ejecución, el tamaño de este espacio se basa en un cálculo de los requisitos de la aplicación más los requisitos de todas las DLL que se vinculan estáticamente. Cuando se utiliza `LoadLibrary`, no se puede extender este espacio para albergar las variables locales para el subproceso declaradas con `__declspec`(thread). Use la API de TLS, como [TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc), en el archivo DLL para asignar TLS si es posible que se puede cargar la DLL con `LoadLibrary`.

## <a name="see-also"></a>Vea también

[Multithreading con C y Win32](multithreading-with-c-and-win32.md)