---
title: Establecer propiedades de Acelerador | Documentos de Microsoft
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
ms.openlocfilehash: 5198fc1958863d3b5ad560ffeb8c5576506e9e46
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888851"
---
# <a name="setting-accelerator-properties"></a>Establecer las propiedades de los aceleradores
Puede establecer propiedades de acelerador el [ventana propiedades](/visualstudio/ide/reference/properties-window) en cualquier momento. También puede utilizar el Editor de aceleradores para modificar las propiedades de acelerador de la tabla de aceleradores. Los cambios realizados mediante la ventana Propiedades o el Editor de aceleradores tienen el mismo resultado: las modificaciones se reflejan inmediatamente en la tabla de aceleradores.  
  
 Hay tres propiedades para cada acelerador [identificador](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/3487f185-de96-4b1d-87db-034a52223160/locales/en-US):  
  
-   El [Modifier (propiedad)](../windows/accelerator-modifier-property.md) establece combinaciones de teclas para el Acelerador de control.  
  
    > [!NOTE]
    >  En la ventana Propiedades, esta propiedad aparece como tres propiedades booleanas independientes que pueden controlarse de forma independiente: Alt, Ctrl y Mayús.  
  
-   El [propiedad clave](../windows/accelerator-key-property.md) establece la clave real que se usará como el acelerador.  
  
-   El [propiedad Type](../windows/accelerator-type-property.md) determina si la clave se interpreta como virtual (VIRTKEY) o ASCII/ANSI.  
  

  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Teclas de aceleración predefinidas](../windows/predefined-accelerator-keys.md)   
 [Editores de recursos](../windows/resource-editors.md)   
 [Editor de aceleradores](../windows/accelerator-editor.md)