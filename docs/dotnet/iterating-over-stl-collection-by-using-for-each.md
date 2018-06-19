---
title: Iterar por la colección de biblioteca estándar de C++ mediante for each | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DTL collections, iterating over
ms.assetid: 9358ca29-b982-4a19-bbfd-bef50fe66c9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 963c8a4213da756f03e95924940dc179bd305f60
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33131347"
---
# <a name="iterating-over-c-standard-library-collection-by-using-for-each"></a>Iterar por la colección de biblioteca estándar de C++ mediante for each
El `for each` palabra clave puede utilizarse para recorrer en iteración una colección de la biblioteca estándar de C++.  
  
## <a name="all-platforms"></a>Todas las plataformas  
 **Comentarios**  
  
 Una colección de la biblioteca estándar de C++ es también conocido como un *contenedor*. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).  
  
## <a name="examples"></a>Ejemplos  
 **Ejemplo**  
  
 El siguiente ejemplo de código usa `for each` para recorrer en iteración un [ \<mapa >](../standard-library/map.md).  
  
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
  
 **Salida**  
  
```Output  
Months with 30 days = 4  
```  
  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se utiliza una referencia constante (`const&`) para una variable de iteración con contenedores de la biblioteca estándar de C++. Puede usar una referencia (`&`) como una variable de iteración en una colección de un tipo que se puede declarar como una *T*`&`.  
  
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
  
 **Salida**  
  
```Output  
retval: 60  
```  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 **Comentarios**  
  
 No hay notas acerca de esta característica específica de la plataforma.  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **Comentarios**  
  
 No hay notas acerca de esta característica específica de la plataforma.  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
## <a name="see-also"></a>Vea también  
 [para cada uno, en](../dotnet/for-each-in.md)   
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)