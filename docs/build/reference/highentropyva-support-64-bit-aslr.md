---
title: /HIGHENTROPYVA (Compatibilidad con ASLR de 64 bits)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: a8bd1b2231530c0f1632b244edaf36ee14ed65b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534802"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (Compatibilidad con ASLR de 64 bits)

Especifica si la imagen ejecutable es compatible con la selección aleatoria del diseño del espacio de direcciones (ASLR) de 64 bits de alta entropía.

## <a name="syntax"></a>Sintaxis

> **/ HIGHENTROPYVA**[**: N**]

## <a name="remarks"></a>Comentarios

**/ HIGHENTROPYVA** modifica el encabezado de un *imagen ejecutable*, un archivo .dll o .exe, para indicar si ASLR puede utilizar el espacio de direcciones entero de 64 bits. Cuando esta opción está establecida en un ejecutable y todos los módulos de los que este depende, un sistema operativo compatible con ASLR de 64 bits puede fusionar mediante cambio de base los segmentos de la imagen ejecutable en tiempo de carga mediante el uso de direcciones aleatorias en un espacio de direcciones virtuales de 64 bits. Este gran espacio de direcciones dificulta a un atacante la tarea de adivinar la ubicación de un área de memoria específica.

De forma predeterminada, **/HIGHENTROPYVA** está habilitada para las imágenes ejecutables de 64 bits. Esta opción requiere [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md), que también está habilitado de forma predeterminada para las imágenes de 64 bits. **/ HIGHENTROPYVA** no es aplicable a las imágenes ejecutables de 32 bits, donde el vinculador omite la opción. Para deshabilitar explícitamente esta opción, utilice **/highentropyva: no**.

Para **/HIGHENTROPYVA** para tener un efecto en tiempo de carga, [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) también debe estar habilitada. **/ DYNAMICBASE** está habilitada de forma predeterminada y es necesario para habilitar ASLR en Windows Vista y sistemas operativos posteriores. Las versiones anteriores de Windows omiten esta marca.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. En **opciones adicionales**, escriba `/HIGHENTROPYVA` o `/HIGHENTROPYVA:NO`.

## <a name="see-also"></a>Vea también

- [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)
- [Opciones del vinculador](../../build/reference/linker-options.md)
- [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)
- [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)
- [Defensas de seguridad de Software de ISV de Windows](https://msdn.microsoft.com/library/bb430720.aspx)
