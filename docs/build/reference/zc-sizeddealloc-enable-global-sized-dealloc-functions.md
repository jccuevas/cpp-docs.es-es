---
title: '/ Zc: sizeddealloc (habilitar funciones tamaño Global desasignación)'
ms.date: 03/06/2018
f1_keywords:
- sizedDealloc
- /Zc:sizedDealloc
helpviewer_keywords:
- -Zc compiler options (C++)
- sizedDealloc
- Enable Global Sized Deallocation Functions
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 3a73ace0-4d36-420a-b699-0ca6fc0dd134
ms.openlocfilehash: dc381058c6a2ef84542be1d3cdd00c410aa51c2f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809306"
---
# <a name="zcsizeddealloc-enable-global-sized-deallocation-functions"></a>/ Zc: sizeddealloc (habilitar funciones tamaño Global desasignación)

El **/Zc: sizeddealloc** opción del compilador indica al compilador que llamar de forma preferente global `operator delete` o `operator delete[]` funciones que tienen un segundo parámetro de tipo `size_t` cuando el tamaño del objeto está disponible. Pueden usar estas funciones el `size_t` parámetro para optimizar el rendimiento de desasignador.

## <a name="syntax"></a>Sintaxis

> **/Zc:sizedDealloc**[**-**]

## <a name="remarks"></a>Comentarios

En el estándar C ++ 11, puede definir las funciones miembro estáticas `operator delete` y `operator delete[]` que toman un segundo, `size_t` parámetro. Normalmente se utilizan en combinación con [operador new](../../cpp/new-operator-cpp.md) las funciones para implementar más eficaz los asignadores y desasignadores para el objeto. Sin embargo, C ++ 11 no definió un conjunto equivalente de funciones de desasignación en el ámbito global. En C ++ 11, desasignación global funciones que tienen un segundo parámetro de tipo `size_t` se consideran funciones delete de colocación. Se debe llamar explícitamente al pasar un argumento de tamaño.

La C ++ 14 estándar cambia el comportamiento del compilador. Al definir global `operator delete` y `operator delete[]` que toman un segundo parámetro de tipo `size_t`, el compilador prefiere llamar a estas funciones cuando no se invocan las versiones de ámbito de miembro y el tamaño del objeto está disponible. El compilador pasa el argumento de tamaño implícitamente. Las versiones de argumento único se llaman cuando el compilador no puede determinar el tamaño del objeto que se va a desasignar. En caso contrario, se siguen aplican las reglas habituales para elegir la versión de la función de desasignación para invocar. Las llamadas a las funciones globales se pueden especificar explícitamente anteponiendo el operador de resolución de ámbito (`::`) a la llamada de función de desasignación.

De forma predeterminada, Visual C++ a partir de Visual Studio 2015 implementa este C ++ 14 un comportamiento estándar. Puede especificar explícitamente esto estableciendo la **/Zc: sizeddealloc** opción del compilador. Esto representa un que se generen cambios. Utilice la **/Zc:sizedDealloc-** opción para conservar el comportamiento anterior, por ejemplo, cuando el código define los operadores de delete de colocación que usan un segundo parámetro de tipo `size_t`. Las implementaciones de biblioteca de Visual Studio predeterminadas de las funciones de desasignación global que tienen el segundo parámetro de tipo `size_t` invocar las versiones de un parámetro único. Si su código proporcione solo único parámetro global delete de operador y operador delete [], las implementaciones de la biblioteca predeterminada de las funciones de desasignación con tamaño global invocan las funciones globales.

El **/Zc: sizeddealloc** opción del compilador está activada de forma predeterminada. El [/ permissive-](permissive-standards-conformance.md) no afecta la opción **/Zc: sizeddealloc**.

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Desde el **configuraciones** menú desplegable, elija **todas las configuraciones de**.

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir **/Zc: sizeddealloc** o **/Zc:sizedDealloc-** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (Ajuste)](zc-conformance.md)<br/>
