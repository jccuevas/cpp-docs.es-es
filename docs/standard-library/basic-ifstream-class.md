---
title: "basic_ifstream (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "basic_ifstream"
  - "fstream/std::basic_ifstream"
  - "std::basic_ifstream"
  - "std.basic_ifstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_ifstream (clase)"
ms.assetid: 366cd9a7-efc4-4b7f-ba10-c8271e47ffcf
caps.latest.revision: 23
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_ifstream (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de secuencia de la clase [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<`Elem`, `Tr`\>, con elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`.  
  
## Sintaxis  
  
```  
template <class Elem, class Tr = char_traits<Elem> >  
    class basic_ifstream : public basic_istream<Elem, Tr>  
```  
  
#### Parámetros  
 `Elem`  
 Elemento básico del búfer del archivo.  
  
 `Tr`  
 Características del elemento básico del búfer del archivo \(normalmente `char_traits`\<`Elem`\>\).  
  
## Comentarios  
 El objeto almacena un objeto de clase `basic_filebuf`\<`Elem`, `Tr`\>.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo leer texto de un archivo.  
  
```  
// basic_ifstream_class.cpp  
// compile with: /EHsc  
  
#include <fstream>  
#include <iostream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ifstream ifs("basic_ifstream_class.txt");  
    if (!ifs.bad())  
    {  
        // Dump the contents of the file to cout.  
        cout << ifs.rdbuf();  
        ifs.close();  
    }  
}  
```  
  
## Entrada: basic\_ifstream\_class.txt  
  
```  
This is the contents of basic_ifstream_class.txt.  
```  
  
## Resultado  
  
```  
This is the contents of basic_ifstream_class.txt.  
```  
  
### Constructores  
  
|||  
|-|-|  
|[basic\_ifstream](../Topic/basic_ifstream::basic_ifstream.md)|Inicializa una nueva instancia de un objeto `basic_ifstream`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[cerrar](../Topic/basic_ifstream::close.md)|Cierra un archivo.|  
|[is\_open](../Topic/basic_ifstream::is_open.md)|Determina si un archivo está abierto.|  
|[abrir](../Topic/basic_ifstream::open.md)|Abre un archivo.|  
|[rdbuf](../Topic/basic_ifstream::rdbuf.md)|Devuelve la dirección del búfer de secuencia almacenado.|  
|[swap](../Topic/basic_ifstream::swap.md)|Intercambia el contenido de `basic_ifstream` por el contenido del `basic_ifstream` proporcionado.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../Topic/basic_ifstream::operator=.md)|Asigna el contenido de este objeto de secuencia.  Se trata de una asignación de movimiento que implica un `rvalue` que no deja ninguna copia atrás.|  
  
## Requisitos  
 **Encabezado:** \<fstream\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)