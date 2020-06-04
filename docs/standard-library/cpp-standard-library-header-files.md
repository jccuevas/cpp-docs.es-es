---
title: Archivos de encabezado de la biblioteca estándar de C++
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: 207e7b7d2d689d3912399e3a867102ee893e003a
ms.sourcegitcommit: 1a8fac06478da8bee1f6d70e25afbad94144af1a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2020
ms.locfileid: "84226041"
---
# <a name="c-standard-library-header-files"></a>Archivos de encabezado de la biblioteca estándar de C++

Archivos de encabezado de la biblioteca estándar de C++ y extensiones, por categoría.

## <a name="headers-by-category"></a>Encabezados por categoría

::: moniker range=">=vs-2017"

| Categoría | Encabezados |
| - | - |
| [Algoritmos](../cpp/algorithms-modern-cpp.md) | [\<algorithm>](algorithm.md), [\<cstdlib>](cstdlib.md), [\<numeric>](numeric.md) |
| Operaciones atómicas |  [\<atomic>](atomic.md)<sup>279</sup> |
| Contenedores de la biblioteca de C | [\<cassert>](cassert.md), [\<ccomplex>](ccomplex.md) <sup>11 a b</sup>, [\<cctype>](cctype.md) , [\<cerrno>](cerrno.md) , [\<cfenv>](cfenv.md) <sup>11</sup>, [\<cfloat>](cfloat.md) , [\<cinttypes>](cinttypes.md) <sup>11</sup>, [\<ciso646>](ciso646.md) <sup>b</sup>, [\<climits>](climits.md) , [\<clocale>](clocale.md) , [\<cmath>](cmath.md) , [\<csetjmp>](csetjmp.md) , [\<csignal>](csignal.md) , [\<cstdalign>](cstdalign.md) <sup>11 a b</sup>, [\<cstdarg>](cstdarg.md) , [\<cstdbool>](cstdbool.md) <sup>11 a b</sup>, [\<cstddef>](cstddef.md) , [\<cstdint>](cstdint.md) <sup>11</sup>, [\<cstdio>](cstdio.md) , [\<cstdlib>](cstdlib.md) , [\<cstring>](cstring.md) , [\<ctgmath>](ctgmath.md) <sup>11 a b</sup>, [\<ctime>](ctime.md) , [\<cuchar>](cuchar.md) <sup>11</sup>, [\<cwchar>](cwchar.md) ,[\<cwctype>](cwctype.md) |
| Conceptos | \<concepts><sup>20</sup> |
| [Containers](../cpp/containers-modern-cpp.md) | |
| Contenedores de secuencias | [\<array>](array.md)<sup>11</sup>, [\<deque>](deque.md) , [\<forward_list>](forward-list.md) <sup>11</sup>, [\<list>](list.md) ,[\<vector>](vector.md) |
| Contenedores asociativos ordenados| [\<map>](map.md), [\<set>](set.md) |
| Contenedores asociativos desordenados | [\<unordered_map>](unordered-map.md)<sup>11</sup>, [\<unordered_set>](unordered-set.md) <sup>11</sup> |
| Adaptadores de contenedor | [\<queue>](queue.md), [\<stack>](stack.md) |
| Vistas de contenedor | [\<span>](span.md)<sup>20</sup> |
| [Errores y control de excepciones](../cpp/errors-and-exception-handling-modern-cpp.md) | [\<cassert>](cassert.md), [\<exception>](exception.md) , [\<stdexcept>](stdexcept.md) , [\<system_error>](system-error.md) <sup>11</sup> |
| Utilidades generales | \<any><sup>17</sup>, [\<bitset>](bitset.md) , \<charconv> <sup>17</sup>, [\<cstdlib>](cstdlib.md) , \<execution> <sup>17</sup>, [\<functional>](functional.md) , [\<memory>](memory.md) , \<memory_resource> <sup>17</sup>, \<optional> <sup>17</sup>, [\<ratio>](ratio.md) <sup>11</sup>, [\<scoped_allocator>](scoped-allocator.md) <sup>11</sup>, [\<tuple>](tuple.md) <sup>11</sup>, [\<type_traits>](type-traits.md) <sup>11</sup>, [\<typeindex>](typeindex.md) <sup>11</sup>, [\<utility>](utility.md) , \<variant> <sup>17</sup> |
| [E/s y formato](../text/string-and-i-o-formatting-modern-cpp.md) | [\<cinttypes>](cinttypes.md)<sup>11</sup>, [\<cstdio>](cstdio.md) , [\<filesystem>](filesystem.md) <sup>17</sup>, [\<fstream>](fstream.md) , [\<iomanip>](iomanip.md) , [\<ios>](ios.md) , [\<iosfwd>](iosfwd.md) , [\<iostream>](iostream.md) , [\<istream>](istream.md) , [\<ostream>](ostream.md) , [\<sstream>](sstream.md) , [\<streambuf>](streambuf.md) , [\<strstream>](strstream.md) <sup>c</sup>, \<syncstream> <sup>20</sup> |
| Iterators | [\<iterator>](iterator.md) |
| Compatibilidad con idiomas | [\<cfloat>](cfloat.md), [\<climits>](climits.md) , [\<codecvt>](codecvt.md) <sup>11 a</sup>, \<compare> <sup>20</sup>, \<contract> <sup>20</sup>, \<coroutine> <sup>20</sup>, [\<csetjmp>](csetjmp.md) , [\<csignal>](csignal.md) , [\<cstdarg>](cstdarg.md) , [\<cstddef>](cstddef.md) , [\<cstdint>](cstdint.md) <sup>11</sup>, [\<cstdlib>](cstdlib.md) , [\<exception>](exception.md) , [\<initializer_list>](initializer-list.md) <sup>11</sup>, [\<limits>](limits.md) , [\<new>](new.md) , [\<typeinfo>](typeinfo.md) , \<version> <sup>20</sup> |
| Localización | [\<clocale>](clocale.md), [\<codecvt>](codecvt.md) <sup>11 a</sup>, [\<cvt/wbuffer>](cvt-wbuffer.md) , [\<cvt/wstring>](cvt-wstring.md) ,[\<locale>](locale.md) |
| Matemáticas y valores numéricos | \<bit><sup>20</sup>, [\<cfenv>](cfenv.md) <sup>11</sup>, [\<cmath>](cmath.md) , [\<complex>](complex.md) , [\<cstdlib>](cstdlib.md) , [\<limits>](limits.md) , [\<numeric>](numeric.md) , [\<random>](random.md) <sup>11</sup>, [\<ratio>](ratio.md) <sup>11</sup>,[\<valarray>](valarray.md) |
| [Administración de memoria](../cpp/smart-pointers-modern-cpp.md) | [\<allocators>](allocators-header.md), [\<memory>](memory.md) , \<memory_resource> <sup>17</sup>, [\<new>](new.md) , [\<scoped_allocator>](scoped-allocator.md) <sup>11</sup> |
| Subprocesamiento múltiple | [\<atomic>](atomic.md)<sup>11</sup>, [\<condition_variable>](condition-variable.md) <sup>11</sup>, [\<future>](future.md) <sup>11</sup>, [\<mutex>](mutex.md) <sup>11</sup>, [\<shared_mutex>](shared-mutex.md) <sup>14</sup>, [\<thread>](thread.md) <sup>11</sup> |
| Intervalos | \<ranges><sup>20</sup> |
| Expresiones regulares | [\<regex>](regex.md)<sup>279</sup> |
| Cadenas y datos de caracteres | [\<cctype>](cctype.md), [\<cstdlib>](cstdlib.md) , [\<cstring>](cstring.md) , [\<cuchar>](cuchar.md) <sup>11</sup>, [\<cwchar>](cwchar.md) , [\<cwctype>](cwctype.md) , [\<regex>](regex.md) <sup>11</sup>, [\<string>](string.md) , [\<string_view>](string-view.md) <sup>17</sup> |
| Hora | [\<chrono>](chrono.md)<sup>11</sup>,[\<ctime>](ctime.md) |

