---
title: _amsg_exit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _amsg_exit
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
- _amsg_exit
dev_langs:
- C++
helpviewer_keywords:
- _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbb7f46bb4f3c942fd1c9e1a1d45c1ccf48739f7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="amsgexit"></a>_amsg_exit

Emite un mensaje de error en tiempo de ejecución y se cierra la aplicación con el código de error 255.

## <a name="syntax"></a>Sintaxis

```cpp
void _amsg_exit ( int rterrnum );
```

### <a name="parameters"></a>Parámetros

*rterrnum*<br/>
Número de identificación de un mensaje de error en tiempo de ejecución definido por el sistema.

## <a name="remarks"></a>Comentarios

Esta función emite el mensaje de error en tiempo de ejecución para **stderr** en aplicaciones de consola o muestra un mensaje en un cuadro de mensaje en aplicaciones de Windows. En modo de depuración, puede invocar al depurador antes de salir.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|_amsg_exit|internal.h|