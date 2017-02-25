---
title: "Reglas y limitaciones generales | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Reglas y limitaciones generales
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
  
-   Si declara una función o un objeto sin el atributo **dllimport** o `dllexport`, la función o el objeto no se consideran parte de la interfaz DLL.  Por consiguiente, la definición de la función o el objeto debe estar presente en ese módulo o en otro módulo del mismo programa.  Para que una función o un objeto formen parte de la interfaz DLL, debe declarar la definición de la función o del objeto en el otro módulo como `dllexport`.  De los contrario, se genera un error del vinculador.  
  
     Si declara una función o un objeto con el atributo `dllexport`, su definición debe aparecer en algún módulo del mismo programa.  De los contrario, se genera un error del vinculador.  
  
-   Si un solo módulo del programa contiene las declaraciones **dllimport** y `dllexport` para la misma función u objeto, el atributo `dllexport` tiene prioridad sobre el atributo **dllimport**.  Sin embargo, se genera una advertencia del compilador.  Por ejemplo:  
  
    ```  
    __declspec( dllimport ) int i;  
    __declspec( dllexport ) int i;   // Warning; inconsistent;  
                                     // dllexport takes precedence.  
    ```  
  
-   En C\+\+, puede inicializar un puntero de datos local estático o declarado globalmente o con la dirección de un objeto de datos declarado con el atributo **dllimport**, lo que genera un error en C.  Asimismo, puede inicializar un puntero de función local estático con la dirección de una función declarada con el atributo **dllimport**.  En C, esta asignación establece el puntero en la dirección del código thunk de importación de DLL \(un código auxiliar que transfiere el control a la función\) en lugar de en la dirección de la función.  En C\+\+, establece el puntero en la dirección de la función.  Por ejemplo:  
  
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
  
     Sin embargo, como un programa que incluya el atributo `dllexport` en la declaración de un objeto debe proporcionar la definición de ese objeto en alguna parte del programa, puede inicializar un puntero de función estático global o local con la dirección de una función `dllexport`.  De igual forma, puede inicializar un puntero de datos estático global o local con la dirección de un objeto de datos `dllexport`.  Por ejemplo, el código siguiente no genera errores en C ni en C\+\+:  
  
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
  
-   Debido a un cambio en el comportamiento introducido en Visual C\+\+ .NET para mejorar la coherencia de la aplicación de `dllexport` entre clases normales y especializaciones de plantillas de clase, si aplica `dllexport` a una clase normal que tenga una clase base que no esté marcada como `dllexport`, el compilador generará la advertencia C4275.  
  
     El compilador genera la misma advertencia si la clase base es una especialización de una plantilla de clase.  Para solucionar este problema, marque la clase base con `dllexport`.  El problema con una especialización de una plantilla de clase es dónde colocar **\_\_declspec\(dllexport\)**; no se permite marcar la plantilla de clase.  En lugar de ello, cree explícitamente una instancia de la plantilla de clase y marque esta instancia explícita con `dllexport`.  Por ejemplo:  
  
    ```  
    template class __declspec(dllexport) B<int>;  
    class __declspec(dllexport) D : public B<int> {  
    // ...  
    ```  
  
     Esta solución no funciona si el argumento de la plantilla es la clase de la que se deriva.  Por ejemplo:  
  
    ```  
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
     Como este es un patrón común con plantillas, el compilador cambió la semántica de `dllexport` cuando se aplica a una clase que tiene una o más clases base y cuando una o más de las clases base es una especialización de una plantilla de clase.  En este caso, el compilador aplica implícitamente `dllexport` a las especializaciones de plantillas de clase.  En Visual C\+\+ .NET, un usuario puede hacer lo siguiente y no recibir una advertencia:  
  
    ```  
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)