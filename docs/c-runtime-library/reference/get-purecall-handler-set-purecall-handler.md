---
title: _get_purecall_handler, _set_purecall_handler
ms.date: 11/04/2016
api_name:
- _set_purecall_handler
- _set_purecall_handler_m
- _get_purecall_handler
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
- _set_purecall_handler
- _set_purecall_handler_m
- set_purecall_handler_m
- set_purecall_handler
- stdlib/_set_purecall_handler
- stdlib/_get_purecall_handler
- _get_purecall_handler
helpviewer_keywords:
- _set_purecall_handler function
- set_purecall_handler function
- purecall_handler
- set_purecall_handler_m function
- _purecall_handler
- _set_purecall_handler_m function
- _get_purecall_handler function
ms.assetid: 2759b878-8afa-4129-86e7-72afc2153d9c
ms.openlocfilehash: 73fc2ffe5cd4ed65c8695432b53816090bbc5f8e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955672"
---
# <a name="_get_purecall_handler-_set_purecall_handler"></a>_get_purecall_handler, _set_purecall_handler

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
Función a la que se llamará cuando se llame a una función virtual pura. Una función **_purecall_handler** debe tener un tipo de valor devuelto void.

## <a name="return-value"></a>Valor devuelto

**_Purecall_handler**anterior. Devuelve **nullptr** si no había ningún controlador anterior.

## <a name="remarks"></a>Comentarios

Las funciones **_get_purecall_handler** y **_set_purecall_handler** son específicas de Microsoft y solo se aplican al C++ código.

Una llamada a una función virtual pura es un error, porque no tiene ninguna implementación. De forma predeterminada, el compilador genera código que invoca a una función de controlador de errores cuando se llama a una función virtual pura, lo que finaliza el programa. Puede instalar su propia función de controlador de errores para llamadas de función virtual pura, para capturarlas con fines informativos o de depuración. Para usar su propio controlador de errores, cree una función que tenga la firma **_purecall_handler** y, a continuación, use **_set_purecall_handler** para convertirlo en el controlador actual.

Dado que solo hay un **_purecall_handler** para cada proceso, al llamar a **_set_purecall_handler** afecta inmediatamente a todos los subprocesos. El último que llama en cualquiera de los subprocesos establece el controlador.

Para restaurar el comportamiento predeterminado, llame a **_set_purecall_handler** con un argumento **nullptr** .

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
