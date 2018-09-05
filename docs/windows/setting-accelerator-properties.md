---
title: Establecer propiedades de Acelerador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b89f409fcf5a856a2207dd8efa655728f57b3fe8
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680140"
---
# <a name="setting-accelerator-properties"></a>Establecer las propiedades de los aceleradores

Puede establecer propiedades de acelerador el [ventana propiedades](/visualstudio/ide/reference/properties-window) en cualquier momento. También puede usar el **acelerador** editor para modificar las propiedades de Acelerador de la tabla de aceleradores. Los cambios realizados mediante el **propiedades** ventana o el **acelerador** editor tiene el mismo resultado: las modificaciones se reflejan inmediatamente en la tabla de aceleradores.

Hay tres propiedades para cada Id. de acelerador:

- El [propiedad modificador](../windows/accelerator-modifier-property.md) establece el Acelerador de combinaciones de teclas de control.

   > [!NOTE]
   > En el **propiedades** ventana, esta propiedad aparece como tres propiedades booleanas independientes que pueden controlarse de forma independiente: **Alt**, **Ctrl**y **MAYÚS**.

- El [propiedad clave](../windows/accelerator-key-property.md) establece la clave real que se usará como el acelerador.

- El [la propiedad Type](../windows/accelerator-type-property.md) determina si la clave se interpreta como virtual (VIRTKEY) o ASCII/ANSI.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Teclas de aceleración predefinidas](../windows/predefined-accelerator-keys.md)  
[Editores de recursos](../windows/resource-editors.md)  
[Editor de aceleradores](../windows/accelerator-editor.md)