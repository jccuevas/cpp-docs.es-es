---
title: /GUARD (habilitar comprobaciones de restricción)
ms.date: 11/04/2016
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
ms.openlocfilehash: 730e26477f4684ca6339a25a945ae04ff5a823c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565911"
---
# <a name="guard-enable-guard-checks"></a>/GUARD (habilitar comprobaciones de restricción)

Especifica la compatibilidad con las comprobaciones de Protección de flujo de control en la imagen ejecutable.

## <a name="syntax"></a>Sintaxis

```
/GUARD:{CF|NO}
```

## <a name="remarks"></a>Comentarios

Cuando se especifica /GUARD:CF, el vinculador modifica el encabezado de un archivo .dll o .exe para indicar la compatibilidad con las comprobaciones en tiempo de ejecución de Protección de flujo de Control (CFG). El vinculador también agrega los datos requeridos de dirección de destino del flujo de control al encabezado. De forma predeterminada, /GUARD:CF está deshabilitada. Se puede deshabilitar explícitamente mediante el uso de /GUARD:NO. Para que sea eficaz, / Guard: CF también requiere la [/DYNAMICBASE (Usar dirección espacio selección aleatoria del diseño)](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) opción del vinculador, que está activada de forma predeterminada.

Cuando se compila código fuente utilizando el [/Guard: CF](../../build/reference/guard-enable-control-flow-guard.md) opción, el compilador analiza el flujo de control examinando todas las llamadas indirectas de posibles direcciones de destino. El compilador inserta código para comprobar que la dirección de destino de una instrucción de llamada indirecta está en la lista de direcciones de destino conocidas en tiempo de ejecución. Si un programa no supera una comprobación de CFG en tiempo de ejecución, los sistemas operativos compatibles con CFG lo detienen. Esto hace más difícil que un atacante pueda ejecutar código malintencionado mediante el uso de datos dañados para cambiar un destino de llamada.

La opción /GUARD:CF debe especificarse tanto en el compilador como en el vinculador para crear imágenes ejecutables con protección de flujo de control (CFG). El código compilado pero no vinculado mediante /GUARD:CF aumenta el costo de comprobaciones en tiempo de ejecución, pero no habilita la protección CFG. Cuando se especifica la opción/Guard: CF para el `cl` comando para compilar y vincular en un solo paso, el compilador pasa la marca al vinculador. Cuando el **protección de flujo de Control** propiedad está establecida en Visual Studio, se pasa la opción/Guard: CF al compilador y vinculador. Cuando se han compilado por separado los archivos objeto o bibliotecas, la opción debe especificarse explícitamente en el `link` comando.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. Expanda **propiedades de configuración**, **vinculador**, **línea de comandos**.

1. En **opciones adicionales**, escriba `/GUARD:CF`.

## <a name="see-also"></a>Vea también

[/guard (Habilitar Protección de flujo de control)](../../build/reference/guard-enable-control-flow-guard.md)<br/>
[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)