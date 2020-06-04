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
ms.openlocfilehash: 31979a3181dc57644f1e6877277884e55cebf733
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170946"
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

## <a name="remarks"></a>Observaciones

Esta función emite el mensaje de error en tiempo de ejecución para **stderr** en aplicaciones de consola o muestra un mensaje en un cuadro de mensaje en aplicaciones de Windows. En modo de depuración, puede invocar al depurador antes de salir.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|_amsg_exit|internal.h|
