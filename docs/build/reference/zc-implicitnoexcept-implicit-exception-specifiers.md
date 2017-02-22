---
title: "/Zc:implicitNoexcept (especificadores de excepci&#243;n impl&#237;cita) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/Zc:implicitNoexcept"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc:implicitNoexcept"
  - "Zc:implicitNoexcept"
  - "-Zc:implicitNoexcept"
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# /Zc:implicitNoexcept (especificadores de excepci&#243;n impl&#237;cita)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Al especificar la opción **\/Zc:implicitNoexcept**, el compilador agrega un especificador de excepción [noexcept](../../cpp/noexcept-cpp.md) implícita a las funciones miembro especiales definidas por el compilador y a los destructores y desasignadores definidos por el usuario.  De forma predeterminada, **\/Zc:implicitNoexcept** está habilitado para cumplir la norma ISO de C\+\+11.  Al desactivar esta opción, se deshabilita el `noexcept` implícito en los destructores y desasignadores definidos por el usuario, así como las funciones miembro especiales definidas por el compilador.  
  
## Sintaxis  
  
```vb  
/Zc:implicitNoexcept[-]  
```  
  
#### Parámetros  
  
## Comentarios  
 De forma predeterminada, y si se especifica **\/Zc:implicitNoexcept**, el compilador sigue la sección 15.4 de la norma ISO de C\+\+11 y agrega de forma implícita un especificador de excepción `noexcept` a cada función miembro especial declarada implícitamente o establecida como explícita \(constructor predeterminado, constructor de copias, constructor de movimiento, destructor, copiar operador de asignación o mover operador de asignación\), así como cada función de desasignador o destructor definida por el usuario.  Un desasignador definido por el usuario tiene un especificador de excepción `noexcept(true)` implícito.  Para los destructores definidos por el usuario, el especificador de excepción implícito es `noexcept(true)` a menos que una clase de miembro independiente o una clase base tengan un destructor que no sea `noexcept(true)`.  Para las funciones miembro especiales generadas por el compilador, si cualquier función invocada directamente por esta función es `noexcept(false)`, el especificador de excepción implícito será `noexcept(false)`.  De lo contrario, el especificador de excepción implícito es `noexcept(true)`.  
  
 El compilador no genera ningún especificador de excepción implícito para las funciones declaradas mediante los especificadores explícitos `noexcept` o `throw`, o un atributo `__declspec(nothrow)`.  
  
 Si se deshabilita la opción especificando **\/Zc:implicitNoexcept\-**, el compilador no generará ningún especificador de excepción implícito.  Este comportamiento es el mismo que en Visual Studio 2013, donde los destructores y desasignadores que no disponían de especificadores de excepción podían tener instrucciones `throw`.  De forma predeterminada, al especificar **\/Zc:implicitNoexcept**, si se encuentra una instrucción `throw` en tiempo de ejecución en una función con un especificador `noexcept(true)` implícito, esta provoca una invocación inmediata de `std::terminate`. Asimismo, no se garantiza el comportamiento normal de desenredado de los controladores de excepciones.  Para facilitar la identificación de esta situación, el compilador genera la [Advertencia del compilador \(nivel 1\) C4297](../Topic/Compiler%20Warning%20\(level%201\)%20C4297.md).  Si la acción `throw` es intencionada, se recomienda cambiar la declaración de función para que tenga un especificador `noexcept(false)` explícito en lugar de usar **\/Zc:implicitNoexcept\-**.  
  
 En este ejemplo se muestra cómo se comporta un destructor definido por el usuario que no tiene ningún especificador de excepción explícito cuando la opción **\/Zc:implicitNoexcept** está establecida o desactivada.  Para mostrar el comportamiento cuando está establecido, efectúe la compilación con `cl /EHsc /W4 implicitNoexcept.cpp`.  Para mostrar el comportamiento cuando está deshabilitado, efectúe la compilación con `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp`.  
  
```  
// implicitNoexcept.cpp  
// Compile by using: cl /EHsc /W4 implicitNoexcept.cpp  
// Compile by using: cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp  
  
#include <iostream>  
#include <cstdlib>      // for std::exit, EXIT_FAILURE, EXIT_SUCCESS  
#include <exception>    // for std::set_terminate  
  
void my_terminate()  
{  
    std::cout << "Unexpected throw caused std::terminate" << std::endl;  
    std::cout << "Exit returning EXIT_FAILURE" << std::endl;  
    std::exit(EXIT_FAILURE);  
}  
  
struct A {  
    // Explicit noexcept overrides implicit exception specification  
    ~A() noexcept(false) {  
        throw 1;  
    }  
};  
  
struct B : public A {  
    // Compiler-generated ~B() definition inherits noexcept(false)  
    ~B() = default;  
};  
  
struct C {  
    // By default, the compiler generates an implicit noexcept(true)  
    // specifier for this user-defined destructor. To enable it to  
    // throw an exception, use an explicit noexcept(false) specifier,  
    // or compile by using /Zc:implicitNoexcept-  
    ~C() {    
        throw 1; // C4297, calls std::terminate() at run time  
    }  
};  
  
struct D : public C {  
    // This destructor gets the implicit specifier of its base.  
    ~D() = default;  
};  
  
int main()  
{  
    std::set_terminate(my_terminate);  
  
    try  
    {  
        {  
            B b;   
        }  
    }  
    catch (...)  
    {  
        // exception should reach here in all cases  
        std::cout << "~B Exception caught" << std::endl;  
    }  
    try  
    {  
        {  
            D d;  
        }  
    }  
    catch (...)  
    {  
        // exception should not reach here if /Zc:implicitNoexcept  
        std::cout << "~D Exception caught" << std::endl;  
    }  
    std::cout << "Exit returning EXIT_SUCCESS" << std::endl;  
    return EXIT_SUCCESS;  
}  
  
```  
  
 Cuando se compila con la opción predeterminada **\/Zc:implicitNoexcept**, el ejemplo genera este resultado:  
  
  **~B Exception caught**  
**Unexpected throw caused std::terminate**  
**Exit returning EXIT\_FAILURE** Cuando se compila con la opción **\/Zc:implicitNoexcept\-**, el ejemplo genera este resultado:  
  
  **~B Exception caught**  
**~D Exception caught**  
**Exit returning EXIT\_SUCCESS** Para más información sobre los problemas de conformidad en Visual C\+\+, vea [Comportamiento no estándar](../../cpp/nonstandard-behavior.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Modifique la propiedad **Opciones adicionales** para que incluya **\/Zc:implicitNoexcept** o **\/Zc:implicitNoexcept\-** y, luego, elija **Aceptar**.  
  
## Vea también  
 [\/Zc \(Ajuste\)](../../build/reference/zc-conformance.md)   
 [noexcept](../../cpp/noexcept-cpp.md)   
 [Especificaciones de excepciones \(throw\)](../../cpp/exception-specifications-throw-cpp.md)   
 [terminate](../Topic/terminate%20\(%3Cexception%3E\).md)