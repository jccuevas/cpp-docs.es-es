---
title: "Extensiones de Microsoft para C y C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "! (operador), extensión de C++"
  - "!= (operador)"
  - "& (operador), extensiones para C/C++"
  - "&amp;&amp; (operador)"
  - "&= (operador)"
  - "^ (operador), extensiones para C/C++"
  - "^= (operador), extensiones para C++"
  - "| (operador), extensiones"
  - "|| (operador)"
  - "|= (operador)"
  - "~ (operador), extensiones para C/C++"
  - "And (operador), extensiones para C/C++"
  - "and_eq (operador)"
  - "compl (método)"
  - "extensiones"
  - "extensiones, lenguaje C"
  - "iso646.h (encabezado)"
  - "extensiones para C/C++ de Microsoft"
  - "NOT (operador)"
  - "not_eq (operador)"
  - "Or (operador), extensiones para C/C++ de Microsoft"
  - "or_eq (operador)"
  - "Visual C, extensiones para Microsoft"
  - "Visual C++, extensiones para C/C++"
  - "Xor (operador), extensiones para C/C++ de Microsoft"
  - "xor_eq (operador)"
ms.assetid: e811a74a-45ba-4c00-b206-2f2321b8689a
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Extensiones de Microsoft para C y C++
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ extiende los estándares ANSI C y ANSI C\+\+ de la forma siguiente.  
  
## Palabras clave  
 Se han agregado varias palabras clave.  En la lista de [Palabras clave de C\+\+](../../cpp/keywords-cpp.md), las palabras clave que tienen dos subrayados iniciales son extensiones de Visual C\+\+.  
  
## Definición fuera de la clase de miembros de tipo entero \(o enum\) estáticos y constantes  
 Bajo el estándar \(**\/Za**\), debe crear una definición fuera de la clase para los miembros de datos, como se muestra aquí:  
  
```  
class CMyClass  {  
   static const int max = 5;  
   int m_array[max];  
}  
...  
const int CMyClass::max;   // out of class definition  
```  
  
 En **\/Ze**, la definición fuera de la clase es opcional para los miembros de datos estáticos, de tipo entero constantes y de enumeración de constantes.  Solamente los miembros enteros y de enumeración de tipo static y const pueden tener inicializadores en una clase; la expresión de inicialización debe ser una expresión de constante.  
  
 Para evitar errores cuando se proporciona una definición fuera de la clase en un archivo de encabezado y este se incluye en varios archivos de código fuente, utilice [selectany](../../cpp/selectany.md).  Por ejemplo:  
  
```  
__declspec(selectany) const int CMyClass::max = 5;  
```  
  
## Conversiones  
 El compilador de C y el de C\+\+ admiten estos tipos de conversiones no ANSI:  
  
-   Conversiones no ANSI para generar valores L.  Por ejemplo:  
  
    ```  
    char *p;  
    (( int * ) p )++;  
    ```  
  
    > [!NOTE]
    >  Esta extensión solo está disponible en el lenguaje C.  Puede utilizar el siguiente formato estándar ANSI C en el código de C\+\+ para modificar un puntero como si fuera un puntero a un tipo diferente.  
  
     El ejemplo anterior podría modificarse de la forma siguiente para adaptarlo al estándar ANSI C.  
  
    ```  
    p = ( char * )(( int * )p + 1 );  
    ```  
  
-   Conversiones no ANSI de un puntero de función en un puntero de datos.  Por ejemplo:  
  
    ```  
    int ( * pfunc ) ();   
    int *pdata;  
    pdata = ( int * ) pfunc;  
    ```  
  
     Para realizar la misma conversión y mantener también la compatibilidad con ANSI, puede convertir el puntero de función en `uintptr_t` antes de convertirlo en un puntero de datos:  
  
    ```  
    pdata = ( int * ) (uintptr_t) pfunc;  
    ```  
  
## Listas de argumentos de longitud variable  
 El compilador de C\+\+ y el de C admiten un declarador de función que especifica un número de argumentos variable, seguido de una definición de función que proporciona un tipo en su lugar:  
  
```  
void myfunc( int x, ... );  
void myfunc( int x, char * c )  
{ }  
```  
  
## Comentarios en una sola línea  
 El compilador de C acepta comentarios en una sola línea, que se introducen mediante dos caracteres de barra diagonal \(\/\/\):  
  
```  
// This is a single-line comment.  
```  
  
## Ámbito  
 El compilador de C acepta las siguientes características relacionadas con el ámbito.  
  
