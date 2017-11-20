---
title: Reglas generales y limitaciones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d7295cfad3d5194de6a80a15e8e186089a0f033f
ms.sourcegitcommit: ce115fcfb20b4fbc198f0f7b6d0ca3e94d7ce947
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="general-rules-and-limitations"></a>Reglas generales y limitaciones
## <a name="microsoft-specific"></a>Específicos de Microsoft  
  
-   Si declara una función o un objeto sin el **dllimport** o `dllexport` atributo, la función o el objeto no se considera parte de la interfaz DLL. Por consiguiente, la definición de la función o el objeto debe estar presente en ese módulo o en otro módulo del mismo programa. Para que una función o un objeto formen parte de la interfaz DLL, debe declarar la definición de la función o del objeto en el otro módulo como `dllexport`. De los contrario, se genera un error del vinculador.  
  
     Si declara una función o un objeto con el atributo `dllexport`, su definición debe aparecer en algún módulo del mismo programa. De los contrario, se genera un error del vinculador.  
  
-   Si un solo módulo del programa contiene **dllimport** y `dllexport` declaraciones para la misma función u objeto, el `dllexport` atributo tiene prioridad sobre la **dllimport** atributo. Sin embargo, se genera una advertencia del compilador. Por ejemplo:  
  
    ```  
    __declspec( dllimport ) int i;  
    __declspec( dllexport ) int i;   // Warning; inconsistent;  
                                     // dllexport takes precedence.  
    ```  
  
-   En C++, puede inicializar un puntero de datos local estático o declarado globalmente o con la dirección de un objeto de datos declarado con el **dllimport** atributo, que genera un error en C. Además, puede inicializar un puntero de función local estático con la dirección de una función declarada con el **dllimport** atributo. En C, esta asignación establece el puntero en la dirección del código thunk de importación de DLL (un código auxiliar que transfiere el control a la función) en lugar de en la dirección de la función. En C++, establece el puntero en la dirección de la función. Por ejemplo:  
  
    ```  
    __declspec( dllimport ) void func1( void );  
    __declspec( dllimport ) int i;  
  
    int *pi = &i;                             // Error in C  
    static void ( *pf )( void ) = &func1;     // Address of thunk in C,  
                                              // function in C++  
  
    void func2()  
    {  
       static int *pi = &i;                  // Error in C  
       static void ( *pf )( void ) = &func1; // Address of thunk in C,  
                                             // function in C++  
    }  
    ```  
  
     Sin embargo, como un programa que incluya el atributo `dllexport` en la declaración de un objeto debe proporcionar la definición de ese objeto en alguna parte del programa, puede inicializar un puntero de función estático global o local con la dirección de una función `dllexport`. De igual forma, puede inicializar un puntero de datos estático global o local con la dirección de un objeto de datos `dllexport`. Por ejemplo, el código siguiente no genera errores en C ni en C++:  
  
    ```  
    __declspec( dllexport ) void func1( void );  
    __declspec( dllexport ) int i;  
  
    int *pi = &i;                              // Okay  
    static void ( *pf )( void ) = &func1;      // Okay  
  
    void func2()  
    {  
        static int *pi = &i;                   // Okay  
        static void ( *pf )( void ) = &func1;  // Okay  
    }  
    ```  
  
-   Si aplica `dllexport` a una clase normal que tiene una clase base que no está marcada como `dllexport`, el compilador generará la advertencia C4275.  
  
     El compilador genera la misma advertencia si la clase base es una especialización de una plantilla de clase. Para solucionar este problema, marque la clase base con `dllexport`. El problema con una especialización de una plantilla de clase es dónde se debe colocar el **__declspec (dllexport)**; no tiene permiso para marcar la plantilla de clase. En lugar de ello, cree explícitamente una instancia de la plantilla de clase y marque esta instancia explícita con `dllexport`. Por ejemplo:  
  
    ```  
    template class __declspec(dllexport) B<int>;  
    class __declspec(dllexport) D : public B<int> {  
    // ...  
    ```  
  
     Esta solución no funciona si el argumento de la plantilla es la clase de la que se deriva. Por ejemplo:  
  
    ```  
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
     Como este es un patrón común con plantillas, el compilador cambió la semántica de `dllexport` cuando se aplica a una clase que tiene una o más clases base y cuando una o más de las clases base es una especialización de una plantilla de clase. En este caso, el compilador aplica implícitamente `dllexport` a las especializaciones de plantillas de clase. Puede hacer lo siguiente y no recibir una advertencia:  
  
    ```  
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)