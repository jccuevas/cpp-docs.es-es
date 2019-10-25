---
title: _amsg_exit
ms.date: 11/04/2016
api_name:
- _amsg_exit
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
- _amsg_exit
helpviewer_keywords:
- _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
ms.openlocfilehash: 2d577bfcf0584ef982ab43ff98674d0cfadd14ba
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939698"
---
# <a name="_amsg_exit"></a>_amsg_exit

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