---
title: Agregar clase de Asistente para controles ActiveX | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.class.axcontrol
dev_langs: C++
helpviewer_keywords:
- ActiveX Control Wizard
- Add Class from ActiveX Control Wizard [C++]
ms.assetid: 668d801c-5fb6-4176-9191-5c38995a4713
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e2b3b1d2b15db47eea8ebc10b2a73cafba5d6952
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="add-class-from-activex-control-wizard"></a>Asistente para agregar clases a partir de un control ActiveX
Use este asistente para agregar una clase MFC desde un control ActiveX disponible. El asistente crea una clase para cada interfaz que se agregue desde el control ActiveX seleccionado.  
  
 **Agregar clase de**  
 Especifica la ubicación de la biblioteca de tipos, desde el que se creó la clase.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Registry**|La biblioteca de tipos está registrada en el sistema. Bibliotecas de tipos registradas aparecen en **controles ActiveX disponible**.|  
|**Archivo**|La biblioteca de tipos no está necesariamente registrada en el sistema pero está contenida en un archivo. Debe proporcionar la ubicación del archivo en **ubicación**.|  
  
 **Controles ActiveX disponibles**  
 Especifica los controles ActiveX actualmente registrados en el sistema. Seleccione un control ActiveX de esta lista para ver sus interfaces en la **Interfaces** lista. Vea [controles ActiveX MFC: distribuir controles ActiveX](../mfc/mfc-activex-controls-distributing-activex-controls.md) para obtener más información sobre cómo registrar controles ActiveX.  
  
 Si hace clic en **archivo** en **Agregar clase desde**, este cuadro no está disponible para el cambio.  
  
 **Ubicación**  
 Especifica la ubicación del control ActiveX. Si hace clic en **archivo** en **Agregar clase desde**, puede proporcionar la ubicación del archivo que contiene la biblioteca de tipos. Para ir a la ubicación del archivo, haga clic en el botón de puntos suspensivos.  
  
 Si hace clic en **registro** en **Agregar clase desde**, este cuadro no está disponible para el cambio.  
  
 **Interfaces**  
 Especifica las interfaces del control ActiveX actualmente seleccionado en **controles ActiveX disponible** o en la biblioteca de tipos en el archivo especificado en **ubicación**.  
  
|Botón de transferencia|Descripción|  
|---------------------|-----------------|  
|**>**|Agrega la interfaz seleccionada en la **Interfaces** lista. No está disponible si no se ha seleccionado ninguna interfaz.|  
|**>>**|Agrega todas las interfaces del control ActiveX actualmente seleccionado en **controles ActiveX disponible** o en la biblioteca de tipos en el archivo especificado en **ubicación**.|  
|**<**|Quita la clase seleccionada actualmente en el **clases generadas** lista. No está disponible si no hay ninguna clase está seleccionada actualmente en el **clases generadas** lista.|  
|**<\<**|Quita todas las clases en el **clases generadas** lista. If no está disponible la **clases generadas** lista está vacía.|  
  
 **Clases generadas**  
 Especifica los nombres de clase que se generarán a partir de las interfaces agregadas con la  **>**  o  **>>**  botón. Puede hacer clic en esta casilla para seleccionar una clase y, a continuación, utilice el arriba o abajo teclas para desplazarse a través de la lista ver cada nombre de clase en el `Class` cuadro y nombre de archivo en el **archivo .h** cuadro que genera el asistente al hacer clic en  **Finalizar**. Puede seleccionar solo una clase a la vez en este cuadro.  
  
 Puede quitar una clase, selecciónelo en esta lista y haga clic en  **<** . No es necesario seleccionar una clase en el **clases generadas** cuadro para quitar todas las clases; haciendo clic  **<<** , quite todas las clases de la **clases generadas** cuadro.  
  
 `Class`  
 Especifica el nombre de la clase seleccionada en el **clases generadas** cuadro que el asistente agrega al hacer clic en **finalizar**. Puede modificar el nombre de la `Class` cuadro.  
  
 **archivo .h**  
 Establece el nombre del archivo de encabezado para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que proporcione en **clases generadas**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección, o para anexar la declaración de clase a un archivo existente. Si elige un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le preguntará si para indicar si se debe anexar la declaración de clase para el contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.  
  
 **archivo .cpp**  
 Establece el nombre del archivo de implementación para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que proporcione en **clases generadas**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección. El archivo no se guarda en la ubicación seleccionada hasta que haga clic **finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le preguntará si para indicar si se debe anexar a la implementación de la clase para el contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.  
  
## <a name="see-also"></a>Vea también  
 [Agregar una clase desde un Control ActiveX](../ide/adding-a-class-from-an-activex-control-visual-cpp.md)   
 [Clientes de automatización: Usar bibliotecas de tipos](../mfc/automation-clients-using-type-libraries.md)