---
title: Reglas generales y limitaciones
ms.date: 11/04/2016
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
ms.openlocfilehash: 1adbaf9d9be3a0fc0724603e01b81700554839bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188611"
---
# <a name="general-rules-and-limitations"></a>Reglas generales y limitaciones

**Específicos de Microsoft**

- Si se declara una función o un objeto sin el atributo **DllImport** o **dllexport** , la función o el objeto no se considera parte de la interfaz dll. Por consiguiente, la definición de la función o el objeto debe estar presente en ese módulo o en otro módulo del mismo programa. Para hacer que la función o el objeto formen parte de la interfaz DLL, debe declarar la definición de la función o el objeto en el otro módulo como **dllexport**. De los contrario, se genera un error del vinculador.

   Si declara una función o un objeto con el atributo **dllexport** , su definición debe aparecer en algún módulo del mismo programa. De los contrario, se genera un error del vinculador.

- Si un solo módulo del programa contiene declaraciones **DllImport** y **dllexport** para la misma función u objeto, el atributo **dllexport** tiene prioridad sobre el atributo **DllImport** . Sin embargo, se genera una advertencia del compilador. Por ejemplo:

    ```cpp
    __declspec( dllimport ) int i;
    __declspec( dllexport ) int i;   // Warning; inconsistent;
                                     // dllexport takes precedence.
    ```

- En C++, puede inicializar un puntero de datos local declarado o estático globalmente o con la dirección de un objeto de datos declarado con el atributo **DllImport** , que genera un error en C. Además, puede inicializar un puntero de función local estático con la dirección de una función declarada con el atributo **DllImport** . En C, esta asignación establece el puntero en la dirección del código thunk de importación de DLL (un código auxiliar que transfiere el control a la función) en lugar de en la dirección de la función. En C++, establece el puntero en la dirección de la función. Por ejemplo:

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

   Sin embargo, dado que un programa que incluye el atributo **dllexport** en la declaración de un objeto debe proporcionar la definición de ese objeto en algún lugar del programa, puede inicializar un puntero a función estático global o local con la dirección de una función **dllexport** . Del mismo modo, puede inicializar un puntero de datos estático global o local con la dirección de un objeto de datos **dllexport** . Por ejemplo, el código siguiente no genera errores en C ni en C++:

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

- Si aplica **dllexport** a una clase normal que tiene una clase base que no está marcada como **dllexport**, el compilador generará C4275.

   El compilador genera la misma advertencia si la clase base es una especialización de una plantilla de clase. Para solucionar este fin, marque la clase base con **dllexport**. El problema con una especialización de una plantilla de clase es dónde colocar el **__declspec (dllexport)** ; no tiene permiso para marcar la plantilla de clase. En su lugar, cree explícitamente una instancia de la plantilla de clase y marque esta instancia explícita con **dllexport**. Por ejemplo:

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

   Dado que se trata de un patrón común con plantillas, el compilador cambió la semántica de **dllexport** cuando se aplica a una clase que tiene una o más clases base y cuando una o más de las clases base es una especialización de una plantilla de clase. En este caso, el compilador aplica implícitamente **dllexport** a las especializaciones de plantillas de clase. Puede hacer lo siguiente y no recibir una advertencia:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
