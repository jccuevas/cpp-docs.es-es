---
title: '#error (Directiva) (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
ms.openlocfilehash: bfb5c18f20319e6e6d345f28d3e1850714334b71
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216122"
---
# <a name="error-directive-cc"></a>#error (Directiva) (C++C/)

La directiva **#error** emite un mensaje de error especificado por el usuario en tiempo de compilación y, a continuación, finaliza la compilación.

## <a name="syntax"></a>Sintaxis

> **#error** *token-cadena*

## <a name="remarks"></a>Comentarios

El mensaje de error que esta directiva emite incluye el parámetro *de cadena de token* . El parámetro *de cadena de token* no está sujeto a la expansión de macros. Esta directiva es especialmente útil durante el preprocesamiento, para notificar al desarrollador de una incoherencia de programa o a la infracción de una restricción. En el ejemplo siguiente se muestra el procesamiento de errores durante el preprocesamiento:

```cpp
#if !defined(__cplusplus)
#error C++ compiler required.
#endif
```

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)
