---
title: "Nombres sin vinculaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "enumeradores [C++], vinculación"
  - "parámetros de función [C++]"
  - "funciones [C++], parámetros"
  - "nombres [C++], sin vinculación"
  - "typedef (nombres), vinculación"
ms.assetid: 7174c500-12d2-4572-8c16-63c27c758fb1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Nombres sin vinculaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los únicos nombres que no tienen vinculación son:  
  
-   Parámetros de función.  
  
-   Nombres de ámbito de bloque no declarados como `extern` o **static**.  
  
-   Enumeradores.  
  
-   Nombres declarados en una instrucción `typedef`.  Una excepción es cuando la instrucción `typedef` se utiliza para proporcionar un nombre para un tipo de clase sin nombre.  El nombre puede tener vinculación externa si la clase tiene vinculación externa.  En el ejemplo siguiente se muestra una situación en la que un nombre `typedef` tiene vinculación externa:  
  
    ```  
    // names_with_no_linkage.cpp  
    typedef struct  
    {  
       short x;  
       short y;  
    } POINT;  
  
    extern int MoveTo( POINT pt );  
  
    int main()  
    {  
    }  
    ```  
  
     El nombre `typedef`, `POINT`, se convierte en el nombre de la estructura sin nombre.  A continuación, se utiliza para declarar una función con vinculación externa.  
  
 Como los nombres `typedef` no tienen ninguna vinculación, sus definiciones pueden diferir entre unidades de traducción.  Dado que las compilaciones tienen lugar de forma discreta, no hay forma de que el compilador detecte estas diferencias.  Como resultado, los errores de esta clase no se detectan hasta el momento de la vinculación.  Considere el caso siguiente:  
  
```  
// Translation unit 1  
typedef int INT  
  
INT myInt;  
...  
  
// Translation unit 2  
typedef short INT  
  
extern INT myInt;  
...  
```  
  
 El código anterior genera un error “externo sin resolver" en tiempo de vinculación.  
  
## Ejemplo  
 Las funciones de C\+\+ solo se pueden definir en el ámbito de archivo o clase.  En el ejemplo siguiente se muestra cómo definir funciones y una definición de función errónea:  
  
```  
// function_definitions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
void ShowChar( char ch );    // Declare function ShowChar.  
  
void ShowChar( char ch )     // Define function ShowChar.  
{                            // Function has file scope.  
   cout << ch;  
}  
  
struct Char                  // Define class Char.  
{  
    char Show();             // Declare Show function.  
    char Get();              // Declare Get function.  
    char ch;  
};  
  
char Char::Show()            // Define Show function  
{                            //  with class scope.  
    cout << ch;  
    return ch;  
}  
  
void GoodFuncDef( char ch )  // Define GoodFuncDef  
{                            //  with file scope.  
    int BadFuncDef( int i )  // C2601, Erroneous attempt to  
    {                        //  nest functions.  
        return i * 7;  
    }  
    for( int i = 0; i < BadFuncDef( 2 ); ++i )  
        cout << ch;  
    cout << "\n";  
}  
```  
  
## Vea también  
 [Programa y vinculación](../cpp/program-and-linkage-cpp.md)