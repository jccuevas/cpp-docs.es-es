---
title: Asistente para cuadros de diálogo ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
ms.openlocfilehash: 043c170021ce1ceb072dba3e5a450375f556753a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287926"
---
# <a name="atl-dialog-wizard"></a>Asistente para cuadros de diálogo ATL

Este asistente inserta en el proyecto de un objeto de cuadro de diálogo ATL, derivado de [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Un cuadro de diálogo derivado de `CAxDialogImpl` puede hospedar controles ActiveX.

El asistente crea un recurso de cuadro de diálogo no tiene valor predeterminado **Aceptar** y **cancelar** botones. Puede editar el recurso de cuadro de diálogo y agregar controles ActiveX utilizando la [Editor de cuadro de diálogo](../../windows/dialog-editor.md) en vista de recursos.

El asistente inserta en el archivo de encabezado un [mapa de mensajes](../../atl/message-maps-atl.md) y declaraciones para controlar el valor predeterminado, haga clic en eventos. Consulte [implementa un cuadro de diálogo](../../atl/implementing-a-dialog-box.md) para obtener más información acerca de los cuadros de diálogo ATL.

- **Nombre corto**

   Establece el nombre abreviado para el objeto de cuadro de diálogo ATL. El nombre que proporcione determina el nombre de clase y los nombres de archivos (.cpp y .h), a menos que cambie esos campos individualmente.

- **Clase**

   Establece el nombre de la clase que se va a crear. Este nombre se basa en el nombre que proporcione en **nombre corto**, precedidos por 'C', el prefijo habitual para un nombre de clase.

- **Archivo .h**

   Establece el nombre del archivo de encabezado para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el nombre que proporcione en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija, o bien para anexar la declaración de clase a un archivo existente. Si elige un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.

   El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la declaración de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

- **Archivo .cpp**

   Establece el nombre del archivo de implementación para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el nombre que proporcione en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija. El archivo no se guarda en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.

   El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la implementación de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

## <a name="see-also"></a>Vea también

[Cuadro de diálogo ATL](../../atl/reference/adding-an-atl-dialog-box.md)
