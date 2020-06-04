---
title: _acmdln, _tcmdln, _wcmdln
ms.date: 11/04/2016
api_name:
- _wcmdln
- _acmdln
api_location:
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _acmdln
- acmdln
- _wcmdln
- wcmdln
- _tcmdln
- tcmdln
helpviewer_keywords:
- _wcmdln global variable
- wcmdln global variable
- _acmdln global variable
- _tcmdln global variable
- tcmdln global variable
- acmdln global variable
ms.assetid: 4fc0a6a0-3f93-420a-a19f-5276061ba539
ms.openlocfilehash: 07061244e06256341a6da7d04e5487e81c4b9378
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940618"
---
# <a name="_acmdln-_tcmdln-_wcmdln"></a>_acmdln, _tcmdln, _wcmdln

Variable global CRT interna. Línea de comandos.

## <a name="syntax"></a>Sintaxis

```
char * _acmdln;
wchar_t * _wcmdln;

#ifdef WPRFLAG
   #define _tcmdln _wcmdln
#else
   #define _tcmdln _acmdln
```

## <a name="remarks"></a>Comentarios

Estas variables de CRT internas almacenan la línea de comandos completa. Se muestran en los símbolos exportados de CRT, pero usarlas en su código no está previsto. `_acmdln` almacena los datos como una cadena de caracteres. `_wcmdln` almacena los datos como una cadena de caracteres anchos. `_tcmdln` se puede definir como `_acmdln` o `_wcmdln`, según lo que sea apropiado.

## <a name="see-also"></a>Vea también

[Variables globales](../c-runtime-library/global-variables.md)
