---
title: "Crear declaración / definición | Documentos de Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b1cdcb2-765e-4b93-8cef-92b861f64eba
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 889c8acf5e0ef0ed6a7ac90088a6188658d49d75
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="create-declaration--definition"></a>Crear declaración o definición
**¿Qué:** permite generar inmediatamente la declaración o definición de una función.

**Cuándo:** tiene una función que se necesita una declaración, o viceversa.  

**Por este motivo:** podría crear manualmente la definición de declaración, pero esto lo creará automáticamente, crear el archivo de encabezado/código si es necesario.

**Cómo:**

1. Coloque el cursor de texto o el mouse sobre la función para la que desea crear la definición o declaración.

   ![Código que aparece resaltado](images/createdefinition_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **crear declaración / definición** en el menú contextual.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione **crear declaración / definición** en el menú contextual.

1. Se creará la declaración o definición de la función en el archivo de origen o de encabezado, que verá en una ventana de vista previa emergente.  Si el archivo de origen o de encabezado no existe, se también se crean y se incluirán en el proyecto.

   ![Crear declaración / definición dar como resultado](images/createdefinition_result.png)
