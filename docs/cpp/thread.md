---
title: thread
ms.date: 05/07/2019
f1_keywords:
- thread_cpp
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
ms.openlocfilehash: cc21602764a9a3c2584bdd7da62c75974ffdd5fb
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301293"
---
# <a name="thread"></a>thread

**Específicos de Microsoft**

El modificador de clase de almacenamiento Extended de **subproceso** se usa para declarar una variable local de subproceso. Para el equivalente portable en C++ 11 y versiones posteriores, use el especificador de clase de almacenamiento [thread_local](../cpp/storage-classes-cpp.md#thread_local) para el código portable. En Windows **thread_local** se implementa con **__declspec (subproceso)** .

## <a name="syntax"></a>Sintaxis

*declarador* **__declspec (Thread)**

## <a name="remarks"></a>Notas

El almacenamiento local para el subproceso (TLS) es el mecanismo por el que cada subproceso de un proceso con varios subproceso asigna almacenamiento para los datos específicos de ese subproceso. En los programas multiproceso estándar, los datos se comparten entre todos los subproceso de un proceso dado, mientras que el almacenamiento local para el subproceso es el mecanismo para asignar datos por subproceso. Para obtener una descripción completa de los subprocesos, vea [multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Las declaraciones de variables locales de subproceso deben utilizar la [Sintaxis de atributo extendido](../cpp/declspec.md) y la palabra clave **__declspec** con la palabra clave **Thread** . Por ejemplo, el código siguiente declara una variable local de subproceso de entero y la inicializa con un valor:

```cpp
__declspec( thread ) int tls_i = 1;
```

Al usar variables locales de subproceso en bibliotecas cargadas dinámicamente, debe tener en cuenta los factores que pueden hacer que una variable local de subproceso no se inicialice correctamente:

1. Si la variable se inicializa con una llamada de función (incluidos los constructores), solo se llamará a esta función para el subproceso que provocó la carga del archivo binario o DLL en el proceso, y para los subprocesos que se iniciaron después de cargar el archivo binario o DLL. No se llama a las funciones de inicialización para ningún otro subproceso que ya se estaba ejecutando cuando se cargó el archivo DLL. La inicialización dinámica se produce en la llamada DllMain para DLL_THREAD_ATTACH, pero el archivo DLL nunca recibe ese mensaje si la DLL no está en el proceso cuando se inicia el subproceso.

1. Las variables locales de subproceso que se inicializan estáticamente con valores constantes normalmente se inicializan correctamente en todos los subprocesos. Sin embargo, a partir del 2017 de diciembre hay un problema de conformidad conocido en el C++ compilador de Microsoft, en el que las variables **constexpr** reciben Dynamic en lugar de una inicialización estática.

   Nota: se espera que ambos problemas se solucionen en futuras actualizaciones del compilador.

Además, debe seguir estas instrucciones al declarar objetos y variables locales para el subproceso:

- Solo puede aplicar el atributo **Thread** a las declaraciones y definiciones de clase y datos; el **subproceso** no se puede usar en declaraciones o definiciones de función.

- Solo puede especificar el atributo **Thread** en elementos de datos con duración de almacenamiento estática. Esto incluye objetos de datos globales (tanto **estáticos** como **externos**), objetos estáticos locales y miembros de datos estáticos de clases. No se pueden declarar objetos de datos automáticos con el atributo **Thread** .

- Debe utilizar el atributo **Thread** para la declaración y la definición de un objeto local de subproceso, ya sea que la declaración y la definición se produzcan en el mismo archivo o en archivos independientes.

- No se puede usar el atributo **Thread** como modificador de tipo.

- Dado que se permite la declaración de objetos que usan el atributo **Thread** , estos dos ejemplos son semánticamente equivalentes:

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

- Estándar C permite la inicialización de un objeto o una variable con una expresión que contenga una referencia a sí misma, pero solo para objetos no estáticos. Aunque C++ normalmente permite la inicialización dinámica de un objeto con una expresión que contenga una referencia a sí misma, este tipo de inicialización no se permite con objetos locales de subproceso. Por ejemplo:

   ```cpp
   // declspec_thread_3.cpp
   // compile with: /LD
   #define Thread __declspec( thread )
   int j = j;   // Okay in C++; C error
   Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
   ```

   Una expresión **sizeof** que incluye el objeto que se va a inicializar no constituye una referencia a sí misma y se permite en C++C y.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Almacenamiento local de subprocesos (TLS)](../parallel/thread-local-storage-tls.md)