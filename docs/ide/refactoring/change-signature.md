---
title: Cambiar firma | Documentos de Microsoft
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8daaa060-7305-4035-99d2-8b460b4f4454
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5280b4940c2a52fc6e72b397300040ca4c1ac92e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="change-signature"></a>Cambiar firma
**¿Qué:** permite modificar los parámetros de la función.

**Cuándo:** desea reordenar, agregar, quitar o modificar los parámetros de una función que se está usando actualmente en diferentes ubicaciones.  

**Por este motivo:** podría manualmente cambiar estos parámetros usted mismo y, a continuación, buscar todas las llamadas a esa función y cambiarlos uno por uno, pero que puede provocar errores.  Esta herramienta refactorización realizará la tarea automáticamente.

**Cómo:**

1. Coloque el cursor de texto o del mouse en el nombre del método para modificar o uno de sus usos:

   ![Código que aparece resaltado](images/changesignature_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl + R**, a continuación, **CTRL+a**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **Cambiar firma** en el menú contextual.
   * **Mouse**
     * Seleccione **Editar > refactorizar > Reordenar parámetros**.
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **Cambiar firma** en el menú contextual.

1. En el **Cambiar firma** cuadro de diálogo que aparece, puede usar los botones a la derecha para cambiar la firma del método:

   ![Cuadro de diálogo de firma de cambio](images/changesignature_dialog.png)

   | Botón | Descripción
   | ------ | ---
   | **Arriba/abajo**    | Mueve el parámetro seleccionado y Bajar la lista
   | **Add**        | Agregar un nuevo parámetro a la lista
   | **Remove**     | Quita el parámetro seleccionado en la lista
   | **Modificar**     | Modificar el parámetro seleccionado, cambiando su tipo, nombre y si es opcional y cuál debería ser su valor insertado
   | **Revertir**     | Restaurar el parámetro seleccionado en su estado original
   | **Revierte todos** | Restaurar todos los parámetros a su estado original

   > [!TIP]
   > Use la **referencia de vista previa de Skip cambia si se confirman todas las referencias** casilla de verificación para realizar los cambios inmediatamente sin retirar primero la ventana de vista previa.

   Al agregar o modificar un parámetro, verá el **Agregar parámetro** o **Editar parámetro** ventana.

   ![Agregar o modificar parámetros](images/changesignature_addmodify.png)

   En este caso, puede hacer lo siguiente:

   | Entrada | Descripción
   | ----- | ---
   | **Type**               | El tipo del parámetro (int, double, float, etcetera.)
   | **Name**               | El nombre del parámetro
   | **Parámetro opcional** | Hace que el parámetro especificado, opcionalmente
   | **Valor insertado**     | El valor insertado en las llamadas a la función donde no se especifica el parámetro (solo es válido para **agregar**)
   | **Valor predeterminado**      | El valor utilizado por la función de si el llamador no especifica ninguno (sólo es válida para **parámetros opcionales**)

1. Use la **ámbito de búsqueda** de lista desplegable para seleccionar si va a aplicar los cambios en el proyecto o la solución completa.

1. Cuando haya terminado, presione el **Aceptar** botón para realizar los cambios.  Asegúrese de que los cambios que está solicitando se están realizando correctamente.  Utilice las casillas de verificación en la mitad superior de la ventana para habilitar o deshabilitar el cambio de nombre de cualquier elemento.

   ![Cambiar la vista previa de firma](images/changesignature_preview.png)

1. Si todo es correcto, haga clic en el **aplicar** cambiará los botones y las funciones en el código fuente.

   ![Resultado de cambio de firma](images/changesignature_result.png)