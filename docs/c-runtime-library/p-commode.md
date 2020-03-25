---
title: __p__commode
ms.date: 11/04/2016
api_name:
- __p__commode
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__commode
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
ms.openlocfilehash: e3121c127c3ebf0f5fccdeb7ae0f67d0164d0965
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171481"
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

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__p\__commode|internal.h|
