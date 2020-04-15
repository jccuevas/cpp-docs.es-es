---
title: __p__commode
ms.date: 4/2/2020
api_name:
- __p__commode
- _o___p__commode
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__commode
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
ms.openlocfilehash: fa589c1972d27854e3f794d8283f49d9db5d053a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349313"
---
# <a name="__p__commode"></a>__p__commode

Apunta a la variable global `_commode`, que especifica el *modo de confirmación de archivos* predeterminado para las operaciones de E/S de archivo.

## <a name="syntax"></a>Sintaxis

```cpp
int * __p__commode(
   );
```

## <a name="return-value"></a>Valor devuelto

Puntero a la variable global `_commode`.

## <a name="remarks"></a>Observaciones

La función `__p__commode` es solo para uso interno y no debe llamarse desde código de usuario.

El modo de confirmación de archivos especifica cuándo se escriben datos críticos en el disco. Para obtener más información, consulte [fflush](../c-runtime-library/reference/fflush.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__p\__commode|internal.h|
