---
title: /HIGHENTROPYVA (Compatibilidad con ASLR de 64 bits)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: 5ecbbf8bbd8e74f80f2f5b2d7df0d2ef544112fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291605"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (Compatibilidad con ASLR de 64 bits)

Especifica si la imagen ejecutable es compatible con la selección aleatoria del diseño del espacio de direcciones (ASLR) de 64 bits de alta entropía.

## <a name="syntax"></a>Sintaxis

> **/HIGHENTROPYVA**[**:NO**]

## <a name="remarks"></a>Comentarios

**/ HIGHENTROPYVA** modifica el encabezado de un *imagen ejecutable*, un archivo .dll o .exe, para indicar si ASLR puede utilizar el espacio de direcciones entero de 64 bits. Cuando esta opción está establecida en un ejecutable y todos los módulos de los que este depende, un sistema operativo compatible con ASLR de 64 bits puede fusionar mediante cambio de base los segmentos de la imagen ejecutable en tiempo de carga mediante el uso de direcciones aleatorias en un espacio de direcciones virtuales de 64 bits. Este gran espacio de direcciones dificulta a un atacante la tarea de adivinar la ubicación de un área de memoria específica.

De forma predeterminada, **/HIGHENTROPYVA** está habilitada para las imágenes ejecutables de 64 bits. Esta opción requiere [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md), que también está habilitado de forma predeterminada para las imágenes de 64 bits. **/ HIGHENTROPYVA** no es aplicable a las imágenes ejecutables de 32 bits, donde el vinculador omite la opción. Para deshabilitar explícitamente esta opción, utilice **/highentropyva: no**.

Para **/HIGHENTROPYVA** para tener un efecto en tiempo de carga, [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) también debe estar habilitada. **/ DYNAMICBASE** está habilitada de forma predeterminada y es necesario para habilitar ASLR en Windows Vista y sistemas operativos posteriores. Las versiones anteriores de Windows omiten esta marca.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. En **opciones adicionales**, escriba `/HIGHENTROPYVA` o `/HIGHENTROPYVA:NO`.

## <a name="see-also"></a>Vea también

- [Referencia del enlazador MSVC](linking.md)
- [Opciones del enlazador MSVC](linker-options.md)
- [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)
- [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)
- [Defensas de seguridad de Software de ISV de Windows](https://msdn.microsoft.com/library/bb430720.aspx)
