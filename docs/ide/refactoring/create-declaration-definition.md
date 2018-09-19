---
title: Crear declaración o definición | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 6b1cdcb2-765e-4b93-8cef-92b861f64eba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60d583ec47a3f9c5b61599a5945e3cfa0d375b1d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33331288"
---
# <a name="create-declaration--definition"></a>Crear declaración o definición
**Qué:** Permite generar inmediatamente la declaración o definición de una función.

**Cuándo:** Tiene una función que necesita una declaración, o viceversa.  

**Por qué:** Podría crear manualmente la definición o declaración, pero esto la creará de manera automática, creando el archivo de encabezado o código si es necesario.

**Cómo**:

1. Coloque el cursor de texto o el ratón sobre la función para la que quiera crear la declaración o definición.

   ![Código resaltado](images/createdefinition_highlight.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Crear declaración o definición** en el menú contextual.
   * **Mouse**
     * Haga clic con el botón derecho en el menú **Acciones rápidas y refactorizaciones** y seleccione **Crear declaración o definición** en el menú contextual.

1. Se creará la declaración o definición de la función en el archivo de código fuente o de encabezado, que verá en una ventana de vista previa emergente.  Si el archivo de código fuente o de encabezado no existe, también se creará y se incluirá en el proyecto.

   ![Resultado de crear la declaración o definición](images/createdefinition_result.png)
