---
title: Implementar virtuales puros | Documentos de Microsoft
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f311c2e5832754bfd785084b9aa930b5dbe43845
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2018
---
# <a name="implement-pure-virtuals"></a>Implementar virtuales puros
**¿Qué:** permite generar inmediatamente el código necesario para implementar todos los métodos virtuales puros en una clase. 

**Cuándo:** desea heredar de una clase con funciones virtuales puras.  

**Por este motivo:** podría implementar manualmente las funciones virtuales puras todos los uno por uno, sin embargo, esta característica generará automáticamente todas las firmas de método.

**Cómo**:

1. Coloque el cursor de texto o el mouse sobre la clase en la que va a implementar las funciones virtuales puras de la clase base.

   ![Código resaltado](images/virtuals_highlight.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **implementar todas las virtuales puras para clase*ClassName*'** en el menú contextual, donde  *ClassName* es el nombre de la clase seleccionada.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione **implementar todas las virtuales puras para clase*ClassName*'** en el menú contextual, donde  *ClassName* es el nombre de la clase seleccionada.

1. Las firmas de método virtual puro estará listo para implementarse, creado automáticamente.

   ![Implementar virtuales puros resultado](images/virtuals_result.png)
