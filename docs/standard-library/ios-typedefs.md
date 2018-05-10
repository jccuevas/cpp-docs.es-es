---
title: Definiciones de tipo &lt;ios&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
ms.openlocfilehash: 7ee458d0d84b63de52a2840a7a86903afed1704d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="ltiosgt-typedefs"></a>Definiciones de tipo &lt;ios&gt;

||||
|-|-|-|
|[ios](#ios)|[streamoff](#streamoff)|[streampos](#streampos)|
|[streamsize](#streamsize)|[wios](#wios)|[wstreampos](#wstreampos)|

## <a name="ios"></a>  ios

Es compatible con la clase ios de la antigua biblioteca iostream.

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>Comentarios

Tipo sinónimo de la clase de plantilla [basic_ios](../standard-library/basic-ios-class.md), especializada en elementos del tipo `char` con rasgos de caracteres predeterminados.

## <a name="streamoff"></a>  streamoff

Admite operaciones internas.

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>Comentarios

El tipo es un entero con signo que describe un objeto que puede almacenar un desplazamiento de bytes implicado en varias operaciones de posicionamiento de flujo. La representación tiene al menos 32 bits de valor. No es necesariamente lo bastante grande como para representar una posición de byte arbitraria en un flujo. El valor **streamoff(-1)** suele indicar un desplazamiento erróneo.

## <a name="streampos"></a>  streampos

Contiene la posición actual del puntero de búfer o el puntero de archivo.

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>Comentarios

Tipo sinónimo de [fpos](../standard-library/fpos-class.md)< `mbstate_t`>.

### <a name="example"></a>Ejemplo

```cpp
// ios_streampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   ofstream x( "iostream.txt" );
   x << "testing";
   streampos y = x.tellp( );
   cout << y << endl;
}
```

```Output
7
```

## <a name="streamsize"></a>  streamsize

Denota el tamaño del flujo.

```cpp
#ifdef _WIN64
    typedef __int64 streamsize;
#else
    typedef int streamsize;
#endif
```

### <a name="remarks"></a>Comentarios

El tipo es un entero con signo que describe un objeto que puede almacenar un recuento del número de elementos implicados en varias operaciones de flujo. La representación tiene al menos 16 bits. No es necesariamente lo bastante grande como para representar una posición de byte arbitraria en un flujo.

### <a name="example"></a>Ejemplo

Después de compilar y ejecutar el siguiente programa, examine el archivo test.txt para ver el efecto de establecer `streamsize`.

```cpp
// ios_streamsize.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   char a[16] = "any such text";
   ofstream x( "test.txt" );
   streamsize y = 6;
   x.write( a, y );
}
```

## <a name="wios"></a>  wios

Es compatible con la clase wios de la antigua biblioteca iostream.

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>Comentarios

Tipo sinónimo de la clase de plantilla [basic_ios](../standard-library/basic-ios-class.md), especializada en elementos del tipo `wchar_t` con rasgos de caracteres predeterminados.

## <a name="wstreampos"></a>  wstreampos

Contiene la posición actual del puntero de búfer o el puntero de archivo.

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>Comentarios

Tipo sinónimo de [fpos](../standard-library/fpos-class.md)< `mbstate_t`>.

### <a name="example"></a>Ejemplo

```cpp
// ios_wstreampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   wofstream xw( "wiostream.txt" );
   xw << L"testing";
   wstreampos y = xw.tellp( );
   cout << y << endl;
}
```

```Output
7
```

## <a name="see-also"></a>Vea también

[\<ios>](../standard-library/ios.md)<br/>
