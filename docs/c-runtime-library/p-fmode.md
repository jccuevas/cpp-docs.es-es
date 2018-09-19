---
title: __p__fmode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __p__fmode
apilocation:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- __p__fmode
dev_langs:
- C++
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c4dcea9e3f35bf5fd8dbfbed9273562ac3db551
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056344"
---
# <a name="pfmode"></a>__p__fmode

Apunta a la variable global `_fmode`, que especifica el *modo de traducción de archivos* predeterminado para las operaciones de E/S de archivo.

## <a name="syntax"></a>Sintaxis

```cpp
int* __p__fmode(
   );
```

## <a name="return-value"></a>Valor devuelto

Puntero a la variable global `_fmode`.

## <a name="remarks"></a>Comentarios

La función `__p__fmode` es solo para uso interno y no debe llamarse desde código de usuario.

El modo de traducción de archivos especifica la traducción `binary` o `text` para las operaciones de E/S [_open](../c-runtime-library/reference/open-wopen.md) y [_pipe](../c-runtime-library/reference/pipe.md). Para obtener más información, consulte [_fmode](../c-runtime-library/fmode.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__p\__fmode|stdlib.h|