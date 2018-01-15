---
title: Almacenamiento local para el subproceso | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- thread-local variables
- TLS (thread local storage)
- thread storage-class attribute
- thread-local storage
- storage, thread local storage
ms.assetid: a0f1b109-c953-4079-aa10-e47f5483173d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1eef6199f67702aeb3d3a886c52e910302a7dcad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="thread-local-storage"></a>Almacenamiento local para el subproceso
**Específicos de Microsoft**  
  
 El almacenamiento local de subprocesos (TLS) es el mecanismo por el que cada subproceso de un proceso con un subproceso determinado asigna almacenamiento para los datos específicos de ese subproceso. En los programas multiproceso estándar, los datos se comparten entre todos los subproceso de un proceso dado, mientras que el almacenamiento local para el subproceso es el mecanismo para asignar datos por subproceso. Para obtener un análisis completo de subprocesos, vea [Procesos y subprocesos](http://msdn.microsoft.com/library/windows/desktop/ms684841) en [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 El lenguaje C de Microsoft incluye el atributo extendido de clase de almacenamiento, thread, que se utiliza con la palabra clave __declspec para declarar una variable local para el subproceso. Por ejemplo, el código siguiente declara una variable local de subproceso de entero y la inicializa con un valor:  
  
```  
__declspec( thread ) int tls_i = 1;  
```  
  
 Deben tenerse en cuenta estas instrucciones cuando se declaran variables locales para el subproceso enlazadas estáticamente:  
  
-   Las variables locales de subprocesos que dispongan de la inicialización dinámica solo se inicializan en el subproceso que provoque la carga del elemento DLL y los subprocesos que ya se estén ejecutando en el proceso. Para obtener más información, consulte el [subproceso](../cpp/thread.md).  
  
-   Puede aplicar el atributo thread solamente a declaraciones y definiciones de datos. No se puede utilizar en declaraciones o definiciones de función. Por ejemplo, el código siguiente genera un error del compilador:  
  
    ```  
    #define Thread   __declspec( thread )  
    Thread void func();      /* Error */  
    ```  
  
-   Solo puede especificar el atributo thread en elementos de datos con duración de almacenamiento estática. Esto incluye datos globales (tanto estáticos como externos) y datos estáticos locales. No puede declarar datos automáticos con el atributo thread. Por ejemplo, el código siguiente genera errores del compilador:  
  
    ```  
    #define Thread   __declspec( thread )  
    void func1()  
    {  
        Thread int tls_i;            /* Error */  
    }  
  
    int func2( Thread int tls_i )    /* Error */  
    {  
       return tls_i;  
    }  
    ```  
  
-   Debe utilizar el atributo thread para la declaración y definición de datos locales de subproceso, con independencia de que la declaración y la definición se produzcan en el mismo archivo o en archivos distintos. Por ejemplo, el siguiente código genera un error:  
  
    ```  
    #define Thread   __declspec( thread )  
    extern int tls_i;     /* This generates an error, because the   */  
    int Thread tls_i;     /* declaration and the definition differ. */  
    ```  
  
-   No puede usar el atributo thread como modificador de tipo. Por ejemplo, el código siguiente genera un error del compilador:  
  
    ```  
    char *ch __declspec( thread );      /* Error */  
    ```  
  
-   La dirección de una variable local de subproceso no se considera constante, ni tampoco se considera una expresión de constante una expresión en la que intervenga una dirección de ese tipo. Esto significa que no puede utilizar la dirección de una variable local de subproceso como inicializador para un puntero. Por ejemplo, el compilador marca el código siguiente como erróneo:  
  
    ```  
    #define Thread   __declspec( thread )  
    Thread int tls_i;  
    int *p = &tls_i;      /* Error */  
    ```  
  
-   C permite la inicialización de una variable con una expresión que contenga una referencia a sí misma, pero solo para objetos cuyo tamaño no sea estático. Por ejemplo:  
  
    ```  
    #define Thread   __declspec( thread )  
    Thread int tls_i = tls_i;             /* Error */  
    int j = j;                            /* Error */  
    Thread int tls_i = sizeof( tls_i )    /* Okay  */  
    ```  
  
     Observe que una expresión sizeof que incluye la variable que se va inicializar no constituye una referencia a sí misma y está permitida.  
  
-   El uso del atributo **__declspec(thread)** puede interferir con la [carga de retraso](../build/reference/linker-support-for-delay-loaded-dlls.md) de importaciones de DLL**.**  
  
 Para más información sobre cómo utilizar el atributo thread, vea [Temas de multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Atributos extendidos de clase de almacenamiento de C](../c-language/c-extended-storage-class-attributes.md)