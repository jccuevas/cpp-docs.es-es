---
title: "Iterar por una colecci&#243;n STL mediante for each | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "colecciones DTL, recorriendo en iteración"
ms.assetid: 9358ca29-b982-4a19-bbfd-bef50fe66c9a
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Iterar por una colecci&#243;n STL mediante for each
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La palabra clave de `for each` se puede utilizar para recorrer en iteración una colección de la biblioteca estándar de C\+\+ \(STL\).  
  
## Todas las plataformas  
 **Comentarios**  
  
 Una colección de STL también se conoce como *contenedor*.  Para obtener más información, vea [Contenedores de STL](../standard-library/stl-containers.md).  
  
## Ejemplos  
 **Ejemplo**  
  
 El ejemplo de código siguiente se utiliza `for each` para recorrer en iteración [\< map \>](../standard-library/map.md).  
  
```  
// for_each_stl.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
#include <string>  
using namespace std;  
  
int main() {  
   int retval  = 0;  
   map<string, int> months;  
  
   months["january"] = 31;  
   months["february"] = 28;  
   months["march"] = 31;  
   months["april"] = 30;  
   months["may"] = 31;  
   months["june"] = 30;  
   months["july"] = 31;  
   months["august"] = 31;  
   months["september"] = 30;  
   months["october"] = 31;  
   months["november"] = 30;  
   months["december"] = 31;  
  
   map<string, int> months_30;  
  
   for each( pair<string, int> c in months )  
      if ( c.second == 30 )  
         months_30[c.first] = c.second;  
  
   for each( pair<string, int> c in months_30 )  
      retval++;  
  
   cout << "Months with 30 days = " << retval << endl;  
}  
```  
  
 **Resultados**  
  
  **Meses con 30 días \= 4** **Ejemplo**  
  
 El ejemplo de código siguiente se utiliza una referencia const \(`const&`\) para una variable de iteración con los contenedores STL.  Puede utilizar una referencia \(`&`\) como variable de iteración de cualquier colección de un tipo que puede declararse como *T*`&`.  
  
```  
// for_each_stl_2.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
using namespace std;  
  
int main() {  
   int retval = 0;  
  
   vector<int> col(3);  
   col[0] = 10;  
   col[1] = 20;  
   col[2] = 30;  
  
   for each( const int& c in col )  
      retval += c;  
  
   cout << "retval: " << retval << endl;  
}  
```  
  
 **Resultados**  
  
  **retval: 60**   
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **Comentarios**  
  
 No hay notas plataforma\-específicas sobre esta característica.  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **Comentarios**  
  
 No hay notas plataforma\-específicas sobre esta característica.  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
## Vea también  
 [for each, in](../dotnet/for-each-in.md)   
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)