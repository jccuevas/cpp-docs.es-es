---
title: Guardar y cargar diferentes paletas (Editor de imágenes para iconos) de Color | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.color
dev_langs:
- C++
helpviewer_keywords:
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
ms.assetid: 694b6346-e606-4f19-aa01-9b4ceb47f423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50e74c65e080b11583e6ff1e591ef612b17e9533
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438891"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>Guardar y cargar diferentes paletas de colores (Editor de imágenes para iconos)

Puede guardar y cargar un **colores** paleta que contiene [personalizar los colores](../windows/customizing-or-changing-colors-image-editor-for-icons.md). (De forma predeterminada, el **colores** paleta usado más recientemente se carga automáticamente al iniciar Visual Studio.)

> [!TIP]
> Puesto que la **imagen** editor no tiene ningún medio para restaurar el valor predeterminado **colores** paleta, debe guardar el valor predeterminado **colores** paleta en un nombre, como  *estándar.PAL* o *predeterminada.PAL* por lo que puede restaurar fácilmente la configuración predeterminada.

### <a name="to-save-a-custom-colors-palette"></a>Para guardar una paleta de colores personalizada

1. Desde el **imagen** menú, elija **Guardar paleta**.

2. Desplácese al directorio donde quiera guardar la paleta y escriba un nombre para la misma.

3. Haga clic en **Guardar**.

### <a name="to-load-a-custom-colors-palette"></a>Para cargar una paleta de colores personalizada

1. Desde el **imagen** menú, elija **Cargar paleta**.

2. En el [cuadro de diálogo Cargar paleta de colores](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), desplácese al directorio correcto y seleccione la paleta que desea cargar. **Color** paletas se guardan con una extensión de archivo. PAL.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Trabajar con colores](../windows/working-with-color-image-editor-for-icons.md)