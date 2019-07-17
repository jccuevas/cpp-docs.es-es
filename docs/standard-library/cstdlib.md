---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 70e05ad734fa49ba8cb96e4bf83bc05b99c5f55c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246528"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

Incluye el encabezado de la biblioteca estándar de C \<stdlib.h > y agrega los nombres asociados a la `std` espacio de nombres. Incluir este encabezado también garantiza que los nombres declarados mediante vinculación externa en el encabezado de la biblioteca estándar de C se declaran en el `std` espacio de nombres.

> [!NOTE]
> \<STDLIB.h > no incluye el tipo **wchar_t**.

## <a name="requirements"></a>Requisitos

**Encabezado**: \<cstdlib >

**Espacio de nombres:** std

## <a name="namespace-and-macros"></a>Macros y Namespace

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

## <a name="exposition-only-functions"></a>Solo las funciones de exposición

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>Funciones de inicio y finalización

|Función|DESCRIPCIÓN|
|-|-|
|[_Exit](#_exit)|Finaliza el programa sin usar destructores o funciones registradas.|
|[abort](#abort)|Finaliza el programa sin usar destructores.|
|[atexit](#atexit)|Registra la función de finalización del programa.|
|[exit](#exit)|Destruye los objetos con subproceso y almacenamiento estático, a continuación, devuelve el control.|
|[at_quick_exit](#at_quick_exit)|Registra la función sin argumentos para la finalización del programa.|
|[quick_exit](#quick_exit)|Registra la función con objetos conservados para la finalización del programa.|
|[getenv](#getenv)|Consulte la referencia de la biblioteca estándar de C.|
|[system](#system)|Consulte la referencia de la biblioteca estándar de C.|

### <a name="_exit"></a> _Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>Comentarios

El programa finaliza sin ejecutar los destructores para objetos de automático, el subproceso o la duración de almacenamiento estática y sin llamar a funciones que pasan a `atexit()`. La función `_Exit` tiene seguridad de la señal.

### <a name="abort"></a> Anulación

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>Comentarios

El programa finaliza sin ejecutar los destructores para objetos de automático, el subproceso o la duración de almacenamiento estática y sin llamar a funciones que pasan a `atexit()`. La función `abort` tiene seguridad de la señal.

### <a name="at_quick_exit"></a> at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>Valor devuelto

Cero si el registro es satisfactorio, distinto de cero si se produce un error.

#### <a name="remarks"></a>Comentarios

El `at_quick_exit()` funciones registran la función señalada por *func* llamarse sin argumentos cuando `quick_exit` se llama. No se especifica si una llamada a `at_quick_exit()` que no se producen antes de todas las llamadas a `quick_exit` se realizará correctamente y el `at_quick_exit()` funciones no introducen una anticipación de datos. El orden del registro puede ser indeterminado si `at_quick_exit` desde más de un subproceso y, puesto que se llamó `at_quick_exit` son distintos de los registros de la `atexit` registros, las aplicaciones pueden necesitar llamar a ambas funciones de registro con el argumento de la mismo. La implementación debe admitir el registro de al menos 32 funciones.

### <a name="atexit"></a> atexit

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>Comentarios

El `atexit()` funciones registran la función señalada por *func* llamarse sin argumentos en la finalización normal del programa. No se especifica si una llamada a `atexit()` que no se producen antes de llamar a `exit()` se realizará correctamente y el `atexit()` funciones no introducen una anticipación de datos. La implementación debe admitir el registro de al menos 32 funciones.

#### <a name="return-value"></a>Valor devuelto

Devuelve cero si el registro es satisfactorio, distinto de cero si se produce un error.

### <a name="exit"></a> salir

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>Comentarios

En primer lugar, los objetos que tienen duración de almacenamiento thread y asociados con el actual subproceso se destruyen.

A continuación, se destruyen objetos con una duración de almacenamiento estática y funciones registrado mediante una llamada a `atexit` se denominan. No se destruyen objetos automáticos como resultado de llamar a `exit()`. Si el control abandona una función registrada llamada `exit` porque la función no proporciona un controlador de excepción producida, `std::terminate()` se denominará. Se llama a una función para cada vez se registra. Todos los objetos con una duración de almacenamiento automática se destruyen en un programa cuya función principal no contiene ningún objeto automática y ejecuta la llamada a `exit()`. Puede transferir el control directamente a esa función principal iniciando una excepción que se detecta en main.

A continuación, todos los abiertos secuencias de C (como mediada por las firmas de función declaradas en <cstdio>) con datos almacenados en búfer tácitas son vaciado, todos los abiertos se cierran las secuencias de C y todos los archivos se crean mediante una llamada `tmpfile()` se quitan.

Por último, el control se devuelve al entorno de host. Si el estado es cero o EXIT_SUCCESS, se devuelve un formulario definido por la implementación de la finalización correcta de estado. Si el estado es EXIT_FAILURE, se devuelve un formulario definido por la implementación de la terminación de estado incorrecto. En caso contrario, el estado devuelto es definido por la implementación.

### <a name="getenv"></a> getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a> quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>Comentarios

Las funciones registran por llamadas a `at_quick_exit` se llaman en orden inverso de su registro, excepto en que se llama a una función después de que cualquiera registrado previamente las funciones que ya se había llamadas en el momento en que se registró. No se destruirán los objetos como resultado de llamar a `quick_exit`. Si el control abandona una función registrada llamada `quick_exit` porque la función no proporciona un controlador de excepción producida, `std::terminate()` se denominará. Una función registrada a través de `at_quick_exit` invocada por el subproceso que llama `quick_exit`, que puede ser un subproceso diferente de lo que lo registró, registrados por lo que las funciones no debe confiar en la identidad de objetos con una duración de almacenamiento de subproceso. Después de llamar a funciones registradas, `quick_exit` recurrirá a `_Exit(status)`. No se vacían los búferes de archivos estándar. La función `quick_exit` tiene seguridad de señal cuando las funciones que se registra con `at_quick_exit` son.

### <a name="system"></a> Sistema

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

Estas funciones tienen la semántica especificada en la biblioteca de C estándar.

##  <a name="multibyte--wide-string-and-character-conversion-functions"></a>Cadena multibyte y ancho y funciones de conversión de caracteres

```cpp
int mblen(const char* s, size_t n);
int mbtowc(wchar_t* pwc, const char* s, size_t n);
int wctomb(char* s, wchar_t wchar);
size_t mbstowcs(wchar_t* pwcs, const char* s, size_t n);
size_t wcstombs(char* s, const wchar_t* pwcs, size_t n);
```

### <a name="remarks"></a>Comentarios

Estas funciones tienen la semántica especificada en la biblioteca de C estándar.

## <a name="algorithm-functions"></a>Funciones de algoritmo

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

### <a name="remarks"></a>Comentarios

Estas funciones tienen la semántica especificada en la biblioteca de C estándar.

## <a name="low-quality-random-number-generation-functions"></a>Funciones de generación de números aleatorios de baja calidad

```cpp
int rand();
void srand(unsigned int seed);
```

### <a name="remarks"></a>Comentarios

Estas funciones tienen la semántica especificada en la biblioteca de C estándar.

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

Estas funciones tienen la semántica especificada en la biblioteca de C estándar.

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

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
