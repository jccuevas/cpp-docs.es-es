---
title: /Zc:inline (Quitar COMDAT no referenciada)
ms.date: 03/01/2018
f1_keywords:
- /Zc:inline
- VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
- /Zc:inline
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
ms.openlocfilehash: 06bdb3300aae88c6c4c8f7e66af658f47548ac5a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820525"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline (Quitar COMDAT no referenciada)

Quita los datos o las funciones a los que no se hace referencia y que son COMDAT o que solo tienen vinculación interna. Cuando **/Zc: inline** se especifica, el compilador requiere que las unidades de traducción que utilicen datos alineados o funciones insertadas también deben incluir las definiciones de los datos o funciones.

## <a name="syntax"></a>Sintaxis

> **/Zc:inline**[**-**]

## <a name="remarks"></a>Comentarios

Cuando **/Zc: inline** se especifica, el compilador no emite información de símbolos para las funciones COMDAT sin referencias o datos, o para las funciones o datos que solo tienen vinculación interna. Esta optimización simplifica parte del trabajo realizado por el enlazador en las versiones de lanzamiento o cuando la opción del vinculador [/OPT: ref](opt-optimizations.md) se especifica. Cuando el compilador realiza esta optimización, puede reducir significativamente el tamaño del archivo .obj y mejorar la velocidad del enlazador. Esta opción del compilador no está habilitada cuando las optimizaciones están deshabilitadas ([/Od](od-disable-debug.md)) o cuando [/GL (Whole Program Optimization)](gl-whole-program-optimization.md) se especifica.

De forma predeterminada, esta opción está desactivada (**/Zc:inline-**). El [/ permissive-](permissive-standards-conformance.md) no habilita la opción **/Zc: inline**.

Si **/Zc: inline** se especifica, el compilador exige C ++ 11 requiere que todas las funciones declaradas `inline` debe tener una definición disponible en la misma unidad de traducción si se usan. Cuando no se especifica la opción, el compilador de Microsoft permite que el código no conforme que invoca funciones declaradas `inline` aunque ninguna definición esté visible. Para más información, consulte las secciones 3.2 y 7.1.2 del estándar C++11. Esta opción del compilador se introdujo en Visual Studio 2013 Update 2.

Para usar el **/Zc: inline** opción Actualizar código que no son compatibles.

Este ejemplo muestra cómo el uso de una declaración de función alineada sin una definición de incumplimiento todavía se compila y vincula cuando el valor predeterminado **/Zc:inline-** se usa la opción:

```cpp
// example.h
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#pragma once

class Example {
public:
   inline void inline_call(); // declared but not defined inline
   void normal_call();
   Example() {};
};
```

```cpp
// example.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#include <stdio.h>
#include "example.h"

void Example::inline_call() {
   printf("inline_call was called.\n");
}

void Example::normal_call() {
   printf("normal_call was called.\n");
   inline_call(); // with /Zc:inline-, inline_call forced into .obj file
}
```

```cpp
// zcinline.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#include "example.h"

void main() {
   Example example;
   example.inline_call(); // normal call when definition unavailable
}
```

Cuando **/Zc: inline** está habilitada, el mismo código provoca un [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) error, porque el compilador no emite un cuerpo de código no para `Example::inline_call` en example.obj. Esto hace que la llamada no alineada de `main` haga referencia a un símbolo externo sin definir.

Para resolver este error, puede quitar la palabra clave `inline` de la declaración de `Example::inline_call`, mover la definición de `Example::inline_call` al archivo de encabezado o mover la implementación de `Example` a main.cpp. En el ejemplo siguiente, la definición se mueve al archivo de encabezado, donde estará visible para todos los autores de llamadas que incluyan el encabezado.

```cpp
// example2.h
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#pragma once
#include <stdio.h>

class Example2 {
public:
   inline void inline_call() {
      printf("inline_call was called.\n");
   }
   void normal_call();
   Example2() {};
};
```

```cpp
// example2.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#include "example2.h"

void Example2::normal_call() {
   printf("normal_call was called.\n");
   inline_call();
}
```

```cpp
// zcinline2.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#include "example2.h"

void main() {
   Example2 example2;
   example2.inline_call(); // normal call when definition unavailable
}
```

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **lenguaje** página de propiedades.

1. Modificar el **quitar código sin referencia y los datos** propiedad y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](zc-conformance.md)<br/>
