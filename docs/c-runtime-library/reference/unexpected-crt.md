---
title: unexpected (CRT)
ms.date: 11/04/2016
api_name:
- unexpected
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
- unexpected
helpviewer_keywords:
- unexpected function
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
ms.openlocfilehash: 796f5ddbf8467656b5430de1d504f162d891864d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957817"
---
# <a name="unexpected-crt"></a>unexpected (CRT)

Llama a **Terminate** o a la función que especifique mediante **set_unexpected**.

## <a name="syntax"></a>Sintaxis

```C
void unexpected( void );
```

## <a name="remarks"></a>Comentarios

La rutina **inesperada** no se utiliza con la implementación C++ actual del control de excepciones. llamadas **inesperadas** **terminan** de forma predeterminada. Puede cambiar este comportamiento predeterminado si escribe una función de finalización personalizada y llama a **set_unexpected** con el nombre de la función como su argumento. **inesperadas** llama a la última función especificada como argumento para **set_unexpected**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**unexpected**|\<eh.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
