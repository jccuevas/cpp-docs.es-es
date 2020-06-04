---
title: __p__fmode
ms.date: 4/2/2020
api_name:
- __p__fmode
- _o___p__fmode
api_location:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__fmode
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
ms.openlocfilehash: dfd9962c49b03dbb30223d1d7403b791ed6dbec9
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919876"
---
# <a name="__p__fmode"></a>__p__fmode

Apunta a la variable global `_fmode`, que especifica el *modo de traducción de archivos* predeterminado para las operaciones de E/S de archivo.

## <a name="syntax"></a>Sintaxis

```cpp
int* __p__fmode(
   );
```

## <a name="return-value"></a>Valor devuelto

Puntero a la variable global `_fmode`.

## <a name="remarks"></a>Observaciones

La función `__p__fmode` es solo para uso interno y no debe llamarse desde código de usuario.

El modo de traducción de archivos especifica la traducción `binary` o `text` para las operaciones de E/S [_open](../c-runtime-library/reference/open-wopen.md) y [_pipe](../c-runtime-library/reference/pipe.md). Para obtener más información, consulte [_fmode](../c-runtime-library/fmode.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__p\__fmode|stdlib.h|
