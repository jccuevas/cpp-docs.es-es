---
title: _set_se_translator | Microsoft Docs
ms.custom: 
ms.date: 02/21/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5b5eec59acfe65189368a9b0555c3065b7159aae
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2018
---
# <a name="setsetranslator"></a>_set_se_translator

Establezca una función de devolución de llamada por subproceso para traducir las excepciones Win32 (excepciones estructuradas de C) en C++ con excepciones con tipo.

## <a name="syntax"></a>Sintaxis

```cpp
_se_translator_function _set_se_translator(
    _se_translator_function seTransFunction
);
```

### <a name="parameters"></a>Parámetros

*seTransFunction*  
Puntero a una función de traductor de excepciones estructuradas de C que se escriba.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la función de traductor anterior registrada por `_set_se_translator` para que después se pueda restaurar dicha función. Si no se ha establecido ninguna función anterior, el valor devuelto puede utilizarse para restaurar el comportamiento predeterminado; Este valor puede ser **nullptr**.

## <a name="remarks"></a>Comentarios

La función `_set_se_translator` proporciona una manera para controlar las excepciones Win32 (excepciones estructuradas de C) como excepciones con tipo de C++. Para permitir que cada excepción de C se pueda controlar con un controlador `catch` de C++, primero debe definir una clase contenedora de excepciones de C que se pueda usar (o de la que se pueda derivar) con el objetivo de atribuir un tipo de clase específico a una excepción de C. Para usar esta clase, instale una función de traductor de excepciones de C a la que llama el mecanismo de control de excepciones internas cada vez que se produce una excepción de C. Dentro de la función de traductor puede producir cualquier excepción con tipo que se pueda detectar con un controlador `catch` de C++ que coincida.

Debe usar [/EHa](../../build/reference/eh-exception-handling-model.md) al usar `_set_se_translator`.

Para especificar una función de traducción personalizada, llame a `_set_se_translator` utilizando el nombre de la función de traducción como su argumento. La función de traductor que escriba se llama una vez para cada invocación de función en la pila que tenga bloques `try`. No hay ninguna función de traductor predeterminada.

La función de traductor solo debe generar una excepción con tipo de C++. Si hace algo más que eso (por ejemplo, escribir en un archivo de registro), es posible que el programa no funcione según lo esperado, ya que la cantidad de veces que se invoca a la función de traductor depende de la plataforma.

En un entorno multiproceso, las funciones de traductor se mantienen por separado para cada subproceso. Cada subproceso nuevo debe instalar su propia función de traductor. Por lo tanto, cada subproceso se encarga de su propio control de traducción. `_set_se_translator` es específico de un subproceso; otro archivo DLL puede instalar una función de traducción diferente.

El *seTransFunction* (función) creado por usted debe ser una función de compilación nativa (no se compila con/CLR). Debe tomar un entero sin signo y un puntero a la estructura `_EXCEPTION_POINTERS` de Win32 como argumentos. Los argumentos son los valores devueltos de las llamadas a las funciones `GetExceptionCode` y `GetExceptionInformation` de la API Win32, respectivamente.

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

Para `_set_se_translator`, hay implicaciones a la hora de vincularse dinámicamente a CRT; otro archivo DLL del proceso podría llamar a `_set_se_translator` y reemplazar el controlador por el suyo propio.

Si usa `_set_se_translator` desde el código administrado (código compilado con/clr) o desde un código nativo y administrado combinados, tenga en cuenta que el traductor solo afecta a las excepciones generadas en el código nativo. Ninguna excepción administrada que se haya generado en el código administrado (por ejemplo, cuando se genera `System::Exception`) se enruta a través de la función de traductor. Las excepciones generadas en el código administrado mediante la función `RaiseException` de Win32 o producidas por una excepción del sistema (como una excepción de división por cero) se enrutan a través del traductor.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`_set_se_translator`|\<eh.h>|

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

Aunque la funcionalidad proporcionada por `_set_se_translator` no está disponible en el código administrado, se puede usar esta asignación en el código nativo, incluso si dicho código está en una compilación en el modificador `/clr`, siempre y cuando el código nativo se indique mediante `#pragma unmanaged`. Si se se produce una excepción estructurada en código administrado que se puede asignar, el código que genera y controla la excepción debe marcarse `#pragma unmanaged`. En el siguiente código se muestra un uso posible. Para obtener más información, vea [Directives pragma y la palabra clave __pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

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

[Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)  
[set_terminate](../../c-runtime-library/reference/set-terminate-crt.md)  
[set_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)  
[terminate](../../c-runtime-library/reference/terminate-crt.md)  
[unexpected](../../c-runtime-library/reference/unexpected-crt.md)  
