---
title: "basic_ofstream (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::basic_ofstream"
  - "basic_ofstream"
  - "std.basic_ofstream"
  - "fstream/std::basic_ofstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_ofstream (clase)"
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# basic_ofstream (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de secuencia de la clase [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<`Elem`, `Tr`\>, con elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`.  
  
## Sintaxis  
  
```  
template <class Elem, class Tr = char_traits<Elem> >  
    class basic_ofstream : public basic_ostream<Elem, Tr>  
```  
  
#### Parámetros  
 `Elem`  
 Elemento básico del búfer del archivo.  
  
 `Tr`  
 Características del elemento básico del búfer del archivo \(normalmente `char_traits`\<`Elem`\>\).  
  
## Comentarios  
 Cuando la especialización `wchar_t` de `basic_ofstream` escribe en el archivo, si el archivo se abre en modo de texto, escribirá una secuencia MBCS.  La representación interna usará un búfer de caracteres `wchar_t`.  
  
 El objeto almacena un objeto de clase `basic_filebuf`\<`Elem`, `Tr`\>.  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestra cómo crear un objeto `basic_ofstream` y escribir texto en él.  
  
```  
// basic_ofstream_class.cpp  
// compile with: /EHsc  
#include <fstream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ofstream ofs("ofstream.txt");  
    if (!ofs.bad())  
    {  
        ofs << "Writing to a basic_ofstream object..." << endl;  
        ofs.close();  
    }  
}  
```  
  
### Constructores  
  
|||  
|-|-|  
|[basic\_ofstream](../Topic/basic_ofstream::basic_ofstream.md)|Crea un objeto del tipo `basic_ofstream`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[cerrar](../Topic/basic_ofstream::close.md)|Cierra un archivo.|  
|[is\_open](../Topic/basic_ofstream::is_open.md)|Determina si un archivo está abierto.|  
|[abrir](../Topic/basic_ofstream::open.md)|Abre un archivo.|  
|[rdbuf](../Topic/basic_ofstream::rdbuf.md)|Devuelve la dirección del búfer de secuencia almacenado.|  
|[swap](../Topic/basic_ofstream::swap.md)|Intercambia el contenido de este `basic_ofstream` con el contenido del `basic_ofstream` proporcionado.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../Topic/basic_ofstream::operator=.md)|Asigna el contenido de este objeto de secuencia.  Se trata de una asignación de movimiento que implica un `rvalue reference` que no deja ninguna copia atrás.|  
  
## Requisitos  
 **Encabezado:** \<fstream\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [basic\_ostream \(Clase\)](../standard-library/basic-ostream-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)