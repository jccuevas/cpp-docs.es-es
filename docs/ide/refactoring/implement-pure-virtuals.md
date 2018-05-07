---
title: Implementar virtuales puros | Documentos de Microsoft
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afce516f2718a76658846ed4f992aeabff75330b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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
