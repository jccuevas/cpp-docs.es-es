---
title: "Funciones de miembro de flujo de entrada | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "objetos de flujo de entrada"
  - "flujos de entrada, funciones miembro"
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Funciones de miembro de flujo de entrada
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las funciones miembro del flujo de entrada se utilizan para la entrada del disco.  La inclusión de las funciones miembro:  
  
-   [La función open para los flujos de entrada](#vclrftheopenfunctionforinputstreamsanchor11)  
  
-   [La función get](#vclrfthegetfunctionanchor12)  
  
-   [La función de getline](#vclrfthegetlinefunctionanchor13)  
  
-   [La función read](#vclrfthereadfunctionanchor14)  
  
-   [Las funciones de seekg y de tellg](#vclrftheseekgandtellgfunctionsanchor7)  
  
-   [La función close para los flujos de entrada](#vclrftheclosefunctionforinputstreamsanchor15)  
  
##  <a name="vclrftheopenfunctionforinputstreamsanchor11"></a> La función open para los flujos de entrada  
 Si utiliza una secuencia de archivo de entrada \(ifstream\), debe asociar esa secuencia con un archivo de disco específico.  Puede hacerlo en el constructor, o puede utilizar la función de **OPEN** .  En cualquier caso, los argumentos son iguales.  
  
 Especifica normalmente un indicador de [ios\_base::openmode](../Topic/ios_base::openmode.md) al abrir el archivo asociado a un flujo de entrada \(el modo predeterminado es **ios::in**\).  Para obtener una lista de los indicadores de **open\_mode** , vea [La función open](#vclrftheopenfunctionforinputstreamsanchor11).  Los marcadores se pueden combinar con el bit a bit OR \( &#124; \) operador.  
  
 Para leer un archivo, utilice primero la función miembro de **error** para determinar si existe:  
  
```  
istream ifile( "FILENAME" );  
if ( ifile.fail() )  
// The file does not exist ...  
```  
  
##  <a name="vclrfthegetfunctionanchor12"></a> La función get  
 La función sin formato del miembro de **obtener** funciona como el operador de **\>\>** con dos excepciones.  Primero, la función de **obtener** incluye caracteres de espacio en blanco, mientras que el extractor excluye el espacio en blanco cuando se establece la marca de [skipws](../Topic/skipws.md) \(valor predeterminado\).  En segundo lugar, la función de **obtener** es menos probable que una secuencia de salida atada \(`cout`, por ejemplo\) que se vaciará.  
  
 Una variación de la función de **obtener** especifica una dirección del búfer y el número máximo de caracteres para leer.  Esto es útil para limitar el número de caracteres enviados a una variable concreta, como en este ejemplo se muestra:  
  
```  
// ioo_get_function.cpp  
// compile with: /EHsc  
// Type up to 24 characters and a terminating character.   
// Any remaining characters can be extracted later.  
#include <iostream>  
using namespace std;  
  
int main()  
{  
   char line[25];  
   cout << " Type a line terminated by carriage return\n>";  
   cin.get( line, 25 );  
   cout << line << endl;  
}  
```  
  
### Entrada  
  
```  
1234  
```  
  
### Resultados del ejemplo  
  
```  
1234  
```  
  
##  <a name="vclrfthegetlinefunctionanchor13"></a> La función de getline  
 La función miembro de **getline** es similar a la función de **obtener** .  Ambas funciones permiten un tercer argumento que especifica el carácter de terminación de la entrada.  El valor predeterminado es el carácter de nueva línea.  Ambas funciones reserva un carácter a carácter de terminación requerido.  Sin embargo, **obtener** permite el carácter de terminación de la secuencia y **getline** quita el carácter de terminación.  
  
 El ejemplo siguiente especifica un carácter de terminación para el flujo de entrada:  
  
```  
// getline_func.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   char line[100];  
   cout << " Type a line terminated by 't'" << endl;  
   cin.getline( line, 100, 't' );  
   cout << line;  
}  
```  
  
### Entrada  
  
```  
test  
```  
  
##  <a name="vclrfthereadfunctionanchor14"></a> La función read  
 La función miembro de **read** lee bytes de un archivo a un área de memoria concreta.  El argumento length determina el número de bytes leídos.  Si no incluye este argumento, la lectura se detiene cuando el final del archivo físico se alcanza o, en el caso de un archivo en modo de texto, cuando se lee un carácter incrustado de `EOF` .  
  
 Este ejemplo lee un registro binario del archivo de nóminas en una estructura:  
  
```  
#include <fstream>  
#include <iostream>  
using namespace std;  
  
int main()  
{  
   struct  
   {  
      double salary;  
      char name[23];  
   } employee;  
  
   ifstream is( "payroll" );  
   if( is ) {  // ios::operator void*()  
      is.read( (char *) &employee, sizeof( employee ) );  
      cout << employee.name << ' ' << employee.salary << endl;  
   }  
   else {  
      cout << "ERROR: Cannot open file 'payroll'." << endl;  
   }  
}  
```  
  
 El programa se supone que los registros de datos están con formato exactamente como se especifica en la estructura sin finalizar los caracteres de retorno de carro y avance de línea.  
  
##  <a name="vclrftheseekgandtellgfunctionsanchor7"></a> Las funciones de seekg y de tellg  
 Secuencias de archivo de entrada conservan un puntero interno a la posición en el archivo donde leer los datos después.  Establece este puntero a la función de `seekg` , como se muestra aquí:  
  
```  
#include <iostream>  
#include <fstream>  
using namespace std;  
  
int main( )  
{  
   char ch;  
  
   ifstream tfile( "payroll" );  
   if( tfile ) {  
      tfile.seekg( 8 );        // Seek 8 bytes in (past salary)  
      while ( tfile.good() ) { // EOF or failure stops the reading  
         tfile.get( ch );  
         if( !ch ) break;      // quit on null  
         cout << ch;  
      }  
   }  
   else {  
      cout << "ERROR: Cannot open file 'payroll'." << endl;  
   }  
}  
```  
  
 Para utilizar `seekg` para implementar registro\- orientó los sistemas de administración de datos, multiplica el tamaño del registro de longitud fija por el número de registro para obtener la posición de bytes en relación con el fin del archivo, y después utiliza el objeto de **obtener** para leer el registro.  
  
 La función miembro de `tellg` devuelve el archivo actual colocar para leer.  Este valor es de `streampos`escrito, `typedef` definido en \<iostream\>.  El ejemplo siguiente se lee un archivo y muestra los mensajes que muestran las posiciones de espacios.  
  
```  
#include <fstream>  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   char ch;  
   ifstream tfile( "payroll" );  
   if( tfile ) {  
       while ( tfile.good( ) ) {  
          streampos here = tfile.tellg();  
          tfile.get( ch );  
          if ( ch == ' ' )  
             cout << "\nPosition " << here << " is a space";  
       }  
   }  
   else {  
      cout << "ERROR: Cannot open file 'payroll'." << endl;  
   }  
}  
```  
  
##  <a name="vclrftheclosefunctionforinputstreamsanchor15"></a> La función close para los flujos de entrada  
 La función miembro de **cerrar** cierra el archivo de disco asociado a un archivo de entrada transmitir y libera el identificador de archivo del sistema operativo.  [ifstream](../standard-library/basic-ifstream-class.md) destructor cierra el archivo automáticamente, pero puede utilizar la función de **cerrar** si necesita abrir otro archivo para el mismo objeto de secuencia.  
  
## Vea también  
 [Flujos de entrada](../standard-library/input-streams.md)