---
title: C++archivos de encabezado de la biblioteca estándar
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: dc337ef078108d86849aa7b7452512dfb69e6e18
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341125"
---
# <a name="c-standard-library-header-files"></a>C++archivos de encabezado de la biblioteca estándar

Archivos de encabezado de C++ la biblioteca estándar y extensiones, por categoría.

## <a name="headers-by-category"></a>Encabezados por categoría

::: moniker range=">=vs-2017"

| Categoría | Encabezados |
| - | - |
| [Algoritmos](../cpp/algorithms-modern-cpp.md) | algoritmo > [, >cstdlib\<](cstdlib.md), [ >\<numéricos](numeric.md) [ \<](algorithm.md) |
| Operaciones atómicas |  Atomic ><sup>11</sup> [ \<](atomic.md) |
| Contenedores de la biblioteca de C | [ \<](cfenv.md)<sup></sup> [ \<](cerrno.md) [ \<cassert >](cctype.md), [ccomplex > 11 a b, cctype >, cerrno >, cfenv > 11, \<](ccomplex.md) [ \<](cassert.md)<sup></sup> [ \<cfloat >](cfloat.md),<sup></sup> [ \<cinttypes >](cinttypes.md)11, [ \<ciso646 >](ciso646.md)<sup>b</sup>, [ \<climits >](climits.md), [ \<clocale >](clocale.md), [ CMATH\<>](cmath.md), [ csetjmp>,csignal>,cstdalign>11ab,cstdarg>,\<](csetjmp.md) [ \<](cstdarg.md) [ \<](csignal.md) [ \<](cstdalign.md)<sup></sup> [ \<cstdbool >](cstdbool.md)<sup>11 a b</sup>, [ \<cstddef >](cstddef.md), [ \<cstdint >](cstdint.md)<sup>11</sup>, [ \<cstdio >](cstdio.md), [ \<cstdlib >](cstdlib.md), [ >\<CString](cstring.md),<sup></sup> [ \<](ctime.md)<sup></sup> [ \<](cuchar.md) [ \<](cwchar.md) [ ctgmath>11\<](ctgmath.md)a b, ctime >, cuchar > 11, cwchar >, [ >\<cwctype](cwctype.md) |
| Conceptos | \<conceptos ><sup>20</sup> |
| [Contenedores](../cpp/containers-modern-cpp.md) | |
| Contenedores de secuencias | <sup></sup><sup></sup> [ array\<>](array.md)11, [ deque>,forward_list>11,list>,Vector>\<](deque.md) [ \<](forward-list.md) [ \<](list.md) [ \<](vector.md) |
| Contenedores asociativos ordenados| [\<map>](map.md), [\<set>](set.md) |
| Contenedores asociativos desordenados | unordered_map ><sup>11</sup>, [ unordered_set>\<](unordered-set.md)<sup>11</sup> [ \<](unordered-map.md) |
| Adaptadores de contenedor | [\<queue>](queue.md), [\<stack>](stack.md) |
| Vistas de contenedor | \<intervalo ><sup>20</sup> |
| [Errores y control de excepciones](../cpp/errors-and-exception-handling-modern-cpp.md) | [ \<](system-error.md)<sup></sup> [ cassert>\<](stdexcept.md), [> de excepciones, > de stdexcept, system_error > 11 \<](exception.md) [ \<](cassert.md) |
| Utilidades generales | \<cualquier ><sup>17</sup>, [ \<BitSet >](bitset.md), \<charconv ><sup>17</sup>, [ \<cstdlib >](cstdlib.md), \<ejecución ><sup>17</sup>, [ \<> funcional](functional.md), [ memoria\<>](memory.md), \< [ \<](ratio.md)<sup></sup><sup></sup><sup></sup>memory_resource > 17, > opcional 17, ratio > 11, scoped_allocator > \< [ \< ](scoped-allocator.md) <sup>11</sup>,<sup></sup><sup></sup><sup></sup> [ tupla\<>](tuple.md)11, [ type_traits>11,typeindex>11,utilidad>,\<](type-traits.md) [ \<](typeindex.md) [ \<](utility.md) \<variante ><sup>17</sup> |
| [E/s y formato](../cpp/string-and-i-o-formatting-modern-cpp.md) | <sup></sup><sup></sup> [ cinttypes\<>](cinttypes.md)11, [ cstdio>,filesystem>17,FStream>,iomanip>\<](cstdio.md) [ \<](filesystem.md) [ \<](fstream.md) [ \<](iomanip.md) [ iOS\<>](ios.md), [ iosfwd>,iostream>,IStream>,ostream>,sstream>\<](iosfwd.md) [ \<](iostream.md) [ \<](istream.md) [ \<](ostream.md) [ \<](sstream.md) \< [ ,\<streambuf >](streambuf.md) [ ,\<strstream >](strstream.md)<sup>c</sup>, syncstream ><sup>20</sup> |
| Iterators | [\<iterator>](iterator.md) |
| Compatibilidad con idiomas | \< \< \< <sup></sup><sup></sup><sup></sup> [ cfloat\<>](cfloat.md) [, climits\<>](climits.md) [, codecvt\<>](codecvt.md)11 a, compare > 20, contrato > 20, corrutina ><sup>20</sup>, [ \<csetjmp >](csetjmp.md), [ \<csignal >](csignal.md), [ \<cstdarg >](cstdarg.md), [ \<cstddef >](cstddef.md), [ \<cstdint > ](cstdint.md) <sup>11</sup><sup></sup> [, cstdlib\<>](cstdlib.md) [, Exception\<>](exception.md) [, initializer_list\<>](initializer-list.md)11 [, limits>,\<](limits.md) [ \< New >](new.md), [ \<TypeInfo >](typeinfo.md), \<version ><sup>20</sup> |
| Localización | [ \<](locale.md) <sup></sup> [ clocale>\<](cvt-wbuffer.md), [codecvt > 11 a, CVT/wbuffer >, CVT/wstring >, configuración regional > \<](codecvt.md) [ \<](cvt-wstring.md) [ \<](clocale.md) |
| Matemáticas y valores numéricos | \<bit ><sup>20</sup>, [ \<cfenv >](cfenv.md)<sup>11</sup>, [ \<> CMATH](cmath.md), [ \<> complejos](complex.md), [ \<cstdlib >](cstdlib.md), [ \<limits >](limits.md), [ >\<](numeric.md)numéricas [ ,\<>s aleatorios](random.md)<sup>11</sup>, [ \<ratio >](ratio.md)<sup>11</sup>, [ \<valarray >](valarray.md) |
| [Administración de memoria](../cpp/smart-pointers-modern-cpp.md) | \< [ \<](memory.md)<sup></sup><sup></sup> [ \<](new.md) [ \<](scoped-allocator.md) [ allocadores>,Memory>,memory_resource>17,\<](allocators-header.md)New >, scoped_allocator > 11 |
| Multithreading | <sup></sup><sup></sup><sup></sup><sup></sup> [ Atomic\<>](atomic.md)11, [ condition_variable>11,Future>11,mutex>11,\<](condition-variable.md) [ \<](mutex.md) [ \<](future.md) [ \< shared_mutex >](shared-mutex.md)<sup>14</sup>, [ \<subproceso >](thread.md)<sup>11</sup> |
| Intervalos | \<intervalos ><sup>20</sup> |
| Expresiones regulares | regex ><sup>11</sup> [ \<](regex.md) |
| Cadenas y datos de caracteres | <sup></sup> [ cctype\<>](cctype.md), [ cstdlib>,CString>,cuchar>11,cwchar>,cwctype\<](cstdlib.md) [ \<](cstring.md) [ \<](cuchar.md) [ \<](cwchar.md) [ \< >](cwctype.md) [ ,\<regex >](regex.md)<sup>11</sup>, [ \<cadena >](string.md), [ \<string_view >](string-view.md)<sup>17</sup> |
| Hora | crónico ><sup>11</sup>, [ ctime\<>](ctime.md) [ \<](chrono.md) |

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
|Contenedores de secuencias|[ array\<>](array.md), [ deque>,forward_list>,list>,Vector>\<](deque.md) [ \<](forward-list.md) [ \<](list.md) [ \<](vector.md)|
|Contenedores asociativos ordenados| [\<map>](map.md), [\<set>](set.md)|
|Contenedores asociativos desordenados|unordered_map >, [ \<](unordered-map.md) [ unordered_set>\<](unordered-set.md)|
|Contenedores de adaptador|[\<queue>](queue.md), [\<stack>](stack.md)|
|[Errores y control de excepciones](../cpp/errors-and-exception-handling-modern-cpp.md)|> de excepción, [ \<stdexcept >](stdexcept.md), [ \<system_error >](system-error.md) [ \<](exception.md)|
|[E/s y formato](../cpp/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md), [\<fstream>](fstream.md), [\<iomanip>](iomanip.md), [\<ios>](ios.md), [\<iosfwd>](iosfwd.md), [\<iostream>](iostream.md), [\<istream>](istream.md), [\<ostream>](ostream.md), [\<sstream>](sstream.md), [\<streambuf>](streambuf.md), [\<strstream>](strstream.md)|
|Iterators|[\<iterator>](iterator.md)|
|Localización|[\<codecvt>](codecvt.md), [\<cvt/wbuffer>](cvt-wbuffer.md), [\<cvt/wstring>](cvt-wstring.md), [\<locale>](locale.md)|
|Matemáticas y valores numéricos|[\<complex>](complex.md), [\<limits>](limits.md), [\<numeric>](numeric.md), [\<random>](random.md), [\<ratio>](ratio.md), [\<valarray>](valarray.md)|
|[Administración de memoria](../cpp/smart-pointers-modern-cpp.md)|asignadores >, [ \<> de memoria](memory.md), [ \<nuevo >](new.md), [ \<scoped_allocator >](scoped-allocator.md) [ \<](allocators-header.md)|
|Multithreading|[ Atomic>\<](mutex.md), [ condition_variable\<>](condition-variable.md), [ \<Future >](future.md), mutex > [ ,\<shared_mutex >](shared-mutex.md), Thread [ \<](atomic.md) [ \< >](thread.md)|
|Otras utilidades|[ BitSet\<>](bitset.md), [ crónico>,Functional>,initializer_list>,Tuple>,type_traits\<](chrono.md) [ \<](functional.md) [ \<](initializer-list.md) [ \<](tuple.md) [ \< >](type-traits.md) [ ,\<TypeInfo >](typeinfo.md), [ \<typeindex >](typeindex.md), [ \<Utility >](utility.md)|
|Cadenas y datos de caracteres|[\<regex>](regex.md), [\<string>](string.md), [\<string_view>](string-view.md)

::: moniker-end

## <a name="see-also"></a>Vea también

[Usar C++ encabezados de biblioteca](using-cpp-library-headers.md)\
[C++biblioteca estándar](cpp-standard-library-reference.md)
