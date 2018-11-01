---
title: _setjmp3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _setjmp3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- setjmp3
- _setjmp3
dev_langs:
- C++
helpviewer_keywords:
- _setjmp3 function
- setjmp3 function
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22416f4036d79f9e9b7c95f1cf9098e450533f39
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054277"
---
# <a name="setjmp3"></a>_setjmp3

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