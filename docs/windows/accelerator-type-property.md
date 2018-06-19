---
title: Propiedad de tipo de Acelerador | Documentos de Microsoft
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
ms.openlocfilehash: cb1ba8f117fadab7cccb835ba8889d57bcc9f184
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856506"
---
# <a name="accelerator-type-property"></a>Type (Propiedad de acelerador)
El Acelerador **tipo** propiedad determina si la combinación de teclas de método abreviado asociada con el ID de acelerador es una combinación de teclas virtual o un valor de clave de ASCII/ANSI:  
  
-   Si el **tipo** propiedad es **ASCII**, [modificador](../windows/accelerator-modifier-property.md) sólo podrá ser o Alt, o puede tener un acelerador que utilice la tecla CTRL (anteponer a la clave con un ^).  
  
-   Si el **tipo** propiedad es **VIRTKEY**, cualquier combinación de valores de modificador y la clave es válida.  
  
    > [!NOTE]
    >  Si desea especificar un valor en la tabla de aceleradores y tienen el valor se tratará como ASCII/ANSI, simplemente haga clic en el tipo de la entrada en la tabla y seleccione ASCII en la lista desplegable. Sin embargo, si usa el **tecla siguiente** comando (**editar** menú) para especificar la clave, debe cambiar la **tipo** propiedad de VIRTKEY a ASCII *antes de* escribir el código de tecla.  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Establecer las propiedades de Acelerador](../windows/setting-accelerator-properties.md)   
 [Editor de aceleradores](../windows/accelerator-editor.md)