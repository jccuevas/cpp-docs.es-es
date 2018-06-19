---
title: Funciones de miembro de flujo de archivos de salida | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- output streams [C++], member functions
ms.assetid: 38aaf710-8035-4a34-a0c4-123a5327f28a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a1cba80b18f94d5a833b238e19be8190a442146
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858466"
---
# <a name="output-file-stream-member-functions"></a>Funciones de miembro de flujo de archivos de salida

Las funciones miembro de flujo de salida tienen tres tipos: las que son equivalentes a los manipuladores, las que realizan operaciones de escritura sin formato y las que, de otro modo, modifican el estado de la secuencia y no tienen un manipulador ni un operador de inserción equivalente. Para la salida con formato secuencial, solo puede usar operadores de inserción y manipuladores. Para la salida de disco binario de acceso aleatorio, use otras funciones miembro, con o sin operadores de inserción.

## <a name="the-open-function-for-output-streams"></a>La función Open para flujos de salida

Para usar un flujo de archivos de salida ([ofstream](../standard-library/basic-ofstream-class.md)), debe asociar esa secuencia con un archivo de disco específico en el constructor o con la función **open**. Si usa la función **open**, puede volver a usar el mismo objeto de secuencia con una serie de archivos. En cualquier caso, los argumentos que describen el archivo son los mismos.

Cuando abre el archivo asociado con un flujo de salida, generalmente especifica una marca **open_mode**. Puede combinar estas marcas, que se definen como enumeradores en la clase `ios`, con el operador OR bit a bit ( &#124; ). Vea [ios_base::openmode](../standard-library/ios-base-class.md#openmode) para obtener una lista de los enumeradores.

Tres situaciones comunes de flujo de salida tienen en cuenta las opciones de modo:

- Crear un archivo. Si el archivo ya existe, la versión anterior se elimina.

   ```cpp
   ostream ofile("FILENAME");
   // Default is ios::out

   ofstream ofile("FILENAME", ios::out);
   // Equivalent to above
   ```

- Anexar registros a un archivo existente o crear uno si no existe.

   ```cpp
   ofstream ofile("FILENAME", ios::app);
   ```

- Abrir dos archivos, uno cada vez, en la misma secuencia.

   ```cpp
   ofstream ofile();
   ofile.open("FILE1", ios::in);
   // Do some output
   ofile.close();    // FILE1 closed
   ofile.open("FILE2", ios::in);
   // Do some more output
   ofile.close();    // FILE2 closed
   // When ofile goes out of scope it is destroyed.
   ```

## <a name="the-put"></a>La ubicación

La función **put** escribe un carácter en el flujo de salida. Las dos instrucciones siguientes son las mismas de manera predeterminada, pero la segunda se ve afectada por los argumentos de formato de la secuencia:

```cpp
cout.put('A');

// Exactly one character written
cout <<'A'; // Format arguments 'width' and 'fill' apply
```

## <a name="the-write"></a>La operación de escritura

La función **write** escribe un bloque de memoria en un flujo de archivos de salida. El argumento de longitud especifica el número de bytes escritos. Este ejemplo crea un flujo de archivos de salida y escribe el valor binario de la estructura `Date` en este:

```cpp
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

La función **write** no se detiene cuando llega a un carácter NULL, por lo que se escribe la estructura de clase completa. La función toma dos argumentos: un puntero `char` y un recuento de caracteres que se va a escribir. Tenga en cuenta la conversión necesaria a **char\*** antes de la dirección del objeto de estructura.

## <a name="the-seekp-and-tellp-functions"></a>Las funciones Seekp y Tellp

Un flujo de archivos de salida mantiene un puntero interno que señala a la posición donde los datos se van a escribir a continuación. La función miembro `seekp` establece este puntero y, por lo tanto, proporciona una salida de archivo de disco de acceso aleatorio. La función miembro `tellp` devuelve la posición del archivo. Para obtener ejemplos que usan el flujo de entrada equivalente a `seekp` y `tellp`, vea [Las funciones Seekp y Tellp](../standard-library/input-stream-member-functions.md).

## <a name="the-close-function-for-output-streams"></a>La función Close para flujos de salida

La función miembro **close** cierra el archivo de disco asociado con un flujo de archivos de salida. El archivo debe cerrarse para completar toda la salida de disco. En caso necesario, el destructor `ofstream` le cierra el archivo, pero puede usar la función **close** si necesita abrir otro archivo para el mismo objeto de secuencia.

El destructor de flujo de salida cierra automáticamente un archivo de secuencia solo si el constructor o la función miembro **open** ha abierto el archivo. Si pasa al constructor un descriptor de archivo para un archivo que ya está abierto o usa la función miembro **attach**, debe cerrar el archivo explícitamente.

## <a name="vclrferrorprocessingfunctionsanchor10"></a> Funciones de procesamiento de errores

Use estas funciones miembro para probar errores al escribir en una secuencia:

|Función|Valor devuelto|
|--------------|------------------|
|[bad](http://msdn.microsoft.com/Library/4038d331-e9c9-48b0-bf49-c6505744469c)|Devuelve **True** si hay un error irrecuperable.|
|[fail](http://msdn.microsoft.com/Library/619f1b36-1e72-4551-8b48-888ae4e370d2)|Devuelve **True** si hay un error irrecuperable o una condición "esperada", como un error de conversión, o si el archivo no se encuentra. A menudo se puede reanudar el procesamiento después de una llamada a **clear** con un argumento cero.|
|[good](http://msdn.microsoft.com/Library/77f0aa17-2ae1-48ae-8040-592d301e3972)|Devuelve **True** si no existe ninguna condición de error (irrecuperable o de otro tipo) y la marca de fin de archivo no se establece.|
|[eof](http://msdn.microsoft.com/Library/3087f631-1268-49cd-86cf-ff4108862329)|Devuelve **True** en la condición de fin de archivo.|
|[clear](http://msdn.microsoft.com/Library/dc172694-1267-45f8-8f5c-e822e16fc271)|Establece el estado de error interno. Si se ha llamado con los argumentos predeterminados, borra todos los bits de error.|
|[rdstate](http://msdn.microsoft.com/Library/e235e4e2-7e95-4777-a160-3938d263dd9c)|Devuelve el estado de error actual.|

El operador **!** se sobrecarga para realizar la misma función que la función **fail**. Por lo tanto, la expresión:

```cpp
if(!cout)...
```

equivale a:

```cpp
if(cout.fail())...
```

El operador **void\*()** se sobrecarga para ser el contrario del operador **!** por lo tanto, la expresión:

```cpp
if(cout)...
```

es igual a:

```cpp
if(!cout.fail())...
```

El operador **void\*()** no es equivalente a **good** porque no se prueba para el final del archivo.

## <a name="see-also"></a>Vea también

[Flujos de salida](../standard-library/output-streams.md)<br/>
