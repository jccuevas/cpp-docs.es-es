---
title: "basic_filebuf (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.basic_filebuf"
  - "fstream/std::basic_filebuf"
  - "std::basic_filebuf"
  - "basic_filebuf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_filebuf (clase)"
ms.assetid: 3196ba5c-bf38-41bd-9a95-70323ddfca1a
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# basic_filebuf (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un búfer de secuencia que controla la transmisión de elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`, a y desde una secuencia de elementos almacenados en un archivo externo.  
  
## Sintaxis  
  
```  
template <class Elem, class Tr = char_traits<Elem> >  
    class basic_filebuf : public basic_streambuf<Elem, Tr>  
```  
  
#### Parámetros  
 `Elem`  
 Elemento básico del búfer del archivo.  
  
 `Tr`  
 Características del elemento básico del búfer del archivo \(normalmente `char_traits`\<`Elem`\>\).  
  
## Comentarios  
 La clase de plantilla describe un búfer de secuencia que controla la transmisión de elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`, a y desde una secuencia de elementos almacenados en un archivo externo.  
  
> [!NOTE]
>  Los objetos de tipo `basic_filebuf` se crean con un búfer interno de tipo `char *`, independientemente del `char_type` especificado por el parámetro de tipo `Elem`.  Esto significa que una cadena Unicode \(que contiene caracteres `wchar_t`\) se convertirá en una cadena ANSI \(que contiene caracteres `char`\) antes de que se escriba en el búfer interno.  Para almacenar cadenas Unicode en el búfer, cree un nuevo búfer de tipo `wchar_t` y establézcalo mediante el método [basic\_streambuf::pubsetbuf](../Topic/basic_streambuf::pubsetbuf.md)`()`.  Para ver un ejemplo que muestra este comportamiento, vea a continuación.  
  
 Un objeto de clase `basic_filebuf`\<`Elem`, `Tr`\> almacena un puntero de archivo, que designa el objeto `FILE` que controla la secuencia asociada a un archivo abierto.  También almacena punteros en dos facetas de conversión de archivo para que los usen las funciones miembro protegidas [overflow](../Topic/basic_filebuf::overflow.md) y [underflow](../Topic/basic_filebuf::underflow.md).  Para obtener más información, consulte [basic\_filebuf::open](../Topic/basic_filebuf::open.md).  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo forzar un objeto de tipo `basic_filebuf<wchar_t>` para almacenar caracteres Unicode en su búfer interno mediante una llamada al método `pubsetbuf()`.  
  
```  
// unicode_basic_filebuf.cpp  
// compile with: /EHsc  
  
#include <iostream>  
#include <string>  
#include <fstream>  
#include <iomanip>  
#include <memory.h>  
#include <string.h>  
  
#define IBUFSIZE 16  
  
using namespace std;  
  
void hexdump(const string& filename);  
  
int main()  
{  
    wchar_t* wszHello = L"Hello World";  
    wchar_t wBuffer[128];  
  
    basic_filebuf<wchar_t> wOutFile;  
  
    // Open a file, wcHello.txt, then write to it, then dump the  
    // file's contents in hex  
    wOutFile.open("wcHello.txt",  
        ios_base::out | ios_base::trunc | ios_base::binary);  
    if(!wOutFile.is_open())  
    {  
        cout << "Error Opening wcHello.txt\n";  
        return -1;  
    }  
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));  
    wOutFile.close();  
    cout << "Hex Dump of wcHello.txt - note that output is ANSI chars:\n";  
    hexdump(string("wcHello.txt"));  
  
    // Open a file, wwHello.txt, then set the internal buffer of  
    // the basic_filebuf object to be of type wchar_t, then write  
    // to the file and dump the file's contents in hex  
    wOutFile.open("wwHello.txt",  
        ios_base::out | ios_base::trunc | ios_base::binary);  
    if(!wOutFile.is_open())  
    {  
        cout << "Error Opening wwHello.txt\n";  
        return -1;  
    }  
    wOutFile.pubsetbuf(wBuffer, (streamsize)128);  
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));  
    wOutFile.close();  
    cout << "\nHex Dump of wwHello.txt - note that output is wchar_t chars:\n";  
    hexdump(string("wwHello.txt"));  
  
    return 0;  
}  
  
