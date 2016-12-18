---
title: "Asistente para cuadros de di&#225;logo ATL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.dlg.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para cuadros de diálogo ATL"
  - "ATL projects, agregar recursos de cuadro de diálogo"
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Asistente para cuadros de di&#225;logo ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este asistente inserta un objeto de cuadro de diálogo ATL en el proyecto, derivado de [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md).  Un cuadro de diálogo derivado de `CAxDialogImpl` puede hospedar controles ActiveX.  
  
 El asistente crea un recurso de cuadro de diálogo que contiene los botones predeterminados **Aceptar** y **Cancelar**.  Puede editar este recurso para agregarle controles ActiveX, por medio del [Editor de cuadros de diálogo](../../mfc/dialog-editor.md), en la Vista de recursos.  
  
 El asistente inserta un [mapa de mensajes](../../atl/message-maps-atl.md) en el archivo de encabezado y declaraciones para controlar los eventos clic predeterminados.  Para obtener más información acerca de los cuadros de diálogo ATL, vea [Implementar un cuadro de diálogo](../../atl/implementing-a-dialog-box.md).  
  
 **Nombre corto**  
 Define el nombre abreviado del objeto de cuadro de diálogo ATL.  El nombre que suministre determinará el nombre de clase y los nombres de archivo \(.cpp y .h\), salvo que modifique estos campos de forma individual.  
  
 `Class`  
 Establece el nombre de la clase que se creará.  Este nombre está basado en el nombre suministrado en **Nombre corto**, precedido por 'C', el prefijo habitual en un nombre de clase.  
  
 **Archivo .H**  
 Establece el nombre del archivo de encabezado para la clase del nuevo objeto.  De forma predeterminada, este nombre se basa en el nombre que indique en **Nombre corto**.  Haga clic en el botón de los puntos suspensivos para guardar el nombre de archivo en la ubicación que desee o para anexar la declaración de la clase a un archivo existente.  Si elige un archivo ya existente, el asistente no lo guardará en la ubicación seleccionada hasta que seleccione **Finalizar** en el asistente.  
  
 El asistente no sobrescribe ningún archivo.  Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar** el asistente le preguntará si desea anexar la declaración de la clase al contenido del archivo.  Haga clic en **Sí** para anexar el archivo; haga clic en **No** para regresar al asistente y especificar otro nombre de archivo.  
  
 **Archivo .cpp**  
 Establece el nombre del archivo de implementación para la clase del nuevo objeto.  De forma predeterminada, este nombre se basa en el nombre que indique en **Nombre corto**.  Haga clic en el botón de los puntos suspensivos para guardar el nombre de archivo en la ubicación que desee.  El archivo no quedará guardado en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.  
  
 El asistente no sobrescribe ningún archivo.  Si selecciona el nombre de un archivo que ya existe, al hacer clic en **Finalizar**, el asistente solicitará que especifique si la implementación de la clase debe anexarse al contenido del archivo.  Haga clic en **Sí** para anexar el archivo; haga clic en **No** para regresar al asistente y especificar otro nombre de archivo.  
  
## Vea también  
 [ATL Dialog Box](../../atl/reference/adding-an-atl-dialog-box.md)