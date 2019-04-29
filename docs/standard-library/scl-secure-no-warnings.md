---
title: _SCL_SECURE_NO_WARNINGS
ms.date: 11/04/2016
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
ms.openlocfilehash: 77c60aed511fc3dbbea2d74e83e36dae735dcb0e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348313"
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

   > cl /wd4996 [other compiler options] myfile.cpp

- Usar la directiva [#pragma warning](../preprocessor/warning.md):

   ```cpp
   #pragma warning(disable:4996)
   ```

Además, puede cambiar manualmente el nivel de advertencia C4996 con la opción del compilador **/w\<l>\<n>**. Por ejemplo, para establecer la advertencia C4996 en el nivel 4:

> cl /w44996 [other compiler options] myfile.cpp

Para más información, vea [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (nivel de advertencia)](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Vea también

[Bibliotecas seguras: biblioteca estándar de C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
