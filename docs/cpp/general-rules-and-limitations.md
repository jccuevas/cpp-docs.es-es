---
title: Reglas generales y limitaciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a2a21de2cade8eb0d8776b340123df3535c36f4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034400"
---
# <a name="general-rules-and-limitations"></a>Reglas generales y limitaciones

## <a name="microsoft-specific"></a>Específicos de Microsoft

- Si declara una función o un objeto sin el **dllimport** o **dllexport** atributo, la función o el objeto no se considera parte de la interfaz DLL. Por consiguiente, la definición de la función o el objeto debe estar presente en ese módulo o en otro módulo del mismo programa. Para hacer que el elemento de objeto o función de la interfaz DLL, debe declarar la definición de la función o un objeto en el otro módulo como **dllexport**. De los contrario, se genera un error del vinculador.

     Si declara una función o un objeto con el **dllexport** atributo, su definición debe aparecer en algún módulo del mismo programa. De los contrario, se genera un error del vinculador.

- Si un solo módulo del programa contiene ambos **dllimport** y **dllexport** declaraciones para la misma función u objeto, el **dllexport** atributo tiene prioridad a través de la **dllimport** atributo. Sin embargo, se genera una advertencia del compilador. Por ejemplo:

    ```cpp
    __declspec( dllimport ) int i;
    __declspec( dllexport ) int i;   // Warning; inconsistent;
                                     // dllexport takes precedence.
    ```

- En C++, puede inicializar un puntero de datos local estático o declarado globalmente o con la dirección de un objeto de datos declarado con el **dllimport** atributo, que genera un error en C. Además, puede inicializar un puntero a función local estático con la dirección de una función declarada con el **dllimport** atributo. En C, esta asignación establece el puntero en la dirección del código thunk de importación de DLL (un código auxiliar que transfiere el control a la función) en lugar de en la dirección de la función. En C++, establece el puntero en la dirección de la función. Por ejemplo:

    ```cpp
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

     Sin embargo, dado que un programa que incluya el **dllexport** atributo en la declaración de un objeto debe proporcionar la definición de ese objeto en algún lugar en el programa, puede inicializar un puntero a función estático global o local con la dirección de un **dllexport** función. De forma similar, puede inicializar un puntero de datos estático global o local con la dirección de un **dllexport** objeto de datos. Por ejemplo, el código siguiente no genera errores en C ni en C++:

    ```cpp
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

- Si aplica **dllexport** a una clase normal que tiene una clase base que no está marcada como **dllexport**, el compilador generará la advertencia C4275.

     El compilador genera la misma advertencia si la clase base es una especialización de una plantilla de clase. Para solucionar este problema, marque la clase base con **dllexport**. El problema con una especialización de una plantilla de clase es dónde colocar el **__declspec (dllexport)**; no tiene permiso para marcar la plantilla de clase. En su lugar, cree una instancia de la plantilla de clase y explícitamente Marque esta instancia explícita con **dllexport**. Por ejemplo:

    ```cpp
    template class __declspec(dllexport) B<int>;
    class __declspec(dllexport) D : public B<int> {
    // ...
    ```

     Esta solución no funciona si el argumento de la plantilla es la clase de la que se deriva. Por ejemplo:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

     Dado que este es un patrón común con plantillas, el compilador cambió la semántica de **dllexport** cuando se aplica a una clase que tiene uno o más clases base y cuando una o varias de las clases base son una especialización de una plantilla de clase . En este caso, el compilador aplica implícitamente **dllexport** a las especializaciones de plantillas de clase. Puede hacer lo siguiente y no recibe una advertencia:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[dllexport, dllimport](../cpp/dllexport-dllimport.md)