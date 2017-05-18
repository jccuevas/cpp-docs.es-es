---
title: "Asistente del cuadro de diálogo ATL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: 43540b1b86dbbf1777e7d5a7f6d8dec5dc618334
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="atl-dialog-wizard"></a>Asistente para cuadros de diálogo ATL
Este asistente inserta en el proyecto un objeto de cuadro de diálogo ATL, derivado de [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Un cuadro de diálogo derivado de `CAxDialogImpl` puede hospedar controles ActiveX.  
  
 El asistente crea un recurso de cuadro de diálogo con predeterminado **Aceptar** y **cancelar** botones. Puede editar el recurso de cuadro de diálogo y agregar controles ActiveX utilizando la [cuadro de diálogo Editor](../../windows/dialog-editor.md) en vista de recursos.  
  
 El asistente inserta en el archivo de encabezado un [mapa de mensajes](../../atl/message-maps-atl.md) y declaraciones para controlar el valor predeterminado, haga clic en eventos. Consulte [implementa un cuadro de diálogo](../../atl/implementing-a-dialog-box.md) para obtener más información acerca de los cuadros de diálogo ATL.  
  
 **Nombre corto**  
 Establece el nombre abreviado del objeto de cuadro de diálogo ATL. El nombre que proporcione determina el nombre de clase y nombres de archivos (.cpp y .h), a menos que cambie estos campos individualmente.  
  
 `Class`  
 Establece el nombre de la clase que se va a crear. Este nombre se basa en el nombre que proporcione en **nombre corto**, precedido por 'C', el prefijo habitual en un nombre de clase.  
  
 **archivo .h**  
 Establece el nombre del archivo de encabezado para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que proporcione en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección, o para anexar la declaración de clase a un archivo existente. Si elige un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le pedirá que especifique si la declaración de clase debe anexarse al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.  
  
 **archivo .cpp**  
 Establece el nombre del archivo de implementación para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que proporcione en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección. El archivo no se guarda en la ubicación seleccionada hasta que haga clic **finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le pedirá que especifique si la implementación de la clase debe anexarse al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.  
  
## <a name="see-also"></a>Vea también  
 [Cuadro de diálogo ATL](../../atl/reference/adding-an-atl-dialog-box.md)


