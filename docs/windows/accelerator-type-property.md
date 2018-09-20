---
title: Propiedad de tipo de acelerador (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Type property
- VIRTKEY
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1b0d02ab8dfec7b6a3f286b09daf9797d62f0990
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384772"
---
# <a name="accelerator-type-property-c"></a>Propiedad de tipo de acelerador (C++)

El Acelerador **tipo** propiedad determina si la combinación de teclas de método abreviado asociada con el Id. de acelerador es una combinación de teclas virtual o un valor de clave ASCII/ANSI:

- Si el **tipo** propiedad es ASCII, el [modificador](../windows/accelerator-modifier-property.md) sólo puede ser `None` o `Alt`, o puede tener un acelerador que utilice la **Ctrl** clave (especificada por anterior a la clave con un `^`).

- Si el **tipo** propiedad es VIRTKEY, cualquier combinación de `Modifier` y `Key` valores es válido.

   > [!NOTE]
   > Si desea especificar un valor en la tabla de aceleradores y tienen el valor se tratan como ASCII/ANSI, simplemente haga clic en el **tipo** para la entrada en la tabla y seleccione ASCII en la lista desplegable. Sin embargo, si usa el **tecla siguiente** comando (**editar** menú) para especificar el `Key`, debe cambiar la **tipo** propiedad de VIRTKEY a ASCII *antes* escribir el `Key` código.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Establecimiento de las propiedades de los aceleradores](../windows/setting-accelerator-properties.md)<br/>
[Editor de aceleradores](../windows/accelerator-editor.md)