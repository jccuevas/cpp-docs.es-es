---
title: /Zc:inline (Quitar COMDAT no referenciada)
ms.date: 09/05/2019
f1_keywords:
- /Zc:inline
- VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
- /Zc:inline
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
ms.openlocfilehash: f0c0d9a4e5e5f52d239f1a8591006b3d9e369778
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740107"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline (Quitar COMDAT no referenciada)

Quita los datos o las funciones a los que no se hace referencia y que son COMDAT o que solo tienen vinculación interna. Cuando se especifica **/Zc: inline** , el compilador requiere que las unidades de traducción que usan datos insertados o funciones insertadas también incluyan las definiciones de los datos o las funciones.

## <a name="syntax"></a>Sintaxis

> **/Zc: inline** [ **-** ]

## <a name="remarks"></a>Comentarios

Cuando se especifica **/Zc: inline** , el compilador no emite información de símbolos para las funciones o los datos de COMDAT sin referencia, ni para las funciones o los datos que solo tienen vinculación interna. Esta optimización simplifica parte del trabajo realizado por el enlazador en las compilaciones de versión o cuando se especifica la opción de vinculador [/OPT: Ref](opt-optimizations.md) . Cuando el compilador realiza esta optimización, puede reducir significativamente el tamaño del archivo .obj y mejorar la velocidad del enlazador. Esta opción del compilador no está habilitada cuando las optimizaciones están deshabilitadas ([/OD](od-disable-debug.md)) o cuando se especifica [/GL (optimización de todo el programa)](gl-whole-program-optimization.md) .

De forma predeterminada, esta opción está desactivada ( **/Zc: inline-** ) en compilaciones de línea de comandos. La opción [/permissive-](permissive-standards-conformance.md) no habilita **/Zc: inline**. En los proyectos de MSBuild, la opción se establece mediante las **propiedades** >  > de configuración**C/C++** **Language** > **quitar el código sin referencia y** la propiedad de datos, que se establece en **sí** por predeterminada.

Si se especifica **/Zc: inline** , el compilador exige el requisito de c++ 11 de que todas `inline` las funciones declaradas deben tener una definición disponible en la misma unidad de traducción si se usan. Cuando no se especifica la opción, el compilador de Microsoft permite el código no compatible que invoca a las `inline` funciones declaradas incluso si no hay ninguna definición visible. Para más información, consulte las secciones 3.2 y 7.1.2 del estándar C++11. Esta opción del compilador se introdujo en Visual Studio 2013 Update 2.

Para usar la opción **/Zc: inline** , actualice el código no compatible.

En este ejemplo se muestra cómo el uso no compatible de una declaración de función insertada sin una definición todavía se compila y se vincula cuando se usa la opción **/Zc: inline-** predeterminada:

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

Cuando se habilita **/Zc: inline** , el mismo código produce un error [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) , porque el compilador no emite un cuerpo de código no insertado para `Example::inline_call` en el ejemplo. obj. Esto hace que la llamada no alineada de `main` haga referencia a un símbolo externo sin definir.

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

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la **Página propiedades** > de configuración**C/C++**  > idioma.

1. Modifique la propiedad **quitar código y datos sin referencia** y, después, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](zc-conformance.md)<br/>