<sup>11</sup> agregado en el estándar c++ 11. \
<sup>14</sup> agregado en el estándar de c++ 14. \
<sup>17</sup> agregado en el estándar c++ 17. \
<sup>20</sup> agregado en el borrador c++ 20 estándar. \
<sup>un</sup> desusado en el estándar c++ 17. \
<sup>b</sup> se ha quitado en el borrador del estándar c++ 20. \
<sup>c</sup> en desuso en el estándar de c++ 98.

::: moniker-end

::: moniker range="vs-2015"

|Categoría|Encabezados|
|-|-|
|[Algoritmos](../cpp/algorithms-modern-cpp.md)|[\<algorithm>](algorithm.md)|
|Contenedores de la biblioteca de C|[\<cassert>](cassert.md), [\<cctype>](cctype.md), [\<cerrno>](cerrno.md), [\<cfenv>](cfenv.md), [\<cfloat>](cfloat.md), [\<cinttypes>](cinttypes.md), [\<ciso646>](ciso646.md), [\<climits>](climits.md), [\<clocale>](clocale.md), [\<cmath>](cmath.md), [\<csetjmp>](csetjmp.md), [\<csignal>](csignal.md), [\<cstdarg>](cstdarg.md), [\<cstdbool>](cstdbool.md), [\<cstddef>](cstddef.md), [\<cstdint>](cstdint.md), [\<cstdio>](cstdio.md), [\<cstdlib>](cstdlib.md), [\<cstring>](cstring.md), [\<ctgmath>](ctgmath.md), [\<ctime>](ctime.md), [\<cwchar>](cwchar.md), [\<cwctype>](cwctype.md)|
|[Containers](../cpp/containers-modern-cpp.md)||
|Contenedores de secuencias|[\<array>](array.md), [\<deque>](deque.md), [\<forward_list>](forward-list.md), [\<list>](list.md), [\<vector>](vector.md)|
|Contenedores asociativos ordenados| [\<map>](map.md), [\<set>](set.md)|
|Contenedores asociativos desordenados|[\<unordered_map>](unordered-map.md), [\<unordered_set>](unordered-set.md)|
|Contenedores de adaptador|[\<queue>](queue.md), [\<stack>](stack.md)|
|[Errores y control de excepciones](../cpp/errors-and-exception-handling-modern-cpp.md)|[\<exception>](exception.md), [\<stdexcept>](stdexcept.md), [\<system_error>](system-error.md)|
|[E/s y formato](../text/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md), [\<fstream>](fstream.md), [\<iomanip>](iomanip.md), [\<ios>](ios.md), [\<iosfwd>](iosfwd.md), [\<iostream>](iostream.md), [\<istream>](istream.md), [\<ostream>](ostream.md), [\<sstream>](sstream.md), [\<streambuf>](streambuf.md), [\<strstream>](strstream.md)|
|Iterators|[\<iterator>](iterator.md)|
|Localización|[\<codecvt>](codecvt.md), [\<cvt/wbuffer>](cvt-wbuffer.md), [\<cvt/wstring>](cvt-wstring.md), [\<locale>](locale.md)|
|Matemáticas y valores numéricos|[\<complex>](complex.md), [\<limits>](limits.md), [\<numeric>](numeric.md), [\<random>](random.md), [\<ratio>](ratio.md), [\<valarray>](valarray.md)|
|[Administración de memoria](../cpp/smart-pointers-modern-cpp.md)|[\<allocators>](allocators-header.md), [\<memory>](memory.md), [\<new>](new.md), [\<scoped_allocator>](scoped-allocator.md)|
|Subprocesamiento múltiple|[\<atomic>](atomic.md), [\<condition_variable>](condition-variable.md), [\<future>](future.md), [\<mutex>](mutex.md), [\<shared_mutex>](shared-mutex.md), [\<thread>](thread.md)|
|Otras utilidades|[\<bitset>](bitset.md), [\<chrono>](chrono.md), [\<functional>](functional.md), [\<initializer_list>](initializer-list.md), [\<tuple>](tuple.md), [\<type_traits>](type-traits.md), [\<typeinfo>](typeinfo.md), [\<typeindex>](typeindex.md), [\<utility>](utility.md)|
|Cadenas y datos de caracteres|[\<regex>](regex.md), [\<string>](string.md), [\<string_view>](string-view.md)

::: moniker-end

## <a name="see-also"></a>Vea también

[Usar encabezados de la biblioteca de C++](using-cpp-library-headers.md)\
[Biblioteca estándar de C++](cpp-standard-library-reference.md)
