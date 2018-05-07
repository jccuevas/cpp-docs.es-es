---
title: Crear declaración / definición | Documentos de Microsoft
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
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="create-declaration--definition"></a>Crear declaración o definición
**¿Qué:** permite generar inmediatamente la declaración o definición de una función.

**Cuándo:** tiene una función que se necesita una declaración, o viceversa.  

**Por este motivo:** podría crear manualmente la definición de declaración, pero esto lo creará automáticamente, crear el archivo de encabezado/código si es necesario.

**Cómo**:

1. Coloque el cursor de texto o el mouse sobre la función para la que desea crear la definición o declaración.

   ![Código resaltado](images/createdefinition_highlight.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **crear declaración / definición** en el menú contextual.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione **crear declaración / definición** en el menú contextual.

1. Se creará la declaración o definición de la función en el archivo de origen o de encabezado, que verá en una ventana de vista previa emergente.  Si el archivo de origen o de encabezado no existe, se también se crean y se incluirán en el proyecto.

   ![Crear declaración / definición dar como resultado](images/createdefinition_result.png)
