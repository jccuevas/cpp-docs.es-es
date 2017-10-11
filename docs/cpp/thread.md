---
title: subproceso | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- thread_cpp
dev_langs:
- C++
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: f460497071445cff87308fa9bf6e0d43c6f13a3e
ms.openlocfilehash: 7261dc1d6d76eeac8a6b2959bc9bb6fc3c98a66e
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="thread"></a>subproceso

**Específicos de Microsoft**  
El **subproceso** modificador de clase de almacenamiento extendida se utiliza para declarar una variable local de subproceso. Para la función portable equivalente en C ++ 11 y versiones posterior, use la [thread_local](../cpp/storage-classes-cpp.md#thread_local) especificador de clase de almacenamiento.

## <a name="syntax"></a>Sintaxis

```
__declspec( thread ) declarator
```

## <a name="remarks"></a>Comentarios

El almacenamiento local de subprocesos (TLS) es el mecanismo por el que cada subproceso de un proceso con varios subprocesos asigna almacenamiento para los datos específicos de ese subproceso. En los programas multiproceso estándar, los datos se comparten entre todos los subproceso de un proceso dado, mientras que el almacenamiento local para el subproceso es el mecanismo para asignar datos por subproceso. Para obtener una explicación completa de subprocesos, vea [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Las declaraciones de variables locales de subproceso deben utilizar [extendidos la sintaxis de atributo](../cpp/declspec.md) y `__declspec` palabra clave con el **subproceso** (palabra clave). Por ejemplo, el código siguiente declara una variable local de subproceso de entero y la inicializa con un valor:

```cpp
__declspec( thread ) int tls_i = 1;  
```

Debe seguir estas instrucciones cuando declare objetos y variables locales para el subproceso:

- Puede aplicar el **subproceso** atributo únicamente a la clase y las declaraciones de datos y de las definiciones; **subproceso** no se puede usar en declaraciones de función o definiciones.

- El uso de la **subproceso** atributo puede interferir con [carga retrasada](../build/reference/linker-support-for-delay-loaded-dlls.md) de importaciones de DLL.

- En los sistemas XP, **subproceso** podría no funcionar correctamente si un archivo DLL usa datos de __declspec (Thread) y se carga dinámicamente mediante LoadLibrary.

- Puede especificar el **subproceso** atributo solamente a los elementos de datos con duración de almacenamiento estática. Esto incluye los objetos de datos globales (tanto **estático** y **extern**), objetos estáticos locales y miembros de datos estáticos de clases. No se puede declarar objetos de datos automáticos con el **subproceso** atributo.

- Debe utilizar el **subproceso** de atributo para la declaración y la definición de un objeto local de subproceso, tanto si la declaración y la definición se realizan en el mismo archivo o archivos independientes.

- No se puede utilizar el **subproceso** atributo como modificador de tipo.

- Puesto que la declaración de objetos que utilizan el **subproceso** se permite el atributo, los dos ejemplos siguientes son semánticamente equivalentes:

    ```cpp
    // declspec_thread_2.cpp
    // compile with: /LD
    __declspec( thread ) class B {
    public:
       int data;
    } BObject;   // BObject declared thread local.

    class B2 {
    public:
       int data;
    };
    __declspec( thread ) B2 BObject2;   // BObject2 declared thread local.
    ```

- El estándar de C permite la inicialización de un objeto o de una variable con una expresión que contenga una referencia a sí misma, pero solo para objetos cuyo tamaño no sea estático. Aunque, generalmente, C++ permite esa inicialización dinámica de objetos con una expresión que contenga una referencia a sí misma, este tipo de inicialización no se permite con objetos locales de un subproceso. Por ejemplo:

    ```cpp
    // declspec_thread_3.cpp
    // compile with: /LD
    #define Thread __declspec( thread )
    int j = j;   // Okay in C++; C error
    Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
    ```

     Tenga en cuenta que un **sizeof** expresión que incluye el objeto que se está inicializando no constituye una referencia a sí misma y se permite en C y C++.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)  
[Palabras clave](../cpp/keywords-cpp.md)  
[Almacenamiento local de subprocesos (TLS)](../parallel/thread-local-storage-tls.md)

