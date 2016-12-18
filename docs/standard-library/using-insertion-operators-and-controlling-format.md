---
title: "Usar operadores de inserci&#243;n y controlar el formato | Microsoft Docs"
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
  - "operadores de inserción"
ms.assetid: cdefe986-6548-4cd1-8a67-b431d7d36a1c
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Usar operadores de inserci&#243;n y controlar el formato
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se muestra cómo controlar el formato y cómo crear operadores de inserción para las clases propias.  El operador de inserción \(**\<\<**\), que está preprogramado para todos los tipos de datos estándar de C\+\+, envía bytes a un objeto de flujo de salida.  Los operadores de inserción trabajan con "manipuladores" predefinidos, que son elementos que cambian el formato predeterminado de argumentos de entero.  
  
 Puede controlar el formato con las opciones siguientes:  
  
-   [Ancho de salida](#vclrfoutputwidthanchor3)  
  
-   [Alineación](#vclrfalignmentanchor4)  
  
-   [Precisión](#vclrfprecisionanchor5)  
  
-   [RADIX](#vclrfradixanchor6)  
  
##  <a name="vclrfoutputwidthanchor3"></a> Ancho de salida  
 Para alinear la salida, especifique el ancho de salida para cada elemento colocando el manipulador `setw` del flujo o llamando a la función miembro **witdh**.  En este ejemplo se alinean a la derecha los valores de una columna de, como mínimo, 10 caracteres de ancho.  
  
```  
// output_width.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };  
   for( int i = 0; i < 4; i++ )  
   {  
      cout.width(10);  
      cout << values[i] << '\n';  
   }  
}  
```  
  
### Salida  
  
```  
   1.23  
  35.36  
  653.7  
4358.24  
```  
  
 Los espacios en blanco iniciales se agregan a cualquier valor con menos de 10 caracteres de ancho.  
  
 Para rellenar un campo, use la función miembro **fill**, que establece el valor del carácter de relleno para los campos que tienen un ancho especificado.  El valor predeterminado es un espacio en blanco.  Para rellenar la columna de números con asteriscos, modifique el bucle anterior de **for** como sigue:  
  
```  
for( int i = 0; i < 4; i++ )  
{  
   cout.width( 10 );  
   cout.fill( '*' );  
   cout << values[i] << endl;  
}  
```  
  
 El manipulador `endl` reemplaza el carácter de nueva línea \(`'\n'`\).  La salida es similar a la siguiente:  
  
```  
******1.23  
*****35.36  
*****653.7  
***4358.24  
```  
  
 Para especificar los anchos de los elementos de datos en la misma línea, use el manipulador `setw`:  
  
```  
// setw.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iomanip>  
using namespace std;  
  
int main( )  
{  
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };  
   char *names[] = { "Zoot", "Jimmy", "Al", "Stan" };  
   for( int i = 0; i < 4; i++ )  
      cout << setw( 6 )  << names[i]  
           << setw( 10 ) << values[i] << endl;  
}  
```  
  
### Salida  
 La función del miembro **witdh** se declara en \<iostream\>.  Si usa `setw` o cualquier otro manipulador con argumentos, se debe incluir \<iomanip\>.  En la salida, las cadenas se imprimen en un campo de ancho 6 y números enteros en un campo de ancho 10:  
  
```  
 Zoot      1.23  
Jimmy     35.36  
   Al     653.7  
 Stan   4358.24  
```  
  
 Ni `setw` ni **width** truncan valores.  Si la salida con formato supera el ancho, se imprime el valor completo, sujeto a la configuración de precisión del flujo.  Tanto `setw` como **width** afectan únicamente al campo siguiente.  El ancho de campo revierte a su comportamiento predeterminado \(el ancho necesario\) después de que se haya impreso un campo,  pero las opciones de formato de flujo seguirán vigentes hasta que se modifiquen.  
  
##  <a name="vclrfalignmentanchor4"></a> Alineación  
 Los flujos de salida tienen de forma predeterminada el texto alineado a la derecha.  Para alinear a la izquierda los nombres del ejemplo anterior y alinear a la derecha los números, reemplace el bucle de **for** como sigue:  
  
```  
for ( int i = 0; i < 4; i++ )  
   cout << setiosflags( ios::left )  
        << setw( 6 )  << names[i]  
        << resetiosflags( ios::left )  
        << setw( 10 ) << values[i] << endl;  
```  
  
 La salida es similar a la siguiente:  
  
```  
Zoot        1.23  
Jimmy      35.36  
Al         653.7  
Stan     4358.24  
```  
  
 La marca de alinear a la izquierda se establece usando el manipulador [setiosflags](../Topic/setiosflags.md) con el enumerador [left](../Topic/left.md).  Este enumerador se define en la clase [ios](../Topic/ios.md), de manera que su referencia se debe incluir en el prefijo **ios::**.  El manipulador [resetiosflags](../Topic/resetiosflags.md) desactiva la marca de alinear a la izquierda.  A diferencia de **witdht** y `setw`, el efecto de `setiosflags` y `resetiosflags` es permanente.  
  
##  <a name="vclrfprecisionanchor5"></a> Precisión  
 El valor predeterminado de precisión de punto flotante es seis.  Por ejemplo, el número 3466.9768 se imprime como 3466.98.  Para cambiar el modo de impresión de este valor, use el manipulador [setprecision](../Topic/setprecision.md).  El manipulador tiene dos marcas: [fixed](../Topic/fixed.md) y [scientific](../Topic/scientific.md).  Si se establece [fixed](../Topic/fixed.md), el número se imprime como 3466.976800.  Si se establece **scientific**, se imprime como 3.4669773 \+ 003.  
  
 Para visualizar los números de punto flotante que se muestran en [Alineación](#vclrfalignmentanchor4) con un dígito significativo, reemplace el bucle de **for** como sigue:  
  
```  
for ( int i = 0; i < 4; i++ )  
   cout << setiosflags( ios::left )  
        << setw( 6 )    
        << names[i]  
        << resetiosflags( ios::left )  
        << setw( 10 )   
        << setprecision( 1 )  
        << values[i]   
        << endl;  
```  
  
 El programa imprime esta lista:  
  
```  
Zoot          1  
Jimmy     4e+001  
Al        7e+002  
Stan      4e+003  
```  
  
 Para eliminar la notación científica, inserte esta instrucción antes del bucle de **for**:  
  
```  
cout << setiosflags( ios::fixed );  
```  
  
 Con la notación fija, el programa imprime con un dígito después del punto decimal.  
  
```  
Zoot         1.2  
Jimmy       35.4  
Al         653.7  
Stan      4358.2  
```  
  
 Si cambia la marca **ios::fixed** por **ios::scientific**, el programa imprime lo siguiente:  
  
```  
Zoot    1.2e+000  
Jimmy   3.5e+001  
Al      6.5e+002  
Stan    4.4e+003  
```  
  
 De nuevo, el programa imprime un dígito después del punto decimal.  Si se establece **ios::fixed** o **ios::scientific**, el valor de precisión determina el número de dígitos después del punto decimal.  Si no se establece ninguna de estas marcas, el valor de precisión determina el número total de dígitos significativos.  El manipulador `resetiosflags` borra estas marcas.  
  
##  <a name="vclrfradixanchor6"></a> RADIX  
 Los manipuladores **dec**, **oct** y **hex** establecen el radix predeterminado para entrada y salida.  Por ejemplo, si inserta el manipulador **hex** en el flujo de salida, el objeto traduce correctamente la representación interna de datos de números enteros a un formato de salida hexadecimal.  Los números se muestran con dígitos de la letra a a la f en minúsculas si la marca [uppercase](../Topic/uppercase.md) es evidente \(valor predeterminado\); en caso contrario, se muestran en mayúsculas.  El radix predeterminado es **dec** \(decimal\).  
  
## Cadena entrecomillada \(C\+\+14\)  
 Cuando se inserta una cadena en un flujo, puede recuperar con facilidad la misma cadena llamando a la función miembro stringstream::str\(\).  Pero si quiere usar el operador de extracción para insertar el flujo en una nueva cadena en un momento posterior, es posible que obtenga un resultado inesperado porque el operador \>\> se detendrá de forma predeterminada cuando encuentre el primer carácter de espacio en blanco.  
  
```  
  
std::stringstream ss;  
std::string inserted = "This is a sentence.";  
std::string extracted;  
  
ss << inserted;  
ss >> extracted;  
  
std::cout << inserted;     //  This is a sentence.  
std::cout << extracted;   //   This  
```  
  
 Este comportamiento se puede solucionar manualmente, pero hacer que el recorrido de ida y vuelta de la cadena sea más fácil, C \+\+ 14 agrega el manipulador de flujo `std::quoted` en `<iomanip>`.  Tras la inserción, `quoted()` rodea la cadena con un delimitador \(comilla doble ' " ' de forma predeterminada\) y tras la extracción manipula el flujo para extraer todos los caracteres hasta que se encuentra el delimitador final.  Las comillas incrustadas se escapan con un carácter de escape \('\\\\ ' de forma predeterminada\).  
  
 Los delimitadores están presentes solo en el objeto de flujo; no están presentes en la cadena extraída, pero están presentes en la cadena devuelta por [basic\_stringstream::str](../Topic/basic_stringstream::str.md)\(\).  
  
 El comportamiento del espacio en blanco de las operaciones de inserción y extracción es independiente de cómo se representa una cadena en el código, de forma que el operador entrecomillado será útil al margen de si la cadena de entrada es un literal de cadena sin formato o una cadena normal.  La cadena de entrada, con independencia de su formato, puede tener comillas, saltos de línea, tabulaciones , etc., insertados y todos ellos se conservarán con el manipulador quoted\(\).  
  
 Para obtener más información y ejemplos de código completos, vea [entrecomillado](../Topic/quoted.md).  
  
## Vea también  
 [Flujos de salida](../standard-library/output-streams.md)   
 [entrecomillado](../Topic/quoted.md)