// dump contents of filename to stdout in hex  
void hexdump(const string& filename)  
{  
    fstream ifile(filename.c_str(),  
        ios_base::in | ios_base::binary);  
    char *ibuff = new char[IBUFSIZE];  
    char *obuff = new char[(IBUFSIZE*2)+1];  
    int i;  
  
    if(!ifile.is_open())  
    {  
        cout << "Cannot Open " << filename.c_str()  
             << " for reading\n";  
        return;  
    }  
    if(!ibuff || !obuff)  
    {  
        cout << "Cannot Allocate buffers\n";  
        ifile.close();  
        return;  
    }  
  
    while(!ifile.eof())  
    {  
        memset(obuff,0,(IBUFSIZE*2)+1);  
        memset(ibuff,0,IBUFSIZE);  
        ifile.read(ibuff,IBUFSIZE);  
  
        // corner case where file is exactly a multiple of  
        // 16 bytes in length  
        if(ibuff[0] == 0 && ifile.eof())  
            break;  
  
        for(i = 0; i < IBUFSIZE; i++)  
        {  
            if(ibuff[i] >= ' ')  
                obuff[i] = ibuff[i];  
            else  
                obuff[i] = '.';  
  
            cout << setfill('0') << setw(2) << hex  
                 << (int)ibuff[i] << ' ';  
        }  
        cout << "  " << obuff << endl;  
    }  
    ifile.close();  
}  
```  
  
  **Volcado hexadecimal de wcHello.txt: observe que el resultado es en caracteres ANSI:**  
**48 65 6c 6c 6f 20 57 6f 72 6c 64 00 00 00 00 00   Hello World.....  Volcado hexadecimal de wwHello.txt: observe que el resultado es en caracteres wchar\_t:**  
**48 00 65 00 6c 00 6c 00 6f 00 20 00 57 00 6f 00   H.e.l.l.o.  .W.o.  72 00 6c 00 64 00 00 00 00 00 00 00 00 00 00 00   r.l.d...........**    
### Constructores  
  
|||  
|-|-|  
|[basic\_filebuf](../Topic/basic_filebuf::basic_filebuf.md)|Construye un objeto de tipo `basic_filebuf`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[char\_type](../Topic/basic_filebuf::char_type.md)|Asocia un nombre de tipo con el parámetro de plantilla `Elem`.|  
|[int\_type](../Topic/basic_filebuf::int_type.md)|Hace que este tipo del ámbito `basic_filebuf` sea equivalente al tipo con el mismo nombre del ámbito `Tr`.|  
|[off\_type](../Topic/basic_filebuf::off_type.md)|Hace que este tipo del ámbito `basic_filebuf` sea equivalente al tipo con el mismo nombre del ámbito `Tr`.|  
|[pos\_type](../Topic/basic_filebuf::pos_type.md)|Hace que este tipo del ámbito `basic_filebuf` sea equivalente al tipo con el mismo nombre del ámbito `Tr`.|  
|[traits\_type](../Topic/basic_filebuf::traits_type.md)|Asocia un nombre de tipo con el parámetro de plantilla `Tr`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[cerrar](../Topic/basic_filebuf::close.md)|Cierra un archivo.|  
|[is\_open](../Topic/basic_filebuf::is_open.md)|Indica si un archivo está abierto.|  
|[abrir](../Topic/basic_filebuf::open.md)|Abre un archivo.|  
|[desbordamiento](../Topic/basic_filebuf::overflow.md)|Función virtual protegida a la que se puede llamar cuando se inserta un carácter nuevo en un búfer lleno.|  
|[pbackfail](../Topic/basic_filebuf::pbackfail.md)|La función miembro virtual protegida intenta colocar un elemento en el flujo de entrada y, a continuación, convertirlo en el elemento actual \(indicado por el puntero siguiente\).|  
|[seekoff](../Topic/basic_filebuf::seekoff.md)|La función miembro virtual protegida intenta modificar las posiciones actuales para los flujos controlados.|  
|[seekpos](../Topic/basic_filebuf::seekpos.md)|La función miembro virtual protegida intenta modificar las posiciones actuales para los flujos controlados.|  
|[setbuf](../Topic/basic_filebuf::setbuf.md)|La función miembro virtual protegida realiza una determinada operación para cada búfer de secuencia derivado.|  
|[Swap](../Topic/basic_filebuf::swap.md)|Intercambia el contenido de `basic_filebuf` por el contenido del parámetro `basic_filebuf` proporcionado.|  
|[sync](../Topic/basic_filebuf::sync.md)|Función virtual protegida que intenta sincronizar las secuencias controladas con cualquier flujo externo asociado.|  
|[uflow](../Topic/basic_streambuf::uflow.md)|Función virtual protegida que extrae el elemento actual de la secuencia de entrada.|  
|[underflow](../Topic/basic_filebuf::underflow.md)|Función virtual protegida que extrae el elemento actual de la secuencia de entrada.|  
  
## Requisitos  
 **Encabezado:** \<fstream\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<fstream\>](../standard-library/fstream.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)