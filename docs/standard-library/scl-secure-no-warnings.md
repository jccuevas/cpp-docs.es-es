---
title: _SCL_SECURE_NO_WARNINGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
dev_langs:
- C++
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b24012825b883550de6f58e6ce2d53b826f746ca
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965505"
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

Llamar a cualquiera de los métodos potencialmente inseguros detallados en la biblioteca estándar de C++ da como resultado [advertencia del compilador (nivel 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Para deshabilitar esta advertencia, defina la macro _SCL_SECURE_NO_WARNINGS en el código:

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

Si usa encabezados precompilados, coloque esta directiva en el archivo de encabezado precompilado antes de incluir cualquier biblioteca de tiempo de ejecución de C o encabezados de la biblioteca estándar. Si lo coloca en un archivo de código fuente individual antes de incluir el archivo de encabezado precompilado, el compilador lo omite.

## <a name="remarks"></a>Comentarios

Otras formas de deshabilitar la advertencia C4996 incluyen:

- Usar la opción del compilador [/D (Definiciones de preprocesador)](../build/reference/d-preprocessor-definitions.md):

   > CL /D_SCL_SECURE_NO_WARNINGS [otras opciones del compilador] myfile.cpp

- Usar la opción del compilador [/w](../build/reference/compiler-option-warning-level.md):

   > CL /wd4996 [otras opciones del compilador] myfile.cpp

- Usar la directiva [#pragma warning](../preprocessor/warning.md):

   ```cpp
   #pragma warning(disable:4996)
   ```

Además, puede cambiar manualmente el nivel de advertencia C4996 con la opción del compilador **/w\<l>\<n>**. Por ejemplo, para establecer la advertencia C4996 en el nivel 4:

> CL /w44996 [otras opciones del compilador] myfile.cpp

Para más información, vea [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (nivel de advertencia)](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Vea también

[Bibliotecas seguras: Biblioteca estándar de C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
