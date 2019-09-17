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
ms.openlocfilehash: 930eb45e8069bdd71b5a7986e229b229318d0be8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944116"
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

## <a name="remarks"></a>Comentarios

La función `__p__commode` es solo para uso interno y no debe llamarse desde código de usuario.

El modo de confirmación de archivos especifica cuándo se escriben datos críticos en el disco. Para obtener más información, consulte [fflush](../c-runtime-library/reference/fflush.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__p\__commode|internal.h|