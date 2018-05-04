---
title: _get_purecall_handler, _set_purecall_handler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_purecall_handler
- _set_purecall_handler_m
- _get_purecall_handler
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
- _set_purecall_handler
- _set_purecall_handler_m
- set_purecall_handler_m
- set_purecall_handler
- stdlib/_set_purecall_handler
- stdlib/_get_purecall_handler
- _get_purecall_handler
dev_langs:
- C++
helpviewer_keywords:
- _set_purecall_handler function
- set_purecall_handler function
- purecall_handler
- set_purecall_handler_m function
- _purecall_handler
- _set_purecall_handler_m function
- _get_purecall_handler function
ms.assetid: 2759b878-8afa-4129-86e7-72afc2153d9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1dca104d04546786a361c63461e502f7aa8b6127
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="getpurecallhandler-setpurecallhandler"></a>_get_purecall_handler, _set_purecall_handler

Obtiene o establece el controlador de errores de una llamada de función virtual pura.

## <a name="syntax"></a>Sintaxis

```cpp
typedef void (__cdecl* _purecall_handler)(void);
_purecall_handler __cdecl _get_purecall_handler(void);
_purecall_handler __cdecl _set_purecall_handler(
   _purecall_handler function
);
```

### <a name="parameters"></a>Parámetros

*function*<br/>
Función a la que se llamará cuando se llame a una función virtual pura. A **_purecall_handler** función debe tener un tipo de valor devuelto void.

## <a name="return-value"></a>Valor devuelto

Anterior **_purecall_handler**. Devuelve **nullptr** si no hay ningún controlador anterior.

## <a name="remarks"></a>Comentarios

El **_get_purecall_handler** y **_set_purecall_handler** funciones son específicos de Microsoft y se aplican únicamente al código de C++.

Una llamada a una función virtual pura es un error, porque no tiene ninguna implementación. De forma predeterminada, el compilador genera código que invoca a una función de controlador de errores cuando se llama a una función virtual pura, lo que finaliza el programa. Puede instalar su propia función de controlador de errores para llamadas de función virtual pura, para capturarlas con fines informativos o de depuración. Para usar su propio controlador de errores, cree una función que tiene el **_purecall_handler** firma, a continuación, utilice **_set_purecall_handler** para que sea el controlador actual.

Dado que solo hay un **_purecall_handler** para cada proceso, al llamar a **_set_purecall_handler** inmediatamente afecta a todos los subprocesos. El último que llama en cualquiera de los subprocesos establece el controlador.

Para restaurar el comportamiento predeterminado, llame a **_set_purecall_handler** mediante el uso de un **nullptr** argumento.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_purecall_handler**, **_set_purecall_handler**|\<cstdlib> o \<stdlib.h>|

Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```cpp
// _set_purecall_handler.cpp
// compile with: /W1
#include <tchar.h>
#include <stdio.h>
#include <stdlib.h>

class CDerived;
class CBase
{
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function(void) = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase
{
public:
   CDerived() : CBase(this) {};   // C4355
   virtual void function(void) {};
};

CBase::~CBase()
{
   m_pDerived -> function();
}

void myPurecallHandler(void)
{
   printf("In _purecall_handler.");
   exit(0);
}

int _tmain(int argc, _TCHAR* argv[])
{
   _set_purecall_handler(myPurecallHandler);
   CDerived myDerived;
}
```

```Output
In _purecall_handler.
```

## <a name="see-also"></a>Vea también

[Control de errores](../../c-runtime-library/error-handling-crt.md)<br/>
[_purecall](purecall.md)<br/>
