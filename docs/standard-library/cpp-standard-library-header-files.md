---
title: C++archivos de encabezado de la biblioteca estándar
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: 807e65c69e55d8790b77a493e4ae1878aa740557
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305415"
---
# <a name="c-standard-library-header-files"></a>C++archivos de encabezado de la biblioteca estándar

Archivos de encabezado de C++ la biblioteca estándar y extensiones, por categoría.

## <a name="headers-by-category"></a>Encabezados por categoría

::: moniker range=">=vs-2017"

| Categoría | Encabezados |
| - | - |
| [Algoritmos](../cpp/algorithms-modern-cpp.md) | [\<algoritmo >](algorithm.md), [\<cstdlib >](cstdlib.md) [\<Numeric >](numeric.md) |
| Operaciones atómicas |  [\<atomic >](atomic.md)<sup>11</sup> |
| Contenedores de la biblioteca de C | [\<cassert >](cassert.md), [\<ccomplex >](ccomplex.md)<sup>11 a b</sup>, [\<cctype >](cctype.md), [\<cerrno >](cerrno.md), [\<cfenv >](cfenv.md)<sup>11</sup>, [\<cfloat >](cfloat.md), [\<cinttypes >](cinttypes.md)<sup>11</sup>, [\<ciso646 >](ciso646.md)<sup>b</sup>, [\<climits](climits.md)>, [\<clocale >](clocale.md), [\<CMATH >](cmath.md),\<[csetjmp >](csetjmp.md), [\<csignal >](csignal.md), [\<cstdalign >](cstdalign.md)<sup>11 a b</sup>, [\<cstdarg >](cstdarg.md), [\<cstdbool >](cstdbool.md)<sup>11 a b</sup>, [\<cstddef >](cstddef.md), [\<cstdint >](cstdint.md)<sup>11</sup>, [\<cstdio >](cstdio.md), [\<cstdlib >](cstdlib.md), [\<CString >](cstring.md), [\<ctgmath >](ctgmath.md)<sup>11 a b</sup>, [\<ctime >](ctime.md), [\<cuchar >](cuchar.md)<sup>11</sup> , [\<cwchar >](cwchar.md), [\<cwctype >](cwctype.md) |
| Conceptos | conceptos de \<><sup>20</sup> |
| [Contenedores](../cpp/containers-modern-cpp.md) | |
| Contenedores de secuencias | [\<array >](array.md)<sup>11</sup>, [\<deque >](deque.md), [\<forward_list](forward-list.md)><sup>11</sup>, [\<list >](list.md),\<[Vector >](vector.md) |
| Contenedores asociativos ordenados| [\<map>](map.md), [\<set>](set.md) |
| Contenedores asociativos desordenados | [\<unordered_map >](unordered-map.md)<sup>11</sup>, [\<unordered_set >](unordered-set.md)<sup>11</sup> |
| Adaptadores de contenedor | [\<queue>](queue.md), [\<stack>](stack.md) |
| Vistas de contenedor | \<intervalo ><sup>20</sup> |
| [Errores y control de excepciones](../cpp/errors-and-exception-handling-modern-cpp.md) | [\<cassert >](cassert.md), [\<excepción >](exception.md), [\<stdexcept >](stdexcept.md), [\<system_error >](system-error.md)<sup>11</sup> |
| Utilidades generales | \<cualquier ><sup>17</sup>, [\<BitSet >](bitset.md), \<charconv ><sup>17</sup>, [\<cstdlib >](cstdlib.md), \<de ejecución<sup>> 17</sup>,\<[funcional >](functional.md),\<de [memoria](memory.md)>, \<memory_resource ><sup>17</sup>, \<opcional ><sup>17</sup>,\<[ratio >](ratio.md)<sup>11</sup>, [\<scoped_allocator](scoped-allocator.md)><sup>11</sup>, [\<tupla >](tuple.md)<sup>11</sup>, [\<type_traits >](type-traits.md)<sup>11</sup>, [\<typeindex >](typeindex.md)<sup>11</sup>, [\<Utility >](utility.md), \<Variant ><sup>17</sup> |
| [E/s y formato](../text/string-and-i-o-formatting-modern-cpp.md) | [\<cinttypes >](cinttypes.md)<sup>11</sup>, [\<cstdio >](cstdio.md), [\<filesystem >](filesystem.md)<sup>17</sup>, [\<fstream >](fstream.md), [\<iomanip >](iomanip.md), [\<ios >](ios.md), [\<iosfwd >](iosfwd.md), [\<iostream >](iostream.md), [\<IStream >](istream.md), [\<ostream >](ostream.md), [\<sstream >](sstream.md), [\<streambuf >](streambuf.md),\<[strstream >](strstream.md)<sup>c </sup>, \<syncstream ><sup>20</sup> |
| Iteradores | [\<iterator>](iterator.md) |
| Compatibilidad con lenguajes | [\<cfloat >](cfloat.md), [\<climits >](climits.md), [\<codecvt >](codecvt.md)<sup>11 a</sup>, \<Compare ><sup>20</sup>, \<contrato ><sup>20</sup>, \<corutina ><sup>20</sup>, [\<csetjmp >](csetjmp.md), [\<csignal >](csignal.md), [\<cstdarg >](cstdarg.md), [\<cstddef >](cstddef.md), [\<cstdint >](cstdint.md)<sup>11</sup>,\<[cstdlib >](cstdlib.md),\<[excepción](exception.md) > , [\<initializer_list >](initializer-list.md)<sup>11</sup>, [\<limita >](limits.md), [\<nuevo >](new.md), [\<TypeInfo >](typeinfo.md), \<versión ><sup>20</sup> |
| Localización | [\<clocale >](clocale.md), [\<codecvt >](codecvt.md)<sup>11 a</sup>, [\<CVT/wbuffer >](cvt-wbuffer.md), [\<CVT/wstring >](cvt-wstring.md),\<[configuración regional >](locale.md) |
| Matemáticas y valores numéricos | \<bit ><sup>20</sup>, [\<cfenv >](cfenv.md)<sup>11</sup>, [\<CMATH >](cmath.md), [\<Complex >](complex.md), [\<cstdlib >](cstdlib.md), [\<limits >](limits.md), [\<Numeric >](numeric.md), [\<Random >](random.md)<sup>11</sup>, [\<ratio >](ratio.md)<sup>11</sup>, [\<valarray >](valarray.md) |
| [Administración de memoria](../cpp/smart-pointers-modern-cpp.md) | [\<asignadores >](allocators-header.md), [\<memoria >](memory.md), \<memory_resource ><sup>17</sup>, [\<nueva >](new.md), [\<](scoped-allocator.md)scoped_allocator ><sup>11</sup> |
| Multithreading | [\<atomic >](atomic.md)<sup>11</sup>, [\<condition_variable >](condition-variable.md)<sup>11</sup>, [\<futuro >](future.md)<sup>11</sup>, [\<mutex >](mutex.md)<sup>11</sup>, [\<](shared-mutex.md)shared_mutex ><sup>14</sup>, [\<subproceso >](thread.md)<sup>11</sup> |
| Intervalos | intervalos de \<><sup>20</sup> |
| Expresiones regulares | [\<regex >](regex.md)<sup>11</sup> |
| Cadenas y datos de caracteres | [\<cctype >](cctype.md), [\<cstdlib >](cstdlib.md), [\<cstring >](cstring.md), [\<cuchar >](cuchar.md)<sup>11</sup>, [\<cwchar >](cwchar.md), [\<cwctype >](cwctype.md), [\<regex >](regex.md)<sup>11</sup>, [\<cadena >](string.md), [\<string_view >](string-view.md)<sup>17</sup> |
| Tiempo | [\<crónico >](chrono.md)<sup>11</sup>, [\<ctime >](ctime.md) |

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
|[Contenedores](../cpp/containers-modern-cpp.md)||
|Contenedores de secuencias|[\<array >](array.md), [\<deque >](deque.md), [\<forward_list >](forward-list.md), [\<list >](list.md),\<[Vector >](vector.md)|
|Contenedores asociativos ordenados| [\<map>](map.md), [\<set>](set.md)|
|Contenedores asociativos desordenados|[\<unordered_map >](unordered-map.md), [\<unordered_set](unordered-set.md) >|
|Contenedores de adaptador|[\<queue>](queue.md), [\<stack>](stack.md)|
|[Errores y control de excepciones](../cpp/errors-and-exception-handling-modern-cpp.md)|[\<> de excepción](exception.md), [\<stdexcept >](stdexcept.md) [,\<system_error >](system-error.md)|
|[E/s y formato](../text/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md), [\<fstream>](fstream.md), [\<iomanip>](iomanip.md), [\<ios>](ios.md), [\<iosfwd>](iosfwd.md), [\<iostream>](iostream.md), [\<istream>](istream.md), [\<ostream>](ostream.md), [\<sstream>](sstream.md), [\<streambuf>](streambuf.md), [\<strstream>](strstream.md)|
|Iteradores|[\<iterator>](iterator.md)|
|Localización|[\<codecvt>](codecvt.md), [\<cvt/wbuffer>](cvt-wbuffer.md), [\<cvt/wstring>](cvt-wstring.md), [\<locale>](locale.md)|
|Matemáticas y valores numéricos|[\<complex>](complex.md), [\<limits>](limits.md), [\<numeric>](numeric.md), [\<random>](random.md), [\<ratio>](ratio.md), [\<valarray>](valarray.md)|
|[Administración de memoria](../cpp/smart-pointers-modern-cpp.md)|[\<asignadores >](allocators-header.md), [\<> de memoria](memory.md), [\<New >](new.md), [\<scoped_allocator >](scoped-allocator.md)|
|Multithreading|[\<atomic >](atomic.md), [\<condition_variable >](condition-variable.md), [\<> futura](future.md), [\<mutex >](mutex.md), [\<shared_mutex >](shared-mutex.md)\<[subproceso >](thread.md)|
|Otras utilidades|[\<bitset >](bitset.md), [\<crónico >](chrono.md), [\<funcional >](functional.md), [\<](initializer-list.md)initializer_list >, [\<tupla >](tuple.md), [\<](type-traits.md)type_traits >, [\<TypeInfo >](typeinfo.md), [\<typeindex >](typeindex.md),\<[utilidad](utility.md) >|
|Cadenas y datos de caracteres|[\<regex >](regex.md), [\<cadena >](string.md), [\<](string-view.md) string_view >

::: moniker-end

## <a name="see-also"></a>Vea también

[Usar C++ encabezados de biblioteca](using-cpp-library-headers.md)\
[C++biblioteca estándar](cpp-standard-library-reference.md)
