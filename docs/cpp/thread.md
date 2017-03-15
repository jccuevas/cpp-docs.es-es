---
title: "subproceso | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "thread"
  - "thread_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], subproceso"
  - "thread __declspec (palabra clave)"
  - "almacenamiento local de subprocesos (TLS)"
  - "TLS (almacenamiento local de subprocesos), Implementación del compilador"
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# subproceso
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 El modificador de clase de almacenamiento extendida **thread** se usa para declarar una variable local de subproceso.  Para el portable equivalente en C\+\+11, use el especificador de clase de almacenamiento [thread\_local](../cpp/storage-classes-cpp.md#thread_local).  
  
## Sintaxis  
  
```  
  
__declspec( thread ) declarator  
```  
  
## Comentarios  
 El almacenamiento local de subprocesos \(TLS\) es el mecanismo por el que cada subproceso de un proceso con varios subprocesos asigna almacenamiento para los datos específicos de ese subproceso.  En los programas multiproceso estándar, los datos se comparten entre todos los subprocesos de un proceso dado, mientras que el almacenamiento local de subprocesos es el mecanismo para asignar datos por subproceso.  Para obtener un análisis completo de los subprocesos, vea [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 Las declaraciones de variables locales de subproceso deben utilizar la [sintaxis de atributos extendida](../cpp/declspec.md) y la palabra clave `__declspec` con la palabra clave **thread**.  Por ejemplo, el código siguiente declara una variable local de subproceso de entero y la inicializa con un valor:  
  
```  
__declspec( thread ) int tls_i = 1;  
```  
  
 Debe seguir estas instrucciones cuando declare objetos y variables locales de subproceso:  
  
-   Solo puede aplicar el atributo **thread** a las declaraciones y definiciones de datos y a clases; **thread** no se puede usar en declaraciones o definiciones de función.  
  
-   El uso del atributo **thread** puede interferir con la [carga de retraso](../build/reference/linker-support-for-delay-loaded-dlls.md) de importaciones de DLL**.**  
  
-   En los sistemas XP, puede que `thread` no funcione correctamente si un archivo DLL usa datos de \_\_declspec\(thread\) y se carga dinámicamente mediante LoadLibrary.  
  
-   Solo puede especificar el atributo **thread** en elementos de datos con duración de almacenamiento estática.  Entre estos se incluyen objetos de datos globales \(tanto **static** como `extern`\), objetos estáticos locales y miembros de datos estáticos de clases.  No puede declarar objetos de datos automáticos con el atributo **thread**.  
  
-   Debe utilizar el atributo **thread** para la declaración y definición de un objeto local de subproceso, tanto si la declaración y la definición se realizan en el mismo archivo como en archivos distintos.  
  
-   No puede usar el atributo **thread** como modificador de tipo.  
  
-   Como la declaración de objetos que usan el atributo **thread** está permitida, los dos ejemplos siguientes son semánticamente equivalentes:  
  
    ```  
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
  
-   El estándar de C permite la inicialización de un objeto o de una variable con una expresión que contenga una referencia a sí misma, pero solo para objetos cuyo tamaño no sea estático.  Aunque, generalmente, C\+\+ permite esa inicialización dinámica de objetos con una expresión que contenga una referencia a sí misma, este tipo de inicialización no se permite con objetos locales de un subproceso.  Por ejemplo:  
  
    ```  
    // declspec_thread_3.cpp  
    // compile with: /LD  
    #define Thread __declspec( thread )  
    int j = j;   // Okay in C++; C error  
    Thread int tls_i = sizeof( tls_i );   // Okay in C and C++  
    ```  
  
     Tenga en cuenta que una expresión `sizeof` que incluye el objeto que se está inicializando no representa una referencia a sí misma y se permite en C y en C\+\+.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Almacenamiento local de subprocesos \(TLS\)](../parallel/thread-local-storage-tls.md)