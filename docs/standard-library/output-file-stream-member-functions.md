---
title: "Funciones de miembro de flujo de archivos de salida | Microsoft Docs"
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
  - "flujos de salida, funciones miembro"
ms.assetid: 38aaf710-8035-4a34-a0c4-123a5327f28a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Funciones de miembro de flujo de archivos de salida
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las funciones miembro del flujo de salida tienen tres tipos: los que son equivalentes a los manipuladores, los que realizan operaciones de escritura sin formato, y los que modifican de otra forma al estado de la secuencia y no tienen ningún operador equivalente de manipulador o inserción.  Para la salida secuencial, con formato, es posible que solo utiliza operadores y los manipuladores de inserción.  Para la salida binaria de acceso aleatorio de disco, utiliza otras funciones miembro, con o sin operadores de inserción.  
  
## La función open para secuencias de salida  
 Para utilizar una secuencia de archivo de salida \([ofstream](../Topic/ofstream.md)\), debe asociar que transmitir con un archivo de disco específico en el constructor o la función de **OPEN** .  Si utiliza la función de **OPEN** , puede reutilizar el mismo objeto de secuencia con una serie de archivos.  En cualquier caso, los argumentos que describen el archivo son iguales.  
  
 Al abrir el archivo asociado a una secuencia de salida, especifique normalmente un indicador de **open\_mode** .  Puede combinar estos marcadores, que se definen como enumeradores en la clase de `ios` , con el bit a bit OR \( &#124; \) operador.  Vea [ios\_base::openmode](../Topic/ios_base::openmode.md) para una lista de los enumeradores.  
  
 Tres escenarios comunes del flujo de salida implican opciones de modo:  
  
-   Crear un archivo.  Si el archivo ya existe, se elimina la versión antigua.  
  
    ```  
    ostream ofile( "FILENAME" );  // Default is ios::out  
    ofstream ofile( "FILENAME", ios::out ); // Equivalent to above  
    ```  
  
-   Anexando los registros a un archivo existente o crear uno si no existe.  
  
    ```  
    ofstream ofile( "FILENAME", ios::app );  
    ```  
  
-   Abra dos archivos, uno a la vez, en la misma secuencia.  
  
    ```  
    ofstream ofile();  
    ofile.open( "FILE1", ios::in );  
    // Do some output  
    ofile.close(); // FILE1 closed  
    ofile.open( "FILE2", ios::in );  
    // Do some more output  
    ofile.close(); // FILE2 closed  
    // When ofile goes out of scope it is destroyed.  
    ```  
  
## La función put  
 La función de **put** escribe un carácter en el flujo de salida.  Las dos instrucciones siguientes son iguales de forma predeterminada, pero la segunda se ven afectadas por los argumentos del formato de la secuencia:  
  
```  
cout.put( 'A' ); // Exactly one character written  
cout << 'A'; // Format arguments 'width' and 'fill' apply   
```  
  
## La función de escritura  
 La función de **escribir** escribe un bloque de memoria a una secuencia de archivo de salida.  El argumento length especifica el número de bytes escritos.  Este ejemplo crea un archivo de salida transmitir y escribe el valor binario de la estructura de `Date` :  
  
```  
// write_function.cpp  
// compile with: /EHsc  
#include <fstream>  
using namespace std;  
  
struct Date  
{  
   int mo, da, yr;  
};  
  
int main( )  
{  
   Date dt = { 6, 10, 92 };  
   ofstream tfile( "date.dat" , ios::binary );  
   tfile.write( (char *) &dt, sizeof dt );  
}  
```  
  
 La función de **escribir** no detiene cuando alcanza un carácter null, por lo que se escribe la estructura de clase completa.  La función toma dos argumentos: un puntero de `char` y un recuento de caracteres a escribir.  Observe necesario para convertir a **char\*** antes de la dirección del objeto de la estructura.  
  
## Las funciones de seekp y de tellp  
 Una secuencia de archivo de salida mantiene un puntero interno que señale a la posición donde escribir los datos después.  La función miembro de `seekp` establece este puntero y proporciona así la salida de acceso aleatorio de archivo de disco.  La función miembro de `tellp` devuelve la posición del archivo.  Para obtener ejemplos que utilizan los equivalentes del flujo de entrada a `seekp` y a `tellp`, vea [Las funciones de seekg y de tellg](../standard-library/input-stream-member-functions.md).  
  
## La función close en las secuencias de salida  
 La función miembro de **cerrar** cierra el archivo de disco asociado a una secuencia de archivo de salida.  El archivo se debe cerrar para completar toda la salida del disco.  En caso necesario, `ofstream` destructor cierra el archivo automáticamente, pero puede utilizar la función de **cerrar** si necesita abrir otro archivo para el mismo objeto de secuencia.  
  
 El flujo de salida destructor automáticamente cierra el archivo de una secuencia solo si abrió el constructor o la función miembro de **OPEN** el archivo.  Si se pasa al constructor descriptor de archivo para un archivo de ya\- Abrir o utiliza la función miembro de **asociar** , debe cerrar el archivo explícitamente.  
  
##  <a name="vclrferrorprocessingfunctionsanchor10"></a> Funciones de procesamiento del error  
 Utilice estas funciones miembro para comprobar los errores mientras escribe en una secuencia:  
  
|Función|Valor devuelto|  
|-------------|--------------------|  
|[erróneo](../Topic/basic_ios::bad.md)|Devuelve **true** si hay un error irrecuperable.|  
|[error](../Topic/basic_ios::fail.md)|Devuelve **true** si hay un error irrecuperable o condición “esperada”, como un error de conversión, o si no se encuentra el archivo.  El procesamiento puede reanudar a menudo después de una llamada a **desactivada** con un argumento cero.|  
|[kind](../Topic/basic_ios::good.md)|Devuelve **true** si no hay ninguna condición de error irrecuperable \(u otro\) y la marca de fin de archivo no está establecida.|  
|[EOF](../Topic/basic_ios::eof.md)|Devuelve **true** en la condición de fin de archivo.|  
|[clear](../Topic/basic_ios::clear.md)|Establece el estado del error interno.  Si se llama con argumentos predeterminados, borra todos los bits del error.|  
|[rdstate](../Topic/basic_ios::rdstate.md)|Devuelve el estado actual del error.|  
  
 Sobrecarga el operador de \#\#\#\!para realizar la misma función que la función de **error** .  Así la expresión:  
  
```  
if( !cout)...  
```  
  
 equivale a:  
  
```  
if( cout.fail() )...  
```  
  
 Sobrecarga el operador de **void\*\(\)** para ser el contrario que el operador de \#\#\#\!; así la expresión:  
  
```  
if( cout)...  
```  
  
 es igual a:  
  
```  
if( !cout.fail() )...  
```  
  
 El operador de **void\*\(\)** no es equivalente a **good** porque no prueba para el final del archivo.  
  
## Vea también  
 [Flujos de salida](../standard-library/output-streams.md)