---
title: __set_app_type
ms.date: 11/04/2016
api_name:
- __set_app_type
- _set_app_type
api_location:
- msvcr90.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __set_app_type
helpviewer_keywords:
- __set_app_type
ms.assetid: f0ac0f4d-70e6-4e96-9e43-eb9d1515490c
ms.openlocfilehash: 4d72eecd454e6c01e88c6869c96b628902690383
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940227"
---
# <a name="__set_app_type"></a>__set_app_type

Establece el tipo de aplicación actual.

## <a name="syntax"></a>Sintaxis

```cpp
void __set_app_type (
   int at
   )
```

#### <a name="parameters"></a>Parámetros

*at*<br/>
Valor que indica el tipo de aplicación. Los valores posibles son:

|Valor|DESCRIPCIÓN|
|-----------|-----------------|
|_UNKNOWN_APP|Tipo de aplicación desconocido.|
|_CONSOLE_APP|Aplicación de consola (línea de comandos).|
|_GUI_APP|Aplicación GUI (Windows).|

## <a name="remarks"></a>Comentarios

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__set_app_type|internal.h|