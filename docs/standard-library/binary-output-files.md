---
title: "Archivos de salida binarios | Microsoft Docs"
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
  - "datos binarios, archivos de salida binarios"
  - "archivos [C++], archivos de salida binarios"
  - "E/S [C++], archivos de salida binarios"
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Archivos de salida binarios
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las secuencias se diseñaron originalmente para el texto, por lo que el modo de salida predeterminado es texto.  En modo de texto, el carácter de nueva línea \(hexadecimal 10\) expanda un retorno\- avance de línea de carro \(de 16 bits solo\).  La extensión puede producir problemas, como se muestra aquí:  
  
```  
// binary_output_files.cpp  
// compile with: /EHsc  
#include <fstream>  
using namespace std;  
int iarray[2] = { 99, 10 };  
int main( )  
{  
    ofstream os( "test.dat" );  
    os.write( (char *) iarray, sizeof( iarray ) );  
}  
```  
  
 Se espera que este programa genere la secuencia de bytes {99, 0, 10, 0}; en su lugar, genera {99, 0, 13, 10, 0}, que produce problemas para un programa que cuenta con entrada binaria.  Si necesita el binario verdadero generar, en el que los caracteres se escriben sin traducir, puede especificar el binario generado utilizando el argumento de modo de constructor de [ofstream](../Topic/ofstream.md) :  
  
```  
// binary_output_files2.cpp  
// compile with: /EHsc  
#include <fstream>  
using namespace std;  
int iarray[2] = { 99, 10 };  
  
int main()  
{  
   ofstream ofs ( "test.dat", ios_base::binary );  
  
   // Exactly 8 bytes written  
   ofs.write( (char*)&iarray[0], sizeof(int)*2 );   
}  
```  
  
## Vea también  
 [Flujos de salida](../standard-library/output-streams.md)