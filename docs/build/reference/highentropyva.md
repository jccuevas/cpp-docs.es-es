---
title: -HIGHENTROPYVA | Microsoft Docs
ms.custom: ''
ms.date: 06/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /HIGHENTROPYVA
dev_langs:
- C++
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fec9314be9d69e2cb0af2a98884bd78de1ff679
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202071"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

Especifica si la imagen ejecutable es compatible con la selección aleatoria del diseño del espacio de direcciones (ASLR) de 64 bits de alta entropía.

## <a name="syntax"></a>Sintaxis

> **/ HIGHENTROPYVA**[**: N**]

## <a name="remarks"></a>Comentarios

Esta opción modifica el encabezado de un *imagen ejecutable*, un archivo .dll o .exe, para indicar si se admite ASLR con direcciones de 64 bits. Cuando esta opción está establecida en un ejecutable y todos los módulos de los que este depende, un sistema operativo compatible con ASLR de 64 bits puede fusionar mediante cambio de base los segmentos de la imagen ejecutable en tiempo de carga mediante el uso de direcciones aleatorias en un espacio de direcciones virtuales de 64 bits. Este gran espacio de direcciones dificulta a un atacante la tarea de adivinar la ubicación de un área de memoria específica.

De forma predeterminada, el vinculador permite **/HIGHENTROPYVA** para las imágenes ejecutables de 64 bits. Esta opción requiere [/LARGEADDRESSAWARE](largeaddressaware.md), que también está habilitado de forma predeterminada para las imágenes de 64 bits. **/ HIGHENTROPYVA** no es aplicable a las imágenes ejecutables de 32 bits, donde se omite la opción. Para deshabilitar explícitamente esta opción, utilice **/highentropyva: no**. Para esta opción para tener un efecto, el [/DYNAMICBASE](dynamicbase.md) también se debe establecer la opción.

## <a name="see-also"></a>Vea también

- [Opciones de EDITBIN](editbin-options.md)
- [/DYNAMICBASE](dynamicbase.md)
- [Defensas de seguridad de Software de ISV de Windows](https://msdn.microsoft.com/library/bb430720.aspx)
