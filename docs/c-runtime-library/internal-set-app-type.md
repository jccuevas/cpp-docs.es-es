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
ms.openlocfilehash: 8efe2159618f728cfaad33493dd482fbdd5375f7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171494"
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

|Value|Descripción|
|-----------|-----------------|
|_UNKNOWN_APP|Tipo de aplicación desconocido.|
|_CONSOLE_APP|Aplicación de consola (línea de comandos).|
|_GUI_APP|Aplicación GUI (Windows).|

## <a name="remarks"></a>Observaciones

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__set_app_type|internal.h|
