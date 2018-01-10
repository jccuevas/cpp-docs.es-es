---
title: subproceso | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: thread_cpp
dev_langs: C++
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b26487e7f5f11bb32f418b438e9d0396b5854a91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="thread"></a>subproceso

**Específicos de Microsoft**  
El **subproceso** modificador de clase de almacenamiento extendida se utiliza para declarar una variable local de subproceso. Para la función portable equivalente en C ++ 11 y versiones posterior, use la [thread_local](../cpp/storage-classes-cpp.md#thread_local) especificador de clase de almacenamiento para el código portable. En Windows **thread_local** se implementa con **__declspec (Thread)**.

## <a name="syntax"></a>Sintaxis

```
__declspec( thread ) declarator
```

## <a name="remarks"></a>Comentarios

El almacenamiento local para el subproceso (TLS) es el mecanismo por el que cada subproceso de un proceso con varios subproceso asigna almacenamiento para los datos específicos de ese subproceso. En los programas multiproceso estándar, los datos se comparten entre todos los subproceso de un proceso dado, mientras que el almacenamiento local para el subproceso es el mecanismo para asignar datos por subproceso. Para obtener una explicación completa de subprocesos, vea [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Las declaraciones de variables locales de subproceso deben utilizar [extendidos la sintaxis de atributo](../cpp/declspec.md) y `__declspec` palabra clave con el **subproceso** (palabra clave). Por ejemplo, el código siguiente declara una variable local de subproceso de entero y la inicializa con un valor:

```cpp
__declspec( thread ) int tls_i = 1;  
```

Cuando use variables locales de subproceso en las bibliotecas que se cargan dinámicamente, debe tener en cuenta los factores que pueden causar una variable local de subproceso no se inicialice correctamente:

1) Si la variable se inicializa con una llamada de función (incluidos constructores), solo se llamará a esta función para el subproceso que produjo el binario o la DLL cargar en el proceso y para esos subprocesos que se inició después de que se cargó el archivo binario o la DLL. No se llaman a las funciones de inicialización para ningún otro subproceso que ya se estaba ejecutando cuando se cargó la DLL. Inicialización dinámica produce en la llamada de DllMain para DLL_THREAD_ATTACH, pero el archivo DLL nunca obtiene que si el archivo DLL no se encuentra en el proceso cuando se inicia el subproceso del mensaje. 

2) Por lo general, las variables locales de subproceso que se inicializan estáticamente con valores constantes se inicializan correctamente en todos los subprocesos. Sin embargo, a partir de diciembre de 2017 hay un problema conocido de conformidad en el compilador de Microsoft C++ mediante el cual variables constexpr recepción dinámica en lugar de inicialización estática.  
  
   Nota: Estos dos problemas se esperan que se solucione en futuras actualizaciones del compilador.


Además, debe seguir estas instrucciones cuando declare variables y objetos locales de subproceso:

- Puede aplicar el **subproceso** atributo únicamente a la clase y las declaraciones de datos y de las definiciones; **subproceso** no se puede usar en declaraciones de función o definiciones.

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
