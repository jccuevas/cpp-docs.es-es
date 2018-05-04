---
title: /Zc:sizedDealloc (Habilitar tamaño desasignación funciones globales) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- sizedDealloc
- /Zc:sizedDealloc
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- sizedDealloc
- Enable Global Sized Deallocation Functions
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 3a73ace0-4d36-420a-b699-0ca6fc0dd134
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a912b87240ad37e29cade077b7a93aa1e7886a6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="zcsizeddealloc-enable-global-sized-deallocation-functions"></a>/Zc:sizedDealloc (Habilitar tamaño desasignación funciones globales)

El **/Zc:sizedDealloc** opción del compilador indica al compilador que llame de forma preferente global `operator delete` o `operator delete[]` funciones que tienen un segundo parámetro de tipo `size_t` cuando el tamaño del objeto está disponible. Pueden utilizar estas funciones el `size_t` parámetro para optimizar el rendimiento de desasignador.

## <a name="syntax"></a>Sintaxis

> **/Zc:sizedDealloc**[**-**]

## <a name="remarks"></a>Comentarios

En el estándar C ++ 11, puede definir las funciones miembro estáticas `operator delete` y `operator delete[]` que tome un segundo `size_t` parámetro. Normalmente se utilizan en combinación con [new (operador)](../../cpp/new-operator-cpp.md) funciones para implementar más eficaz asignadores y desasignadores para el objeto. Sin embargo, en C ++ 11 no se definió un conjunto equivalente de funciones de desasignación en el ámbito global. En C ++ 11, desasignación global funciones que tienen un segundo parámetro de tipo `size_t` se consideran funciones de eliminación de colocación. Se debe llamar explícitamente al pasar un argumento de tamaño.

La C ++ 14 estándar cambia el comportamiento del compilador. Al definir global `operator delete` y `operator delete[]` que tome un segundo parámetro de tipo `size_t`, el compilador preferir llamar a estas funciones cuando no se invocan las versiones de ámbito de miembro y el tamaño del objeto está disponible. El compilador pasa el argumento de tamaño implícitamente. Las versiones de argumento solo se llama cuando el compilador no puede determinar el tamaño del objeto que se va a cancelar la asignación. En caso contrario, todavía se aplican las reglas habituales para elegir la versión de la función de desasignación debe invocarse. Llamadas a las funciones globales se pueden especificar explícitamente anteponiendo el operador de resolución de ámbito (`::`) a la llamada de función de desasignación.

De forma predeterminada, Visual C++ a partir de Visual Studio 2015 implementa este C ++ 14 el comportamiento estándar. Puede especificar explícitamente esto estableciendo el **/Zc:sizedDealloc** opción del compilador. Esto representa un potencialmente importante cambio. Utilice la **/Zc:sizedDealloc-** opción para conservar el comportamiento anterior, por ejemplo, cuando el código define los operadores de eliminación de colocación que usan un segundo parámetro de tipo `size_t`. Las implementaciones de biblioteca de Visual Studio predeterminadas de las funciones de desasignación globales que tienen el segundo parámetro de tipo `size_t` invocar las versiones de parámetro único. Si el código proporcione solo solo parámetro global delete de operador y operador delete [], las implementaciones de biblioteca predeterminado de las funciones de desasignación con tamaño global invocan las funciones globales.

El **/Zc:sizedDealloc** opción del compilador está activada de forma predeterminada. El [/ permisivo-](permissive-standards-conformance.md) no afecta la opción **/Zc:sizedDealloc**.

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Desde el **configuraciones** menú desplegable, elija **todas las configuraciones de**.

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad para incluir **/Zc:sizedDealloc** o **/Zc:sizedDealloc-** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (Ajuste)](../../build/reference/zc-conformance.md)<br/>
