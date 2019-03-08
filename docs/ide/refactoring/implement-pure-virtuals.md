---
title: Implementar virtuales puras
ms.date: 11/16/2016
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
ms.openlocfilehash: 59e4519f57a1d9bd9ba1cee1ed6ae41bea785a9f
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692676"
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
