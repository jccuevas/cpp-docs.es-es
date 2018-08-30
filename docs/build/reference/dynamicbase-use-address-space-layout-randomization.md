---
title: -DYNAMICBASE (Usar dirección espacio selección aleatoria del diseño) | Microsoft Docs
ms.custom: ''
ms.date: 06/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.RandomizedBaseAddress
dev_langs:
- C++
helpviewer_keywords:
- -DYNAMICBASE linker option
- /DYNAMICBASE linker option
- DYNAMICBASE linker option
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 896e2eca86b7694c8b3b951a8eb080a4cf9e7684
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223426"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE (Usar selección aleatoria del diseño del espacio de direcciones)

Especifica si debe generarse una imagen ejecutable que puede reubicarse aleatoriamente durante la carga mediante el uso de la característica de selección aleatoria (ASLR) de diseño del espacio de direcciones de Windows que estuvo disponible en Windows Vista poseían primera vez.

## <a name="syntax"></a>Sintaxis

> **/ DYNAMICBASE**[**: N**]

## <a name="remarks"></a>Comentarios

El **/DYNAMICBASE** opción modifica el encabezado de un *imagen ejecutable*, un archivo .dll o .exe, para indicar si la aplicación debería fusionarse aleatoriamente en tiempo de carga y permite la dirección virtual selección aleatoria de asignación, lo que afecta a la ubicación de memoria virtual de montones, pilas y otras asignaciones de sistema operativo. El **/DYNAMICBASE** opción se aplica a las imágenes de 32 bits y 64 bits. ASLR se admite en Windows Vista y sistemas operativos posteriores. Omite la opción de sistemas operativos anteriores.

De forma predeterminada, **/DYNAMICBASE** está habilitado. Para deshabilitar esta opción, utilice **: no**. El **/DYNAMICBASE** opción es necesaria para la [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) opción tenga efecto.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **avanzadas** página de propiedades.

1. Modificar el **dirección Base aleatoria** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>.

## <a name="see-also"></a>Vea también

- [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)
- [Opciones del vinculador](../../build/reference/linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Defensas de seguridad de Software de ISV de Windows](https://msdn.microsoft.com/library/bb430720.aspx)