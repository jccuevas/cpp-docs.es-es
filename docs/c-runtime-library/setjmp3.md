---
title: _setjmp3
ms.date: 11/04/2016
api_name:
- _setjmp3
api_location:
- msvcrt.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setjmp3
- _setjmp3
helpviewer_keywords:
- _setjmp3 function
- setjmp3 function
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
ms.openlocfilehash: d7120ddd10322d0b7391608fd388d9f45c1600e8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957792"
---
# <a name="_setjmp3"></a>_setjmp3

Función de CRT interna. Nueva implementación de la función `setjmp`.

## <a name="syntax"></a>Sintaxis

```
int _setjmp3(
   OUT jmp_buf env,
   int count,
   (optional parameters)
);
```

#### <a name="parameters"></a>Parámetros

*env*<br/>
[out] Dirección del búfer para almacenar la información de estado.

*count*<br/>
[in] Número de `DWORD` de información adicionales que hay almacenados en los `optional parameters`.

*optional parameters*<br/>
[in] Datos adicionales insertados por la función intrínseca `setjmp`. El primer `DWORD` es un puntero de función que sirve para desenredar datos extra y regresar a un estado de registro no volatile. El segundo `DWORD` es el nivel de intento que se va a restaurar. Cualquier otro dato extra se guarda en la matriz de datos genéricos de `jmp_buf`.

## <a name="return-value"></a>Valor devuelto

Siempre devuelve 0.

## <a name="remarks"></a>Comentarios

No use esta función en un programa de C++. Se trata de una función intrínseca que no admite C++. Para más información sobre cómo usar `setjmp`, vea [Usar setjmp/longjmp](../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[setjmp](../c-runtime-library/reference/setjmp.md)