-   Redefiniciones de elementos extern como static:  
  
    ```  
    extern int clip();  
    static int clip()  
    {}  
    ```  
  
-   Uso de redefiniciones de typedef sin efecto dentro del mismo ámbito:  
  
    ```  
    typedef int INT;  
    typedef int INT;  
    ```  
  
-   Los declaradores de función tienen ámbito de archivo:  
  
    ```  
    void func1()  
    {  
        extern int func2( double );  
    }  
    int main( void )  
    {  
        func2( 4 );    //  /Ze passes 4 as type double  
    }                  //  /Za passes 4 as type int  
    ```  
  
-   Uso de las variables de ámbito de bloque que se inicializan mediante expresiones no constantes:  
  
    ```  
    int clip( int );  
    int bar( int );  
    int main( void )  
    {  
        int array[2] = { clip( 2 ), bar( 4 ) };  
    }  
    int clip( int x )  
    {  
        return x;  
    }  
    int bar( int x )  
    {  
        return x;  
    }  
    ```  
  
## Declaraciones y definiciones de datos  
 El compilador de C admite las siguientes características de declaración y definición de datos.  
  
-   Constantes de caracteres y cadenas mezcladas en un inicializador:  
  
    ```  
    char arr[5] = {'a', 'b', "cde"};  
    ```  
  
-   Campos de bit que tienen tipos base distintos de **unsigned int** o **signed int**.  
  
-   Declaradores que no tienen un tipo:  
  
    ```  
    x;  
    int main( void )  
    {  
        x = 1;  
    }  
    ```  
  
-   Matrices sin tamaño como último campo de estructuras y uniones:  
  
    ```  
    struct zero  
    {  
        char *c;  
        int zarray[];  
    };  
    ```  
  
-   Estructuras sin nombre \(anónimas\):  
  
    ```  
    struct  
    {  
        int i;  
        char *s;  
    };  
    ```  
  
-   Uniones sin nombre \(anónimas\):  
  
    ```  
    union  
    {  
        int i;  
        float fl;  
    };  
    ```  
  
-   Miembros sin nombre:  
  
    ```  
    struct s  
    {  
       unsigned int flag : 1;  
       unsigned int : 31;  
    }  
    ```  
  
## Funciones intrínsecas de punto flotante  
 El compilador de C\+\+ y el de C admiten la generación alineada **x86 Specific \>** de las funciones `atan`, `atan2`, `cos`, `exp`, `log`, `log10`, `sin`, `sqrt` y `tan` **END x86 Specific** cuando se especifica **\/Oi**.  Para el compilador de C, la conformidad con ANSI se pierde cuando se utilizan estas funciones intrínsecas, puesto que no definen la variable `errno`.  
  
## Pasar un parámetro de puntero que no sea const a una función que espera una referencia a un parámetro de puntero const  
 Esto es una extensión de C\+\+.  Este código se compilará con **\/Ze**:  
  
```  
typedef   int   T;  
  
const T  acT = 9;      // A constant of type 'T'  
const T* pcT = &acT;   // A pointer to a constant of type 'T'  
  
void func2 ( const T*& rpcT )   // A reference to a pointer to a constant of type 'T'  
{  
   rpcT = pcT;  
}  
  
T*   pT;               // A pointer to a 'T'  
  
void func ()  
{  
   func2 ( pT );      // Should be an error, but isn't detected  
   *pT   = 7;         // Invalidly overwrites the constant 'acT'  
}  
```  
  
## ISO646.H no habilitado  
 En **\/Ze** debe incluir iso646.h si desea usar formas de texto de los operadores siguientes:  
  
-   && \(and\)  
  
-   &\= \(and\_eq\)  
  
-   & \(bitand\)  
  
-   &#124; \(bitor\)  
  
-   ~ \(compl\)  
  
-   \! \(not\)  
  
-   \!\= \(not\_eq\)  
  
-   &#124;&#124; \(or\)  
  
-   &#124;\= \(or\_eq\)  
  
-   ^ \(xor\)  
  
-   ^\= \(xor\_eq\)  
  
## La dirección de un literal de cadena tiene el tipo const char \[\], no const char \(\*\) \[\]  
 El siguiente ejemplo escribirá char const \(\*\)\[4\] con la opción **\/Za** y char const \[4\] con **\/Ze**.  
  
```  
#include <stdio.h>  
#include <typeinfo>  
  
int main()  
{  
    printf_s("%s\n", typeid(&"abc").name());  
}  
```  
  
## Vea también  
 [\/Za, \/Ze \(Deshabilitar extensiones de lenguaje\)](../../build/reference/za-ze-disable-language-extensions.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)