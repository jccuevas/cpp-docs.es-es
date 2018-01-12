---
title: "Cambie la instrucción) (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
dev_langs: C++
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e668756e8cabafbdef522d6754487efe452f96de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="switch-statement-c"></a>switch (Instrucción) (C++)
Permite la selección entre varias secciones de código, dependiendo del valor de una expresión entera.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
   switch ( init; expression )  
   case constant-expression : statement  
   [default  : statement]  
```  
  
## <a name="remarks"></a>Comentarios  
 El *expresión* debe ser de un tipo entero o de un tipo de clase para el que hay una conversión no ambigua a un tipo entero. La promoción de entero se realiza como se describe en [conversiones estándar](standard-conversions.md).  
  
 El `switch` cuerpo de instrucción está formada por una serie de **caso** etiquetas y una función opcional **predeterminado** etiqueta. No hay dos expresiones constantes en **caso** instrucciones pueden evaluar en el mismo valor. El **predeterminado** etiqueta puede aparecer solo una vez. Las instrucciones con etiquetas no son requisitos sintácticos, pero la instrucción `switch` no tiene sentido sin ellas.   La instrucción predeterminada no necesita estar al final; puede aparecer en cualquier parte del cuerpo de la instrucción switch. Una etiqueta case o default solo puede aparecer en una instrucción switch.  
  
 El *expresión constante* en cada uno de ellos **caso** etiqueta se convierte al tipo de *expresión* y se compara con *expresión* para igualdad. El control transfiere a la instrucción cuya **caso** *expresión constante* coincide con el valor de *expresión*. El comportamiento resultante se muestra en la siguiente tabla.  
  
### <a name="switch-statement-behavior"></a>Comportamiento de la instrucción switch  
  
|Condición|Acción|  
|---------------|------------|  
|El valor convertido coincide con el de la expresión de control promovida.|El control se transfiere a la instrucción que sigue a esa etiqueta.|  
|Ninguna de las constantes coincide con las constantes en el **caso** etiquetas; un **predeterminado** etiqueta está presente.|El control se transfiere a la **predeterminado** etiqueta.|  
|Ninguna de las constantes coincide con las constantes en el **caso** las etiquetas; **predeterminado** etiqueta no está presente.|El control se transfiere a la instrucción situada detrás de la instrucción `switch`.|  
  
 Si se encuentra una expresión coincidente, control no se interrumpa por posteriores **caso** o **predeterminado** etiquetas. El [salto](../cpp/break-statement-cpp.md) instrucción se utiliza para detener la ejecución y transferir el control a la instrucción después de la `switch` instrucción. Sin un **salto** instrucción, todas las instrucciones desde el conjunto de **caso** etiqueta al final de la `switch`, incluido el **predeterminado**, se ejecuta. Por ejemplo:  
  
```  
// switch_statement1.cpp  
#include <stdio.h>  
  
int main() {  
   char *buffer = "Any character stream";  
   int capa, lettera, nota;  
   char c;  
   capa = lettera = nota = 0;  
  
   while ( c = *buffer++ )   // Walks buffer until NULL  
   {  
      switch ( c )  
      {  
         case 'A':  
            capa++;  
            break;  
         case 'a':  
            lettera++;  
            break;  
         default:  
            nota++;  
      }  
   }  
   printf_s( "\nUppercase a: %d\nLowercase a: %d\nTotal: %d\n",  
      capa, lettera, (capa + lettera + nota) );  
}  
```  
  
 En el ejemplo anterior, se incrementa `capa` si `c` es una `A` mayúscula. La instrucción `break` detrás de `capa++` finaliza la ejecución del cuerpo de la instrucción `switch` y el control pasa al bucle `while`. Sin el `break` instrucción, ejecución sería "pasar explícitamente" a la siguiente instrucción con etiqueta, por lo que `lettera` y `nota` también se incrementarían. La instrucción `break` para `case 'a'` tiene un propósito similar. Si `c` es una `a` minúscula, `lettera` se incrementa y la instrucción `break` finaliza el cuerpo de la instrucción `switch`. Si `c` no es `a` ni `A`, se ejecuta la instrucción `default`.  

 **Visual Studio 2017 y versiones posterior:** (disponible con [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)) la `[[fallthrough]]` atributo se especifica en el estándar C ++ 17. Se puede utilizar en una `switch` instrucción como una sugerencia para el compilador (o a cualquiera que lea el código) se utiliza ese comportamiento paso explícito. Actualmente el compilador de Visual C++ no avisar al comportamiento de fallthrough, por lo que este atributo no tiene ningún comportamiento del compilador efecto. Tenga en cuenta que el atributo se aplica a una instrucción vacía en la instrucción con etiqueta; en otras palabras, el punto y coma es necesario.

```cpp
int main()
{
    int n = 5;
    switch (n)
    {

    case 1:
        a();
        break;
    case 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    case 3:
        c();
        break;
    default:
        d();
        break;
    }

    return 0;
}
```

 **Visual Studio 2017 15,3 y versiones posteriores** (disponible con [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): una instrucción switch puede introducir e inicializar una variable cuyo ámbito está limitado a un bloque de la instrucción switch:

```cpp
 switch (Gadget gadget(args); auto s = gadget.get_status())
        {
        case status::good:
            gadget.zip();
            break;
        case status::bad:
            throw BadGadget();
        };
```

 Un bloque interno de una instrucción `switch` puede contener definiciones con inicializaciones siempre que se pueda tener acceso a ellas, es decir, siempre que las rutas de ejecución posibles no las omitan. Los nombres proporcionados mediante estas declaraciones tienen ámbito local. Por ejemplo:  
  
```cpp  
// switch_statement2.cpp  
// C2360 expected  
#include <iostream>  
using namespace std;  
int main(int argc, char *argv[])  
{  
   switch( tolower( *argv[1] ) )  
   {  
       // Error. Unreachable declaration.  
       char szChEntered[] = "Character entered was: ";  
  
   case 'a' :  
       {  
       // Declaration of szChEntered OK. Local scope.  
       char szChEntered[] = "Character entered was: ";  
       cout << szChEntered << "a\n";  
       }  
       break;  
  
   case 'b' :  
       // Value of szChEntered undefined.  
       cout << szChEntered << "b\n";  
       break;  
  
   default:  
       // Value of szChEntered undefined.  
       cout << szChEntered << "neither a nor b\n";  
       break;  
   }  
}  
```  
  
 Una instrucción `switch` puede estar anidada. En tales casos, **caso** o **predeterminado** etiquetas asociar el más cercano `switch` instrucción que contenga.  

 
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Microsoft C no limita el número de valores case en una instrucción `switch`. El número solo está limitado por la memoria disponible. ANSI C requiere que al menos 257 etiquetas case se permitan en una instrucción `switch`.  
  
 El valor predeterminado para Microsoft C es que las extensiones de Microsoft estén habilitadas. Use la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador para deshabilitar estas extensiones.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones de selección](../cpp/selection-statements-cpp.md)   
 [Palabras clave](../cpp/keywords-cpp.md)   
 