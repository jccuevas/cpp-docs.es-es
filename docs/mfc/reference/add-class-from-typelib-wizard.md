---
title: "Asistente para agregar clases de la biblioteca de tipos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.class.typelib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para agregar clases de la biblioteca de tipos [C++]"
  - "interfaces COM, agregar clases"
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Asistente para agregar clases de la biblioteca de tipos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Use este asistente para agregar clases MFC a partir de una biblioteca de tipos disponible.  El asistente crea una clase por cada interfaz que agregue de la biblioteca de tipos seleccionada.  
  
 **Agregar clase desde**  
 Especifica la ubicación de la biblioteca de tipos desde la que se crea la clase.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Registro**|La biblioteca de tipos se registra en el sistema.  Las bibliotecas de tipos registradas aparecen en **Controles ActiveX disponibles**.|  
|**Archivo**|La biblioteca de tipos no tiene por qué estar registrada en el sistema, pero sí está contenida en un archivo.  Deberá especificar la ubicación del archivo en **Ubicación**.|  
  
 **Bibliotecas de tipos disponibles**  
 Muestra una relación de las bibliotecas de tipos que están registradas en el sistema.  Seleccione una biblioteca de tipos en esta lista si desea ver sus interfaces en la lista **Interfaces**.  
  
 Para obtener más información sobre cómo registrar bibliotecas de tipos, vea "Dentro de COM distribuido: bibliotecas de tipos e integración del lenguaje" en MSDN Library.  
  
 **Ubicación**  
 Especifica la ubicación de la biblioteca de tipos.  Si eligió **Archivo** en **Agregar clase desde**, podrá especificar aquí la ubicación del archivo que contiene la biblioteca de tipos.  Para buscar la ubicación del archivo, haga clic en el botón de puntos suspensivos.  
  
 **Interfaces**  
 Enumera las interfaces de la biblioteca de tipos que está seleccionada en la lista **Bibliotecas de tipos disponibles**.  
  
|Botón de transferencia|Descripción|  
|----------------------------|-----------------|  
|**\>**|Agrega la interfaz seleccionada en la lista **Interfaces**.  Está atenuado mientras no está seleccionada una interfaz.|  
|**\>\>**|Agrega todas las interfaces de la biblioteca de tipos que está seleccionada en la lista **Bibliotecas de tipos disponibles**.|  
|**\<**|Quita la clase que está seleccionada en la lista **Clases generadas**.  Está atenuado mientras no está seleccionada una clase en la lista **Clases generadas**.|  
|**\<\<**|Quita todas las clases de la lista **Clases generadas**.  Está atenuado mientras la lista **Clases generadas** está vacía.|  
  
 **Clases generadas**  
 Especifica los nombres de clase que se generen de interfaces agregadas mediante el botón de **\>** o de **\>\>** .  Puede hacer clic en este cuadro para seleccionar una clase y, a continuación, desplazarse en la lista mediante las teclas arriba o abajo, ver el nombre de las clases en el cuadro `Class` y el nombre del archivo en el cuadro **Archivo** que el asistente genera cuando se hace clic en **Finalizar**.  En esta casilla sólo puede seleccionar una clase cada vez.  
  
 Puede quitar una clase seleccionándola en esta lista y haciendo clic **\<**.  No necesita seleccionar una clase en el cuadro generado de las clases para quitar todas las clases; haga clic en **\<\<**, quita todas las clases en el cuadro de **Clases generadas** .  
  
 `Class`  
 Especifica el nombre de la clase seleccionada en el cuadro **Clases generadas** que agrega el asistente cuando se hace clic en **Finalizar**.  Puede editar el nombre en el cuadro `Class`.  
  
 **Archivo**  
 Establece el nombre del archivo de encabezado de la nueva clase.  De forma predeterminada, este nombre está basado en el nombre suministrado en **Clases generadas**.  Haga clic en el botón de los puntos suspensivos para guardar el nombre de archivo en la ubicación que desee o para anexar la declaración de la clase a un archivo existente.  Si elige un archivo ya existente, el asistente no lo guardará en la ubicación seleccionada hasta que seleccione **Finalizar** en el asistente.  
  
 El asistente no sobrescribe ningún archivo.  Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar** el asistente le preguntará si desea anexar la declaración de la clase al contenido del archivo.  Haga clic en **Sí** para anexar el archivo; haga clic en **No** para regresar al asistente y especificar otro nombre de archivo.  
  
## Vea también  
 [clase MFC desde una biblioteca de tipos](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)   
 [Clientes de automatización: Usar bibliotecas de tipos](../../mfc/automation-clients-using-type-libraries.md)