---
title: /Zc:throwingNew (inicia nuevo operador de asumir)
ms.date: 03/01/2018
f1_keywords:
- throwingNew
- /Zc:throwingNew
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
ms.openlocfilehash: 782cb55d30bfb11f55a0074a5c3245dd389323ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561231"
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew (inicia nuevo operador de asumir)

Cuando el **/Zc:throwingNew** se especifica la opción, el compilador optimiza las llamadas a `operator new` para omitir las comprobaciones de un puntero null devuelto. Esta opción indica al compilador que asuma que todos los vinculados a las implementaciones de `operator new` y los asignadores personalizados se ajustan al estándar de C++ y produce una excepción durante el error de asignación. De forma predeterminada en Visual Studio, el compilador genera forma pesimista comprobaciones de valores null (**/Zc:throwingNew-**) para estas llamadas, porque los usuarios pueden vincular con una implementación no producen excepciones de `operator new` o escribir rutinas de asignador personalizado que devuelven punteros nulos.

## <a name="syntax"></a>Sintaxis

> **/Zc:throwingNew**[**-**]

## <a name="remarks"></a>Comentarios

Desde el ISO C ++ 98, ha especificado el estándar que el valor predeterminado [new (operador)](../../standard-library/new-operators.md#op_new) produce `std::bad_alloc` cuando se produce un error en la asignación de memoria. Versiones de Visual C++ en Visual Studio 6.0, devuelven un puntero nulo en un error de asignación. A partir de Visual Studio 2002, `operator new` se ajusta al estándar y en caso de error. Para admitir el código que usa el estilo anterior de asignación, Visual Studio proporciona una implementación de vinculable `operator new` en nothrownew.obj que devuelve un puntero null en caso de error. De forma predeterminada, el compilador también genera las comprobaciones de valores null defensivas para evitar que estos asignadores de estilo antiguo causa un bloqueo inmediato en caso de error. El **/Zc:throwingNew** opción indica al compilador que omita estas comprobaciones null, en la suposición de que todos los vinculados memoria asignadores cumplen el estándar. Esto no es aplicable a explícita no producen excepciones `operator new` sobrecargas, que se declaran con un parámetro adicional del tipo `std::nothrow_t` y tienen una explícita `noexcept` especificación.

Conceptualmente, para crear un objeto en el almacén libre, el compilador genera código para asignar la memoria y, a continuación, para invocar su constructor para inicializar la memoria. Dado que el compilador de Visual C++ normalmente no se puede indicar si este código se vinculará a un asignador no conforme, no producen excepciones, de forma predeterminada también genera una comprobación de null antes de llamar al constructor. Esto evita que un puntero nulo en la llamada al constructor de desreferenciación si se produce un error en una asignación no producen excepciones. En la mayoría de los casos, estas comprobaciones no son necesarios porque el valor predeterminado `operator new` asignadores throw en lugar de devolver punteros nulos. Las comprobaciones también tienen desafortunados efectos. El tamaño del código a la saturación, inundan la predicción de ramas e impiden que otras optimizaciones del compilador útiles como devirtualization o const propagación fuera del objeto inicializado. Las comprobaciones de existan únicamente al código de soporte técnico que se vincula a *nothrownew.obj* o tiene personalizado no conformes `operator new` implementaciones. Si no usa no es conforme `operator new`, le recomendamos que use **/Zc:throwingNew** para optimizar el código.

El **/Zc:throwingNew** opción está desactivada de forma predeterminada y no se ve afectado por la [/ permissive-](permissive-standards-conformance.md) opción.

Si se compila con la generación de código en tiempo de vínculo (LTCG), no es necesario especificar **/Zc:throwingNew**. Cuando se compila el código mediante el uso de LTCG, el compilador puede detectar si el valor predeterminado, conforme `operator new` se usa la implementación. Si es así, el compilador deja automáticamente las comprobaciones de null. El vinculador busca la **/ThrowingNew** marca para indicar si la implementación de `operator new` es conforme. Puede especificar esta marca al vinculador mediante la inclusión de esta directiva en el origen de la nueva implementación de un operador personalizado:

```cpp
#pragma comment(linker, "/ThrowingNew")
```

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Desde el **configuración** menú desplegable, elija **todas las configuraciones de**.

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir **/Zc:throwingNew** o **/Zc:throwingNew-** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (Ajuste)](../../build/reference/zc-conformance.md)<br/>
[noexcept (C++)](../../cpp/noexcept-cpp.md)<br/>
[Especificaciones de excepciones (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Finalizar (excepción)](../../standard-library/exception-functions.md#terminate)<br/>
