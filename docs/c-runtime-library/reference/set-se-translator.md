---
title: _set_se_translator
ms.date: 02/21/2018
api_name:
- _set_se_translator
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_se_translator
- set_se_translator
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
ms.openlocfilehash: 781deaad091b6aed72350100f7575c566bbae793
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948393"
---
# <a name="_set_se_translator"></a>_set_se_translator

Establezca una función de devolución de llamada por subproceso para traducir excepciones Win32 (excepciones estructuradas de C) en C++ excepciones con tipo.

## <a name="syntax"></a>Sintaxis

```cpp
_se_translator_function _set_se_translator(
    _se_translator_function seTransFunction
);
```

### <a name="parameters"></a>Parámetros

*seTransFunction*<br/>
Puntero a una función de traductor de excepciones estructuradas de C que se escriba.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la función de traductor anterior registrada por _ **set_se_translator**, de modo que la función anterior se puede restaurar más adelante. Si no se ha establecido ninguna función anterior, el valor devuelto se puede utilizar para restaurar el comportamiento predeterminado; Este valor puede ser **nullptr**.

## <a name="remarks"></a>Comentarios

La función _ **set_se_translator** proporciona una manera de controlar las excepciones Win32 (excepciones estructuradas C++ de C) como excepciones con tipo. Para permitir que cada excepción de C se controle C++ mediante un controlador **catch** , primero defina una clase contenedora de excepciones de c que se pueda usar, o derive de, para atribuir un tipo de clase específico a una excepción de c. Para usar esta clase, instale una función de traductor de excepciones de C a la que llama el mecanismo de control de excepciones internas cada vez que se produce una excepción de C. Dentro de la función de traductor, puede producir cualquier excepción con tipo que pueda ser detectada por C++ un controlador **catch** coincidente.

Debe usar [/EHA](../../build/reference/eh-exception-handling-model.md) al usar _ **set_se_translator**.

Para especificar una función de traducción personalizada, llame a _ **set_se_translator** con el nombre de la función de traducción como su argumento. La función de traductor que escriba se llama una vez para cada invocación de función en la pila que tenga bloques **try** . No hay ninguna función de traductor predeterminada.

La función de traductor solo debe generar una excepción con tipo de C++. Si hace algo más que eso (por ejemplo, escribir en un archivo de registro), es posible que el programa no funcione según lo esperado, ya que la cantidad de veces que se invoca a la función de traductor depende de la plataforma.

En un entorno multiproceso, las funciones de traductor se mantienen por separado para cada subproceso. Cada subproceso nuevo debe instalar su propia función de traductor. Por lo tanto, cada subproceso se encarga de su propio control de traducción. _ **set_se_translator** es específico de un subproceso; otro archivo DLL puede instalar una función de traducción diferente.

La función *seTransFunction* que escriba debe ser una función compilada de forma nativa (no compilada con/CLR). Debe tomar como argumentos un entero sin signo y un puntero a una estructura **_EXCEPTION_POINTERS** de Win32. Los argumentos son los valores devueltos de las llamadas a las funciones **GetExceptionCode** y **GETEXCEPTIONINFORMATION** de la API Win32, respectivamente.

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

Para _ **set_se_translator**, hay implicaciones al vincular dinámicamente a CRT; otro archivo DLL del proceso podría llamar a _ **set_se_translator** y reemplazar el controlador por el suyo propio.

Al usar _ **set_se_translator** desde código administrado (código compilado con/CLR) o código nativo y administrado mixto, tenga en cuenta que el traductor solo afecta a las excepciones generadas en código nativo. Ninguna excepción administrada que se haya generado en el código administrado (por ejemplo, cuando se genera `System::Exception`) se enruta a través de la función de traductor. Las excepciones generadas en el código administrado mediante la función **RaiseException** de Win32 o provocadas por una excepción del sistema como una excepción de división por cero se enrutan a través del traductor.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_set_se_translator**|\<eh.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Este ejemplo incluye las llamadas para establecer un traductor de excepciones estructurado y para restaurar el antiguo en una clase RAII, `Scoped_SE_Translator`. Esta clase le permite introducir un traductor específico del ámbito como una sola declaración. El destructor de clase restaura el traductor original cuando el control sale del ámbito.

```cpp
// crt_settrans.cpp
// compile with: cl /W4 /EHa crt_settrans.cpp
#include <stdio.h>
#include <windows.h>
#include <eh.h>
#include <exception>

class SE_Exception : public std::exception
{
private:
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
};

void SEFunc()
{
    __try
    {
        printf( "In __try, about to force exception\n" );
        int x = 5;
        int y = 0;
        int *p = &y;
        *p = x / *p;
    }
    __finally
    {
        printf( "In __finally\n" );
    }
}

void trans_func( unsigned int u, EXCEPTION_POINTERS* )
{
    throw SE_Exception( u );
}

int main()
{
    Scoped_SE_Translator scoped_se_translator{ trans_func };
    try
    {
        SEFunc();
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught a __try exception, error %8.8x.\n", e.getSeNumber() );
    }
}
```

```Output
In __try, about to force exception
In __finally
Caught a __try exception, error c0000094.
```

## <a name="example"></a>Ejemplo

Aunque la funcionalidad proporcionada por _ **set_se_translator** no está disponible en código administrado, es posible usar esta asignación en código nativo, incluso si ese código nativo está en una compilación en el modificador **/CLR** , siempre y cuando el código nativo sea indicado mediante `#pragma unmanaged`. Si se produce una excepción estructurada en el código administrado que se va a asignar, se debe marcar `#pragma unmanaged`el código que genera y controla la excepción. En el siguiente código se muestra un uso posible. Para obtener más información, vea [Directives pragma y la palabra clave __pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <stdio.h>
#include <exception>

int thrower_func( int i ) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class SE_Exception : public std::exception
{
private:
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
};

#pragma unmanaged
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS )
{
    throw SE_Exception( u );
}

void DoTest()
{
    try
    {
        thrower_func( 10 );
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught SE_Exception, error %8.8x\n", e.getSeNumber() );
    }
    catch(...)
    {
        printf( "Caught unexpected SEH exception.\n" );
    }
}
#pragma managed

int main() {
    Scoped_SE_Translator scoped_se_translator{ my_trans_func };

    DoTest();
}
```

```Output
Caught SE_Exception, error c0000094
```

## <a name="see-also"></a>Vea también

[Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
