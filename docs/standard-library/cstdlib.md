---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 298d6a512b2863a326bda0670f33fe8f1bda0688
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449407"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

Incluye el encabezado \<stdlib. > h de la biblioteca estándar de C y agrega los nombres `std` asociados al espacio de nombres. Incluir este encabezado garantiza que los nombres declarados mediante vinculación externa en el encabezado de la biblioteca estándar `std` de C se declaran en el espacio de nombres.

> [!NOTE]
> \<stdlib. h > no incluye el tipo **wchar_t**.

## <a name="requirements"></a>Requisitos

**Encabezado**: \<cstdlib >

**Espacio de nombres:** std

## <a name="namespace-and-macros"></a>Espacio de nombres y macros

```cpp
namespace std {
    using size_t = see definition;
    using div_t = see definition;
    using ldiv_t = see definition;
    using lldiv_t = see definition;
}

#define NULL
#define EXIT_FAILURE
#define EXIT_SUCCESS
#define RAND_MAX
#define MB_CUR_MAX
```

## <a name="exposition-only-functions"></a>Funciones de solo exposición

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>Funciones de inicio y finalización

|Función|DESCRIPCIÓN|
|-|-|
|[_Exit](#_exit)|Finaliza el programa sin usar destructores ni funciones registradas.|
|[abort](#abort)|Finaliza el programa sin usar destructores.|
|[atexit](#atexit)|Registra la función para la finalización del programa.|
|[exit](#exit)|Destruye objetos con el almacenamiento estático y el subproceso y, a continuación, devuelve el control.|
|[at_quick_exit](#at_quick_exit)|Registra la función sin argumentos para la finalización del programa.|
|[quick_exit](#quick_exit)|Registra la función con objetos conservados para la finalización del programa.|
|[getenv](#getenv)|Consulte referencia de la biblioteca estándar de C.|
|[system](#system)|Consulte referencia de la biblioteca estándar de C.|

### <a name="_exit"></a>_Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>Comentarios

El programa finaliza sin ejecutar destructores para los objetos de duración de almacenamiento automático, de subproceso o estático y sin llamar a las funciones `atexit()`que se pasan a. La función `_Exit` es segura para señales.

### <a name="abort"></a>aborta

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>Comentarios

El programa finaliza sin ejecutar destructores para los objetos de duración de almacenamiento automático, de subproceso o estático y sin llamar a las funciones `atexit()`que se pasan a. La función `abort` es segura para señales.

### <a name="at_quick_exit"></a>at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>Valor devuelto

Cero si el registro se realiza correctamente, distinto de cero si se produce un error.

#### <a name="remarks"></a>Comentarios

Las `at_quick_exit()` funciones registran la función a la que apunta *FUNC* para que se llame `quick_exit` sin argumentos cuando se llama a. No se especifica si una llamada a `at_quick_exit()` no se produce antes de que todas las llamadas a `quick_exit` se realicen correctamente y que las `at_quick_exit()` funciones no presenten una carrera de datos. El orden de registro puede ser indeterminado `at_quick_exit` si se llamó desde más de un subproceso `at_quick_exit` y, dado que los registros `atexit` son distintos de los registros, es posible que las aplicaciones necesiten llamar a ambas funciones de registro con el mismo argumento. La implementación de debe admitir el registro de al menos 32 funciones.

### <a name="atexit"></a>AtExit

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>Comentarios

Las `atexit()` funciones registran la función a la que apunta *FUNC* para que se llame sin argumentos en la finalización del programa normal. No se especifica si una llamada a `atexit()` no se produce antes de que una llamada a `exit()` se realice correctamente `atexit()` y las funciones no presenten una carrera de datos. La implementación de debe admitir el registro de al menos 32 funciones.

#### <a name="return-value"></a>Valor devuelto

Devuelve cero si el registro se realiza correctamente y es distinto de cero si se produce un error.

### <a name="exit"></a>abandonar

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>Comentarios

En primer lugar, se destruyen los objetos con duración de almacenamiento de subprocesos y asociados al subproceso actual.

A continuación, se destruyen los objetos con duración de almacenamiento estática y `atexit` se llama a las funciones registradas mediante una llamada a. Los objetos automáticos no se destruyen como `exit()`resultado de una llamada a. Si el control deja una función registrada a `exit` la que llama porque la función no proporciona un controlador para una `std::terminate()` excepción iniciada, se llamará a. Se llama a una función cada vez que se registra. Los objetos con la duración de almacenamiento automática se destruyen en un programa cuya función Main no contiene ningún objeto automático y ejecuta `exit()`la llamada a. El control se puede transferir directamente a esta función principal iniciando una excepción que se detecta en Main.

A continuación, se vacían todas las secuencias de c abiertas (como las correcciones <cstdio>de las firmas de función declaradas en) con datos almacenados en búfer no escritos, se cierran todas las secuencias `tmpfile()` de c abiertas y se quitan todos los archivos creados mediante una llamada.

Por último, se devuelve el control al entorno de host. Si status es cero o EXIT_SUCCESS, se devuelve un formulario definido por la implementación de la finalización correcta de status. Si el estado es EXIT_FAILURE, se devuelve un formulario definido por la implementación de la terminación de estado incorrecto. De lo contrario, el estado devuelto es definido por la implementación.

### <a name="getenv"></a>getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a>quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>Comentarios

Las funciones registradas por `at_quick_exit` las llamadas a se llaman en el orden inverso a su registro, con la excepción de que se llamará a una función después de las funciones registradas previamente que ya se hayan llamado en el momento en que se registró. Los objetos no se destruirán como resultado de llamar `quick_exit`a. Si el control deja una función registrada a `quick_exit` la que llama porque la función no proporciona un controlador para una `std::terminate()` excepción iniciada, se llamará a. Una función registrada mediante `at_quick_exit` se invoca mediante el subproceso que llama `quick_exit`a, que puede ser un subproceso diferente al que lo registró, por lo que las funciones registradas no deben confiar en la identidad de los objetos con duración de almacenamiento de subprocesos. Después de llamar a las `quick_exit` funciones registradas, debe llamar a. `_Exit(status)` No se vacían los búferes de archivo estándar. La función `quick_exit` es segura para señales cuando las funciones registradas `at_quick_exit` con son.

### <a name="system"></a>integrado

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>Funciones de asignación de memoria

```cpp
void* aligned_alloc(size_t alignment, size_t size);
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
double atof(const char* nptr);
int atoi(const char* nptr);
long int atol(const char* nptr);
long long int atoll(const char* nptr);
double strtod(const char* nptr, char** endptr);
float strtof(const char* nptr, char** endptr);
long double strtold(const char* nptr, char** endptr);
long int strtol(const char* nptr, char** endptr, int base);
long long int strtoll(const char* nptr, char** endptr, int base);
unsigned long int strtoul(const char* nptr, char** endptr, int base);
unsigned long long int strtoull(const char* nptr, char** endptr, int base);
```

#### <a name="remarks"></a>Comentarios

Estas funciones tienen la semántica especificada en la biblioteca estándar de C.

##  <a name="multibyte--wide-string-and-character-conversion-functions"></a>Funciones de conversión de caracteres y cadenas multibyte/ancho

```cpp
int mblen(const char* s, size_t n);
int mbtowc(wchar_t* pwc, const char* s, size_t n);
int wctomb(char* s, wchar_t wchar);
size_t mbstowcs(wchar_t* pwcs, const char* s, size_t n);
size_t wcstombs(char* s, const wchar_t* pwcs, size_t n);
```

### <a name="remarks"></a>Comentarios

Estas funciones tienen la semántica especificada en la biblioteca estándar de C.

## <a name="algorithm-functions"></a>Funciones de algoritmo

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

### <a name="remarks"></a>Comentarios

Estas funciones tienen la semántica especificada en la biblioteca estándar de C.

## <a name="low-quality-random-number-generation-functions"></a>Funciones de generación de números aleatorios de baja calidad

```cpp
int rand();
void srand(unsigned int seed);
```

### <a name="remarks"></a>Comentarios

Estas funciones tienen la semántica especificada en la biblioteca estándar de C.

## <a name="absolute-values"></a>Valores absolutos

```cpp
int abs(int j);
long int abs(long int j);
long long int abs(long long int j);
float abs(float j);
double abs(double j);
long double abs(long double j);
long int labs(long int j);
long long int llabs(long long int j);
div_t div(int numer, int denom);
ldiv_t div(long int numer, long int denom);
lldiv_t div(long long int numer, long long int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
```

### <a name="remarks"></a>Comentarios

Estas funciones tienen la semántica especificada en la biblioteca estándar de C.

## <a name="functions"></a>Funciones

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size,
c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size,
compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
