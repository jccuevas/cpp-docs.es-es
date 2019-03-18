---
title: _acmdln, _tcmdln, _wcmdln
ms.date: 11/04/2016
apiname:
- _wcmdln
- _acmdln
apilocation:
- msvcrt.dll
apitype: DLLExport
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
ms.openlocfilehash: f4cacb512cb9b5bb6ea22f4dc4014ac2a2eeebe6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747026"
---
# <a name="acmdln-tcmdln-wcmdln"></a>_acmdln, _tcmdln, _wcmdln

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
