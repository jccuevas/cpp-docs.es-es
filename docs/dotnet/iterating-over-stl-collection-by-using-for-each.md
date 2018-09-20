---
title: Iterar por la colección de biblioteca estándar de C++ mediante for each | Microsoft Docs
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
ms.openlocfilehash: 92934e3f00bb34e6adfe101b0fea7abbe03600c2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383201"
---
# <a name="iterating-over-c-standard-library-collection-by-using-for-each"></a>Iterar por la colección de biblioteca estándar de C++ mediante for each

El `for each` palabra clave puede utilizarse para recorrer en iteración una colección de la biblioteca estándar de C++.

## <a name="all-platforms"></a>Todas las plataformas

Una colección de la biblioteca estándar de C++ es también se denomina un *contenedor*. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).

## <a name="examples"></a>Ejemplos

El siguiente ejemplo de código usa `for each` para recorrer en iteración un [ \<map >](../standard-library/map.md).

```cpp
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

### <a name="output"></a>Salida

```Output
Months with 30 days = 4
```

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se utiliza una referencia const (`const&`) para una variable de iteración con contenedores de la biblioteca estándar de C++. Puede usar una referencia (`&`) como una variable de iteración en cualquier colección de un tipo que se puede declarar como una *T*`&`.

```cpp
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

### <a name="output"></a>Salida

```Output
retval: 60
```

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

No hay ninguna observación específica de la plataforma sobre esta característica.

### <a name="requirements"></a>Requisitos

Opción del compilador: **/ZW**

## <a name="common-language-runtime"></a>Common Language Runtime

No hay ninguna observación específica de la plataforma sobre esta característica.

### <a name="requirements"></a>Requisitos

Opción del compilador: **/clr**

## <a name="see-also"></a>Vea también

[for each, in](../dotnet/for-each-in.md)<br/>
[Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)