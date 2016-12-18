---
title: "Error del compilador C2666 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2666"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2666"
ms.assetid: 78364d15-c6eb-439a-9088-e04a0176692b
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2666
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : sobrecargas número tienen conversiones similares  
  
 Una función u operador sobrecargado es ambiguo.   Las listas de parámetros formales pueden ser demasiado parecidas para que el compilador resuelva la ambigüedad.  Para corregir este error, convierta explícitamente uno o más de los parámetros actuales.  
  
 El código siguiente genera el error C2666:  
  
```  
// C2666.cpp  
struct complex {  
   complex(double);  
};  
  
void h(int,complex);  
void h(double, double);  
  
int main() {  
   h(3,4);   // C2666  
}  
```  
  
 Este error también puede producirse como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003:  
  
-   operadores binarios y conversiones definidas por el usuario a tipos de puntero  
  
-   conversión de calificación no es lo mismo que conversión de identidad  
  
 Para los operadores binarios \<\>, \<\=, y \>\=, un último parámetro ahora se convierte implícitamente al tipo de operando si el tipo del parámetro define un operador de conversión definida por el usuario para convertir al tipo del operando.  Ahora existe la posibilidad de que se produzcan ambigüedades.  
  
 Para que el código sea válido en las versiones Visual Studio .NET 2003 y Visual Studio .NET de Visual C\+\+, llame explícitamente al operador de clase mediante sintaxis de función.  
  
## Ejemplo  
  
```  
// C2666b.cpp  
#include <string.h>  
#include <stdio.h>  
  
struct T   
{  
    T( const T& copy )   
    {  
        m_str = copy.m_str;  
    }  
  
    T( const char* str )   
    {  
        int iSize = (strlen( str )+ 1);  
        m_str = new char[ iSize ];  
        if (m_str)  
            strcpy_s( m_str, iSize, str );  
    }  
  
    bool operator<( const T& RHS )   
    {  
        return m_str < RHS.m_str;  
    }  
  
    operator char*() const   
    {  
        return m_str;  
    }  
  
    char* m_str;  
};  
  
int main()   
{  
    T str1( "ABCD" );  
    const char* str2 = "DEFG";  
  
    // Error – Ambiguous call to operator<()  
    // Trying to convert str1 to char* and then call   
    // operator<( const char*, const char* )?  
    //  OR  
    // trying to convert str2 to T and then call  
    // T::operator<( const T& )?  
  
    if( str1 < str2 )   // C2666  
  
    if ( str1.operator < ( str2 ) )   // Treat str2 as type T  
        printf_s("str1.operator < ( str2 )\n");  
  
    if ( str1.operator char*() < str2 )   // Treat str1 as type char*  
        printf_s("str1.operator char*() < str2\n");  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente genera C2666:  
  
```  
// C2666c.cpp  
// compile with: /c  
  
enum E   
{  
    E_A,   E_B  
};  
  
class A   
{  
    int h(const E e) const {return 0; }  
    int h(const int i) { return 1; }  
    // Uncomment the following line to resolve.  
    // int h(const E e) { return 0; }  
  
    void Test()   
    {  
        h(E_A);   // C2666  
        h((const int) E_A);  
        h((int) E_A);  
    }  
};  
```