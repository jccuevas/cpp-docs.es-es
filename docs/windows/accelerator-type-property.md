---
title: Propiedad de tipo de Acelerador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Type property
- VIRTKEY
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 214d8ca9c45a3657215833764268794b152bd337
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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