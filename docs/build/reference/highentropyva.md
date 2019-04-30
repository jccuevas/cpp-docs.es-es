---
title: /HIGHENTROPYVA
ms.date: 06/12/2018
f1_keywords:
- /HIGHENTROPYVA
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
ms.openlocfilehash: 90d3c868eaab85e3b1a2a416c9aa14b0e27ec8f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270229"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

Especifica si la imagen ejecutable es compatible con la selección aleatoria del diseño del espacio de direcciones (ASLR) de 64 bits de alta entropía.

## <a name="syntax"></a>Sintaxis

> **/HIGHENTROPYVA**[**:NO**]

## <a name="remarks"></a>Comentarios

Esta opción modifica el encabezado de un *imagen ejecutable*, un archivo .dll o .exe, para indicar si se admite ASLR con direcciones de 64 bits. Cuando esta opción está establecida en un ejecutable y todos los módulos de los que este depende, un sistema operativo compatible con ASLR de 64 bits puede fusionar mediante cambio de base los segmentos de la imagen ejecutable en tiempo de carga mediante el uso de direcciones aleatorias en un espacio de direcciones virtuales de 64 bits. Este gran espacio de direcciones dificulta a un atacante la tarea de adivinar la ubicación de un área de memoria específica.

De forma predeterminada, el vinculador permite **/HIGHENTROPYVA** para las imágenes ejecutables de 64 bits. Esta opción requiere [/LARGEADDRESSAWARE](largeaddressaware.md), que también está habilitado de forma predeterminada para las imágenes de 64 bits. **/ HIGHENTROPYVA** no es aplicable a las imágenes ejecutables de 32 bits, donde se omite la opción. Para deshabilitar explícitamente esta opción, utilice **/highentropyva: no**. Para esta opción para tener un efecto, el [/DYNAMICBASE](dynamicbase.md) también se debe establecer la opción.

## <a name="see-also"></a>Vea también

- [Opciones de EDITBIN](editbin-options.md)
- [/DYNAMICBASE](dynamicbase.md)
- [Defensas de seguridad de Software de ISV de Windows](https://msdn.microsoft.com/library/bb430720.aspx)
