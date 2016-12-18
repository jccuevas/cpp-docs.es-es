---
title: "Asistente para agregar clases a partir de un control ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.class.axcontrol"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para controles ActiveX de MFC"
  - "Asistente para agregar clases a partir de un control ActiveX [C++]"
ms.assetid: 668d801c-5fb6-4176-9191-5c38995a4713
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Asistente para agregar clases a partir de un control ActiveX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este asistente se utiliza para agregar clases MFC a partir de un control ActiveX disponible.  El asistente crea una clase para cada interfaz que se agregue desde el control ActiveX seleccionado.  
  
 **Agregar clase desde**  
 Especifica la ubicación de la biblioteca de tipos desde la que se crea la clase.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Registro**|La biblioteca de tipos se registra en el sistema.  Las bibliotecas de tipos registradas aparecen en **Controles ActiveX disponibles**.|  
|**Archivo**|La biblioteca de tipos no tiene por qué estar registrada en el sistema, pero sí está contenida en un archivo.  Deberá especificar la ubicación del archivo en **Ubicación**.|  
  
 **Controles ActiveX disponibles**  
 Especifica los controles ActiveX actualmente registrados en el sistema.  Seleccione un control ActiveX de esta lista para ver sus interfaces en la lista **Interfaces**.  Vea [Controles ActiveX de MFC: distribuir controles ActiveX](../mfc/mfc-activex-controls-distributing-activex-controls.md) para obtener más información sobre cómo registrar controles ActiveX.  
  
 Si eligió **Archivo** en **Agregar clase desde**, no podrá realizar cambios en este cuadro.  
  
 **Ubicación**  
 Especifica la ubicación del control ActiveX.  Si eligió **Archivo** en **Agregar clase desde**, podrá especificar aquí la ubicación del archivo que contiene la biblioteca de tipos.  Para buscar la ubicación del archivo, haga clic en el botón de puntos suspensivos.  
  
 Si eligió **Registro** en **Agregar clase desde**, no podrá realizar cambios en este cuadro.  
  
 **Interfaces**  
 Especifica las interfaces del control ActiveX actualmente seleccionado en **Controles ActiveX disponibles** o en la biblioteca de tipos del archivo especificado en **Ubicación**.  
  
|Botón de transferencia|Descripción|  
|----------------------------|-----------------|  
|**\>**|Agrega la interfaz seleccionada en la lista **Interfaces**.  No estará disponible si no hay ninguna interfaz seleccionada.|  
|**\>\>**|Agrega todas las interfaces del control ActiveX actualmente seleccionado en **Controles ActiveX disponibles** o en la biblioteca de tipos del archivo especificado en **Ubicación**.|  
|**\<**|Quita la clase que está seleccionada en la lista **Clases generadas**.  No estará disponible si no hay ninguna clase seleccionada en la lista **Clases generadas**.|  
|**\<\<**|Quita todas las clases de la lista **Clases generadas**.  No estará disponible si la lista **Clases generadas** está vacía.|  
  
 **Clases generadas**  
 Especifica los nombres de las clases que se generarán a partir de las interfaces agregadas con los botones  **\>** o **\>\>**.  Puede hacer clic en este cuadro para seleccionar una clase y, a continuación, desplazarse en la lista mediante las teclas arriba o abajo, ver el nombre de las clases en el cuadro `Class` y el nombre del archivo en el cuadro **Archivo .H** que el asistente genera cuando se hace clic en **Finalizar**.  En esta casilla sólo puede seleccionar una clase cada vez.  
  
 Para quitar una clase, deberá seleccionarla en la lista y hacer clic en **\<**.  Para quitar todas las clases no es necesario seleccionar una clase en el cuadro **Clases generadas**; sencillamente haga clic en **\<\<** .  
  
 `Class`  
 Especifica el nombre de la clase seleccionada en el cuadro **Clases generadas** que agrega el asistente cuando se hace clic en **Finalizar**.  Puede editar el nombre en el cuadro `Class`.  
  
 **Archivo .H**  
 Establece el nombre del archivo de encabezado para la clase del nuevo objeto.  De forma predeterminada, este nombre está basado en el nombre suministrado en **Clases generadas**.  Haga clic en el botón de los puntos suspensivos para guardar el nombre de archivo en la ubicación que desee o para anexar la declaración de la clase a un archivo existente.  Si elige un archivo ya existente, el asistente no lo guardará en la ubicación seleccionada hasta que seleccione **Finalizar** en el asistente.  
  
 El asistente no sobrescribe ningún archivo.  Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar** el asistente le preguntará si desea anexar la declaración de la clase al contenido del archivo.  Haga clic en **Sí** para anexar el archivo; haga clic en **No** para regresar al asistente y especificar otro nombre de archivo.  
  
 **Archivo .cpp**  
 Establece el nombre del archivo de implementación para la clase del nuevo objeto.  De forma predeterminada, este nombre está basado en el nombre suministrado en **Clases generadas**.  Haga clic en el botón de los puntos suspensivos para guardar el nombre de archivo en la ubicación que desee.  El archivo no quedará guardado en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.  
  
 El asistente no sobrescribe ningún archivo.  Si selecciona el nombre de un archivo que ya existe, al hacer clic en **Finalizar**, el asistente solicitará que especifique si la implementación de la clase debe anexarse al contenido del archivo.  Haga clic en **Sí** para anexar el archivo; haga clic en **No** para regresar al asistente y especificar otro nombre de archivo.  
  
## Vea también  
 [Agregar una clase desde un control ActiveX](../ide/adding-a-class-from-an-activex-control-visual-cpp.md)   
 [Clientes de automatización: Usar bibliotecas de tipos](../mfc/automation-clients-using-type-libraries.md)