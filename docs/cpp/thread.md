---
title: subproceso | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 80ea212f8c888680edf50e269c89e62988a0ee36
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104392"
---
# <a name="thread"></a>subproceso

**Específicos de Microsoft**

El **subproceso** modificador de clase de almacenamiento extendidos se usa para declarar una variable local de subproceso. Para el portable equivalente en C ++ 11 y versiones posterior, utilice el [thread_local](../cpp/storage-classes-cpp.md#thread_local) especificador de clase de almacenamiento para el código portable. En Windows `thread_local` se implementa con **__declspec (Thread)**.

## <a name="syntax"></a>Sintaxis

> **__declspec (thread)** *declarador*

## <a name="remarks"></a>Comentarios

El almacenamiento local para el subproceso (TLS) es el mecanismo por el que cada subproceso de un proceso con varios subproceso asigna almacenamiento para los datos específicos de ese subproceso. En los programas multiproceso estándar, los datos se comparten entre todos los subproceso de un proceso dado, mientras que el almacenamiento local para el subproceso es el mecanismo para asignar datos por subproceso. Para obtener una explicación completa de los subprocesos, vea [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Deben usar las declaraciones de variables locales del subproceso [sintaxis de atributo extendida](../cpp/declspec.md) y **__declspec** palabra clave with el **subproceso** palabra clave. Por ejemplo, el código siguiente declara una variable local de subproceso de entero y la inicializa con un valor:

```cpp
__declspec( thread ) int tls_i = 1;
```

Al usar variables locales de subproceso en bibliotecas de carga dinámica, es preciso tener en cuenta los factores que pueden hacer que una variable local de subproceso no se inicialicen correctamente:

1. Si la variable se inicializa con una llamada de función (incluidos constructores), solo se llamará a esta función para el subproceso que produjo el archivo binario o DLL cargar en el proceso y para esos subprocesos que se inició después de que se cargó el archivo binario o DLL. Las funciones de inicialización no se llama a ningún otro subproceso que ya se estaba ejecutando cuando se cargó la DLL. Inicialización dinámica produce en la llamada de DllMain para DLL_THREAD_ATTACH, pero el archivo DLL nunca obtiene que si el archivo DLL no está en el proceso cuando se inicia el subproceso del mensaje.

1. Por lo general, las variables locales del subproceso que se inicializan estáticamente con valores constantes se inicializan correctamente en todos los subprocesos. Sin embargo, a partir de diciembre de 2017 hay un problema conocido de conformidad del compilador de Microsoft Visual C++ mediante el cual recepción las variables constexpr dinámica en lugar de la inicialización estática.

   Nota: Estos problemas se esperan que se solucione en futuras actualizaciones del compilador.

Además, debe seguir estas instrucciones al declarar variables y objetos locales de subproceso:

- Puede aplicar el **subproceso** atributo solo a la clase y las declaraciones de datos y las definiciones; **subproceso** no puede usarse en definiciones o declaraciones de función.

- Puede especificar el **subproceso** atributo solo en los elementos de datos con duración de almacenamiento estática. Esto incluye los objetos de datos globales (tanto **estático** y **extern**), objetos estáticos locales y miembros de datos estáticos de clases. No se puede declarar objetos de datos automáticos con el **subproceso** atributo.

- Debe usar el **subproceso** atributo para la declaración y la definición de un objeto de subproceso local, si la declaración y definición que se producen en el mismo archivo o archivos independientes.

- No puede usar el **subproceso** atributo como un modificador de tipo.

- Puesto que la declaración de objetos que utilizan el **subproceso** se permite el atributo, estos dos ejemplos son semánticamente equivalentes:

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

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Almacenamiento local de subprocesos (TLS)](../parallel/thread-local-storage-tls.md)