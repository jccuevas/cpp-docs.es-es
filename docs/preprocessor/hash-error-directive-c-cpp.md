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
ms.openlocfilehash: dc229a8eae6938cba32787ecbec6a5aa6a17ab47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383991"
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