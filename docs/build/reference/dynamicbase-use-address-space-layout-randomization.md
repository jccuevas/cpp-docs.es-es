---
title: /DYNAMICBASE (Usar selección aleatoria del diseño del espacio de direcciones)
ms.date: 06/12/2018
f1_keywords:
- VC.Project.VCLinkerTool.RandomizedBaseAddress
helpviewer_keywords:
- -DYNAMICBASE linker option
- /DYNAMICBASE linker option
- DYNAMICBASE linker option
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
ms.openlocfilehash: 66d6232ed43f9c842ebbb0e22b57c509cf610afa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170064"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE (Usar selección aleatoria del diseño del espacio de direcciones)

Especifica si se genera una imagen ejecutable que se puede reorganizar aleatoriamente en el momento de la carga mediante la característica de selección aleatoria del diseño del espacio de direcciones (ASLR) de Windows que primero estaba disponible en Windows Vista.

## <a name="syntax"></a>Sintaxis

> **/dynamicbase**[ **: no**]

## <a name="remarks"></a>Observaciones

La opción **/dynamicbase** modifica el encabezado de una *imagen ejecutable*, un archivo. dll o. exe, para indicar si la aplicación se debe reorganizar aleatoriamente en el momento de la carga y permite la selección aleatoria de asignación de direcciones virtuales, que afecta a la ubicación de la memoria virtual de montones, pilas y otras asignaciones del sistema operativo. La opción **/dynamicbase** se aplica a las imágenes de 32 bits y de 64 bits. ASLR es compatible con Windows Vista y sistemas operativos posteriores. Los sistemas operativos anteriores omiten la opción.

De forma predeterminada, **/dynamicbase** está habilitado. Para deshabilitar esta opción, use **/dynamicbase: no**. La opción **/dynamicbase** es necesaria para que la opción [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) tenga un efecto.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione las **propiedades de configuración** > **enlazador** > página de propiedades **avanzadas** .

1. Modifique la propiedad **dirección base aleatoria** .

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>.

## <a name="see-also"></a>Consulte también

- [Referencia del enlazador MSVC](linking.md)
- [Opciones del enlazador MSVC](linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Defensas de seguridad de software de ISV de Windows](https://msdn.microsoft.com/library/bb430720.aspx)
