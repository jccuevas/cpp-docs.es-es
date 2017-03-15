---
title: "basic_fstream (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::basic_fstream"
  - "basic_fstream"
  - "fstream/std::basic_fstream"
  - "std.basic_fstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_fstream (clase)"
ms.assetid: 8473817e-42a4-430b-82b8-b476c86bcf8a
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# basic_fstream (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que controla la inserción y la extracción de elementos y objetos codificados de un búfer de secuencia de la clase [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<`Elem`, `Tr`\>, con elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`.  
  
## Sintaxis  
  
```  
template <class Elem, class Tr = char_traits<Elem> >  
    class basic_fstream : public basic_iostream<Elem, Tr>  
```  
  
#### Parámetros  
 `Elem`  
 Elemento básico del búfer del archivo.  
  
 `Tr`  
 Características del elemento básico del búfer del archivo \(normalmente `char_traits`\<`Elem`\>\).  
  
## Comentarios  
 El objeto almacena un objeto de clase `basic_filebuf`\<`Elem`, `Tr`\>.  
  
> [!NOTE]
>  El puntero get y el puntero put de un objeto fstream **NO** son independientes el uno del otro.  Si el puntero get se mueve, también lo hace el puntero put.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo crear un objeto `basic_fstream` del que se puede leer y en el que se puede escribir.  
  
```  
// basic_fstream_class.cpp  
// compile with: /EHsc  
  
#include <fstream>  
#include <iostream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    fstream fs("fstream.txt", ios::in | ios::out | ios::trunc);  
    if (!fs.bad())  
    {  
        // Write to the file.  
        fs << "Writing to a basic_fstream object..." << endl;  
        fs.close();  
  
        // Dump the contents of the file to cout.  
        fs.open("fstream.txt", ios::in);  
        cout << fs.rdbuf();  
        fs.close();  
    }  
}  
```  
  
  **Escribiendo en un objeto basic\_fstream...**   
### Constructores  
  
|||  
|-|-|  
|[basic\_fstream](../Topic/basic_fstream::basic_fstream.md)|Construye un objeto de tipo `basic_fstream`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[cerrar](../Topic/basic_fstream::close.md)|Cierra un archivo.|  
|[is\_open](../Topic/basic_fstream::is_open.md)|Determina si un archivo está abierto.|  
|[abrir](../Topic/basic_fstream::open.md)|Abre un archivo.|  
|[rdbuf](../Topic/basic_fstream::rdbuf.md)|Devuelve la dirección del búfer de secuencia almacenado, de tipo puntero a [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<`Elem`, `Tr`\>.|  
|[swap](../Topic/basic_fstream::swap.md)|Intercambia el contenido de este objeto con el contenido de otro objeto `basic_fstream`.|  
  
## Requisitos  
 **Encabezado:** \<fstream\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)