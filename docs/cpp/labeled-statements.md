---
title: "Instrucciones con etiquetas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "goto"
  - "case"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "instrucción con etiqueta"
  - "instrucciones, con etiqueta"
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Instrucciones con etiquetas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las etiquetas se usan para transferir el control de programas directamente a la instrucción especificada.  
  
```  
identifier :  statement  
case constant-expression :  statement  
default :  statement  
```  
  
 El ámbito de una etiqueta es toda la función donde se declara.  
  
## Comentarios  
 Hay tres tipos de instrucciones con etiquetas.  En todas ellas se utiliza el carácter de dos puntos para distinguir el tipo de etiqueta de la instrucción.  La etiqueta case y las etiquetas predeterminadas son específicas para las instrucciones case.  
  
```cpp  
#include <iostream>   
using namespace std;   
  
void test_label(int x) {  
  
    if (x == 1){  
        goto label1;  
    }  
    goto label2;  
  
label1:  
    cout << "in label1" << endl;  
    return;  
  
label2:  
    cout << "in label2" << endl;  
    return;  
}  
  
int main() {  
    test_label(1);  // in label1   
    test_label(2);  // in label2  
}  
  
```  
  
 **La instrucción goto**  
  
 La aparición de una etiqueta *identifier* en el programa de origen declara una etiqueta.  Solo una instrucción [goto](../cpp/goto-statement-cpp.md) puede transferir el control a una etiqueta *identifier*.  En el siguiente fragmento de código se muestra el uso de la instrucción `goto` y una etiqueta *identifier*:  
  
 Una etiqueta no puede aparecer por sí misma; debe estar asociada siempre a una instrucción.  Si se necesita la propia etiqueta, coloque una instrucción null detrás de la etiqueta.  
  
 La etiqueta tiene ámbito de función y no se puede volver a declarar dentro de la función.  Sin embargo, se puede utilizar el mismo nombre como una etiqueta en diferentes funciones.  
  
```  
// labels_with_goto.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   using namespace std;  
   goto Test2;  
  
   cout << "testing" << endl;  
  
   Test2:  
      cerr << "At Test2 label." << endl;  
}  
  
//Output: At Test2 label.  
```  
  
 **La instrucción case**  
  
 Las etiquetas que aparecen después de la palabra clave **case** no pueden aparecer también fuera de una instrucción `switch`.  \(Esta restricción también se aplica a la palabra clave **default**\). En el fragmento de código siguiente se muestra el uso correcto de las etiquetas **case**:  
  
```  
// Sample Microsoft Windows message processing loop.  
switch( msg )  
{  
   case WM_TIMER:    // Process timer event.  
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );  
      ShowWindow( hWnd, SW_SHOWNA );  
      nIcon %= 14;  
      Yield();  
      break;  
  
   case WM_PAINT:  
      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );  
      hDC = BeginPaint( hWnd, &ps );   
      EndPaint( hWnd, &ps );  
      break;  
  
   default:  
      // This choice is taken for all messages not specifically  
      //  covered by a case statement.  
  
      return DefWindowProc( hWnd, Message, wParam, lParam );  
      break;  
}  
```  
  
## Etiquetas en la instrucción case  
 Las etiquetas que aparecen después de la palabra clave **case** no pueden aparecer también fuera de una instrucción `switch`.  \(Esta restricción también se aplica a la palabra clave **default**\). En el fragmento de código siguiente se muestra el uso correcto de las etiquetas **case**:  
  
```  
// Sample Microsoft Windows message processing loop.  
switch( msg )  
{  
   case WM_TIMER:    // Process timer event.  
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );  
      ShowWindow( hWnd, SW_SHOWNA );  
      nIcon %= 14;  
      Yield();  
      break;  
  
   case WM_PAINT:  
      // Obtain a handle to the device context.  
      // BeginPaint will send WM_ERASEBKGND if appropriate.  
  
      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );  
      hDC = BeginPaint( hWnd, &ps );  
  
      // Inform Windows that painting is complete.  
  
      EndPaint( hWnd, &ps );  
      break;  
  
   case WM_CLOSE:  
      // Close this window and all child windows.  
  
      KillTimer( hWnd, TIMER1 );  
      DestroyWindow( hWnd );  
      if ( hWnd == hWndMain )  
         PostQuitMessage( 0 );  // Quit the application.  
      break;  
  
   default:  
      // This choice is taken for all messages not specifically  
      //  covered by a case statement.  
  
      return DefWindowProc( hWnd, Message, wParam, lParam );  
      break;  
}  
```  
  
## Etiquetas en la instrucción goto  
 La aparición de una etiqueta *identifier* en el programa de origen declara una etiqueta.  Solo una instrucción [goto](../cpp/goto-statement-cpp.md) puede transferir el control a una etiqueta *identifier*.  En el siguiente fragmento de código se muestra el uso de la instrucción `goto` y una etiqueta *identifier*:  
  
 Una etiqueta no puede aparecer por sí misma; debe estar asociada siempre a una instrucción.  Si se necesita la propia etiqueta, coloque una instrucción null detrás de la etiqueta.  
  
 La etiqueta tiene ámbito de función y no se puede volver a declarar dentro de la función.  Sin embargo, se puede utilizar el mismo nombre como una etiqueta en diferentes funciones.  
  
```  
// labels_with_goto.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   using namespace std;  
   goto Test2;  
  
   cout << "testing" << endl;  
  
   Test2:  
      cerr << "At Test2 label." << endl;  
// At Test2 label.  
}  
  
```  
  
## Vea también  
 [Información general sobre las instrucciones de C\+\+](../cpp/overview-of-cpp-statements.md)   
 [switch \(Instrucción\) \(C\+\+\)](../cpp/switch-statement-cpp.md)