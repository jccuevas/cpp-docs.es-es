---
title: unexpected (CRT)
ms.date: 11/04/2016
apiname:
- unexpected
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
- unexpected
helpviewer_keywords:
- unexpected function
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
ms.openlocfilehash: 78538c0a10e183e72c742b041b297275c0859a03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155490"
---
# <a name="unexpected-crt"></a>unexpected (CRT)

Las llamadas **finalizar** o función que se especifique mediante **set_unexpected**.

## <a name="syntax"></a>Sintaxis

```C
void unexpected( void );
```

## <a name="remarks"></a>Comentarios

El **inesperado** rutina no se utiliza con la implementación actual del control de excepciones de C++. **inesperado** llamadas **finalizar** de forma predeterminada. Puede cambiar este comportamiento predeterminado escribiendo una función de finalización personalizada y llamando a **set_unexpected** con el nombre de la función como su argumento. **inesperado** llama a la última función especificada como argumento a **set_unexpected**.

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
