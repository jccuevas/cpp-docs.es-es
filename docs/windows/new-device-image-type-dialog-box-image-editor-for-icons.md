---
title: Nuevo &lt;dispositivo&gt; (C++) (Editor de imágenes para iconos) de cuadro de diálogo de tipo de imagen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.newimagetype
dev_langs:
- C++
helpviewer_keywords:
- New <Device> Image Type dialog box [C++]
ms.assetid: 9c1344f5-dea0-42cd-9042-b13032f72be2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c375a10d1c8dadca643ac428422eb388c16cdae6
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313941"
---
# <a name="new-ltdevicegt-image-type-dialog-box-c-image-editor-for-icons"></a>Nuevo &lt;dispositivo&gt; imagen en el cuadro de diálogo de tipo (C++) (Editor de imágenes para iconos)

Permite crear una nueva imagen de dispositivo de un tipo especificado. Para abrir el **New \<dispositivo > imagen** cuadro de diálogo, haga clic en **nuevo tipo de imagen** en el **imagen** menú.

### <a name="target-image-type"></a>Tipo de imagen de destino

Enumera los tipos de imagen disponible. Seleccione el tipo de imagen que desea abrir:

||||
|-|-|-|
|-16 x 16, 16 colores|-48 x 48, 16 colores|-96 x 96, 16 colores|
|-16 x 16, 256 colores|-48 x 48, 256 colores|-96 x 96, 256 colores|
|-16 x 16, monocromático|-48 x 48, monocromático|-96 x 96, monocromático|
|-32 x 32, 16 colores|-64 x 64, 16 colores||
|-32 x 32, 256 colores|-64 x 64, 256 colores||
|-32 x 32, monocromático|-64 x 64, monocromático||

> [!NOTE]
> Las imágenes ya existentes no se mostrará en esta lista.

### <a name="custom"></a>Personalizados

Se abre el [cuadro de diálogo imagen personalizada](custom-image-dialog-box-image-editor-for-icons.md) en el que puede crear una nueva imagen con un tamaño personalizado y el número de colores.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Iconos y cursores: recursos de imagen para dispositivos de presentación](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)  
[Imagen (menú)](../windows/image-menu-image-editor-for-icons.md)  
[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)