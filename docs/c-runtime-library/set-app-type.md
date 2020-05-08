---
title: _set_app_type
ms.date: 4/2/2020
api_name:
- _set_app_type
- _o__set_app_type
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: 2b78b7205b1e5dda7ac7062747c6dd1065ed1c94
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919919"
---
# <a name="_set_app_type"></a>_set_app_type

Función interna que se usa en el inicio para indicar a CRT si la aplicación es de consola o de interfaz gráfica de usuario.

## <a name="syntax"></a>Sintaxis

```cpp
typedef enum _crt_app_type
{
    _crt_unknown_app,
    _crt_console_app,
    _crt_gui_app
} _crt_app_type;

void __cdecl _set_app_type(
    _crt_app_type appType
    );
```

## <a name="parameters"></a>Parámetros

*appType*<br/>
Valor que indica el tipo de aplicación. Los valores posibles son:

|Value|Descripción|
|----------------|-----------------|
|_crt_unknown_app|Tipo de aplicación desconocido.|
|_crt_console_app|Aplicación de consola (línea de comandos).|
|_crt_gui_app|Aplicación GUI (Windows).|

## <a name="remarks"></a>Observaciones

Normalmente, no es necesario llamar a esta función. Forma parte del código de inicio en tiempo de ejecución de C que se ejecuta antes de llamar a `main` en la aplicación.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|_set_app_type|process.h|
