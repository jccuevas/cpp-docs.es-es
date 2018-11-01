---
title: _set_se_translator
ms.date: 02/21/2018
apiname:
- _set_se_translator
apilocation:
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
apitype: DLLExport
f1_keywords:
- _set_se_translator
- set_se_translator
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
ms.openlocfilehash: 6435b5bfa2f1f238ae608e68d97d356af7fb03dd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521159"
---
# <a name="setsetranslator"></a>_set_se_translator

Establecer excepciones con tipo de una función de devolución de llamada por subproceso para traducir excepciones Win32 (excepciones estructuradas de C) en C++.

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

Devuelve un puntero a la función de traductor anterior registrado por **_set_se_translator**, de modo que la función anterior se puede restaurar más adelante. Si no se ha establecido ninguna función anterior, el valor devuelto puede utilizarse para restaurar el comportamiento predeterminado; Este valor puede ser **nullptr**.

## <a name="remarks"></a>Comentarios

El **_set_se_translator** función proporciona un medio para controlar las excepciones Win32 (excepciones estructuradas de C) como C++ excepciones con tipo. Para permitir que cada excepción de C controlarse mediante C++ **catch** controlador, primero defina una clase contenedora de excepciones de C que puede utilizar, o que deriven de atribuir un tipo de clase específico a una excepción de C. Para usar esta clase, instale una función de traductor de excepciones de C a la que llama el mecanismo de control de excepciones internas cada vez que se produce una excepción de C. Dentro de la función de traductor puede producir cualquier excepción con tipo que se puede detectar mediante una búsqueda de coincidencias C++ **catch** controlador.

Debe usar [/EHa](../../build/reference/eh-exception-handling-model.md) al usar **_set_se_translator**.

Para especificar una función de traducción personalizada, llame a **_set_se_translator** utilizando el nombre de la función de traducción como su argumento. La función de traductor que escriba se llama una vez para cada invocación de función en la pila que tenga **intente** bloques. No hay ninguna función de traductor predeterminada.

La función de traductor solo debe generar una excepción con tipo de C++. Si hace algo más que eso (por ejemplo, escribir en un archivo de registro), es posible que el programa no funcione según lo esperado, ya que la cantidad de veces que se invoca a la función de traductor depende de la plataforma.

En un entorno multiproceso, las funciones de traductor se mantienen por separado para cada subproceso. Cada subproceso nuevo debe instalar su propia función de traductor. Por lo tanto, cada subproceso se encarga de su propio control de traducción. **_set_se_translator** es específico de un subproceso; otro archivo DLL puede instalar una función de traducción diferente.

El *seTransFunction* función que escriba debe ser una función compilado en modo nativo (no se compiló con/CLR). Debe tomar un entero sin signo y un puntero a Win32 **_EXCEPTION_POINTERS** estructura como argumentos. Los argumentos son los valores devueltos de llamadas a la API Win32 **GetExceptionCode** y **GetExceptionInformation** funciones, respectivamente.

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

Para **_set_se_translator**, hay implicaciones cuando se vinculan dinámicamente a CRT; otro archivo DLL en el proceso podría llamar a **_set_se_translator** y reemplazar el controlador con su propia.

Cuando se usa **_set_se_translator** desde código administrado (código compilado con/CLR) o mezclar código nativo y administrado, tenga en cuenta que el traductor afecta a las excepciones generadas en código nativo solamente. Ninguna excepción administrada que se haya generado en el código administrado (por ejemplo, cuando se genera `System::Exception`) se enruta a través de la función de traductor. Las excepciones producidas en código administrado mediante la función de Win32 **RaiseException** o causado por una excepción del sistema, como una división por cero se enrutan a través del traductor.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_set_se_translator**|\<eh.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```cpp
// crt_settrans.cpp
// compile with: cl /W4 /EHa crt_settrans.cpp
#include <stdio.h>
#include <windows.h>
#include <eh.h>

class SE_Exception
{
private:
    unsigned int nSE;
public:
    SE_Exception() : nSE{ 0 } {}
    SE_Exception( unsigned int n ) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
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

void trans_func(unsigned int u, EXCEPTION_POINTERS*)
{
    throw SE_Exception(u);
}

int main()
{
    auto original = _set_se_translator(trans_func);
    try
    {
        SEFunc();
    }
    catch(SE_Exception& e)
    {
        printf("Caught a __try exception, error %8.8x.\n", e.getSeNumber());
    }
    _set_se_translator(original);
}
```

```Output
In __try, about to force exception
In __finally
Caught a __try exception, error c0000094.
```

## <a name="example"></a>Ejemplo

Aunque la funcionalidad proporcionada por **_set_se_translator** está disponible en código administrado, es posible usar esta asignación en el código nativo, incluso si dicho código está en una compilación en el **/CLR** cambiar, siempre y cuando el código nativo se indique mediante `#pragma unmanaged`. Si es que se produce una excepción estructurada en código administrado que va a asignarse, se debe marcar el código que genera y controla la excepción `#pragma unmanaged`. En el siguiente código se muestra un uso posible. Para obtener más información, vea [Directives pragma y la palabra clave __pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <assert.h>
#include <stdio.h>

int thrower_func(int i) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class CMyException{
private:
    unsigned int nSE;
public:
    CMyException() : nSE{ 0 } {}
    CMyException(unsigned int n) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
};

#pragma unmanaged
void my_trans_func(unsigned int u, PEXCEPTION_POINTERS)
{
    throw CMyException(u);
}

void DoTest()
{
    try
    {
        thrower_func(10);
    }
    catch(CMyException e)
    {
        printf("Caught CMyException.\n");
    }
    catch(...)
    {
        printf("Caught unexpected SEH exception.\n");
    }
}
#pragma managed

int main() {
    auto original = _set_se_translator(my_trans_func);
    DoTest();
    _set_se_translator(original);
}
```

```Output
Caught CMyException, error c0000094
```

## <a name="see-also"></a>Vea también

[Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
