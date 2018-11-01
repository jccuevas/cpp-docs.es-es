---
title: '#Error (directiva) (C/C ++)'
ms.date: 11/04/2016
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
ms.openlocfilehash: c83fc7ef8135ee0cba37a956df47bcab0f796007
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447819"
---
# <a name="error-directive-cc"></a>#error (Directiva) (C/C++)
El **#error** directiva emite un mensaje de error especificado por el usuario en tiempo de compilación y, a continuación, finaliza la compilación.

## <a name="syntax"></a>Sintaxis

```
#errortoken-string
```

## <a name="remarks"></a>Comentarios

El mensaje de error que esta directiva emite incluye el *token-string* parámetro. El *token-string* parámetro no está sujeto a la expansión de macro. Esta directiva es más útil durante el preprocesamiento para notificar al desarrollador una incoherencia del programa o la infracción de una restricción. En el ejemplo siguiente se muestra el procesamiento de errores durante el preprocesamiento:

```
#if !defined(__cplusplus)
#error C++ compiler required.
#endif
```

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)