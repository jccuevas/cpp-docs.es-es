---
title: Asistente para agregar clases a partir de un control ActiveX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.class.axcontrol
dev_langs:
- C++
helpviewer_keywords:
- ActiveX Control Wizard
- Add Class from ActiveX Control Wizard [C++]
ms.assetid: 668d801c-5fb6-4176-9191-5c38995a4713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ab96943e47287c9b54753c8d3a1edb868804274
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336822"
---
# <a name="add-class-from-activex-control-wizard"></a>Asistente para agregar clases a partir de un control ActiveX
Use este asistente para agregar una clase MFC desde un control ActiveX disponible. El asistente crea una clase para cada interfaz que se agregue desde el control ActiveX seleccionado.  
  
 **Agregar clase desde**  
 Especifica la ubicación de la biblioteca de tipos, desde la que se crea la clase.  
  
|Opción|Description|  
|------------|-----------------|  
|**Registry**|La biblioteca de tipos se registra en el sistema. Las bibliotecas de tipos registradas se enumeran en **Controles ActiveX disponibles**.|  
|**Archivo**|La biblioteca de tipos no está necesariamente registrada en el sistema pero se incluye en un archivo. Debe proporcionar la ubicación del archivo en **Ubicación**.|  
  
 **Controles ActiveX disponibles**  
 Especifica los controles ActiveX registrados actualmente en el sistema. Seleccione un control ActiveX de esta lista para mostrar sus interfaces en la lista **Interfaces**. Vea [Controles ActiveX MFC: distribuir controles ActiveX](../mfc/mfc-activex-controls-distributing-activex-controls.md) para obtener más información sobre cómo registrar los controles ActiveX.  
  
 Si hace clic en **Archivo** en **Agregar clase desde**, este cuadro no está disponible para el cambio.  
  
 **Ubicación**  
 Especifica la ubicación del control ActiveX. Si hace clic en **Archivo** en **Agregar clase desde**, puede proporcionar la ubicación del archivo que contiene la biblioteca de tipos. Para ir a la ubicación del archivo, haga clic en el botón de puntos suspensivos.  
  
 Si hace clic en **Registro** en **Agregar clase desde**, este cuadro no está disponible para el cambio.  
  
 **Interfaces**  
 Especifica las interfaces del control ActiveX seleccionado actualmente en **Controles ActiveX disponibles** o en la biblioteca de tipos del archivo especificado en **Ubicación**.  
  
|Botón de transferencia|Description|  
|---------------------|-----------------|  
|**>**|Agrega la interfaz seleccionada actualmente en la lista **Interfaces**. No está disponible si no se ha seleccionado ninguna interfaz.|  
|**>>**|Agrega todas las interfaces del control ActiveX seleccionado actualmente en **Controles ActiveX disponibles** o en la biblioteca de tipos del archivo especificado en **Ubicación**.|  
|**<**|Quita la clase seleccionada actualmente en la lista **Clases generadas**. No está disponible si no hay ninguna clase seleccionada actualmente en la lista **Clases generadas**.|  
|**<\<**|Quita todas las clases de la lista **Clases generadas**. No está disponible si la lista **Clases generadas** está vacía.|  
  
 **Clases generadas**  
 Especifica los nombres de clase que se van a generar a partir de las interfaces agregadas con el botón **>** o **>>**. Puede hacer clic en esta casilla para seleccionar una clase y, después, usar las teclas arriba o abajo para desplazarse a través de la lista y ver todos los nombres de clase en el cuadro `Class` y los nombres de archivo en el cuadro **Archivo .h** que el asistente genera al hacer clic en **Finalizar**. Solo se puede seleccionar una clase a la vez en este cuadro.  
  
 Puede quitar una clase si la selecciona en esta lista y hace clic en **<**. No es necesario seleccionar una clase en el cuadro **Clases generadas** para quitar todas las clases; al hacer clic en **<<** se quitan todas las clases del cuadro **Clases generadas**.  
  
 `Class`  
 Especifica el nombre de la clase seleccionada en el cuadro **Clases generadas** que el asistente agrega al hacer clic en **Finalizar**. Se puede modificar el nombre en el cuadro `Class`.  
  
 **Archivo .h**  
 Establece el nombre del archivo de encabezado para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el que se proporcione en **Clases generadas**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija, o bien para anexar la declaración de clase a un archivo existente. Si elige un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la declaración de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.  
  
 **Archivo .cpp**  
 Establece el nombre del archivo de implementación para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el que se proporcione en **Clases generadas**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija. El archivo no se guarda en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la implementación de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.  
  
## <a name="see-also"></a>Vea también  
 [Agregar una clase desde un control ActiveX](../ide/adding-a-class-from-an-activex-control-visual-cpp.md)   
 [Clientes de automatización: Usar bibliotecas de tipos](../mfc/automation-clients-using-type-libraries.md)