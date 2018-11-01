---
title: Implementar virtuales puras | Microsoft Docs
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
ms.openlocfilehash: 234ae9a67bcbc60ea156fbacb5169d0bd1573a91
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442765"
---
# <a name="implement-pure-virtuals"></a>Implementar virtuales puras
**Qué:** Permite generar inmediatamente el código necesario para implementar todos los métodos virtuales puros en una clase.

**Cuándo:** quiere heredar de una clase con funciones virtuales puras.

**Por qué:** Podría implementar manualmente todas las funciones virtuales puras una por una, pero esta característica generará de manera automática todas las firmas de método.

**Cómo**:

1. Coloque el cursor de texto o el ratón sobre la clase en la que quiera implementar las funciones virtuales puras de la clase base.

   ![Código resaltado](images/virtuals_highlight.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Implementar todas las virtuales puras para la clase "*NombreDeClase*"** en el menú contextual, donde *NombreDeClase* es el nombre de la clase seleccionada.
   * **Mouse**
     * Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**, y seleccione **Implementar todas las virtuales puras para la clase "*NombreDeClase*"** en el menú contextual, donde *NombreDeClase* es el nombre de la clase seleccionada.

1. Las firmas de métodos virtuales puros se crearán automáticamente y estarán listas para la implementación.

   ![Resultado de implementar virtuales puras](images/virtuals_result.png)
