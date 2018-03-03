---
title: Agregar clase de Asistente de Typelib | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.class.typelib
dev_langs:
- C++
helpviewer_keywords:
- Add Class from TypeLib Wizard [MFC]
- COM interfaces, adding classes
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4aad89b6f3227cac59b6429cc67975db3dad424
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="add-class-from-typelib-wizard"></a>Asistente para agregar clases de la biblioteca de tipos
Use este asistente para agregar una clase MFC desde una biblioteca de tipos disponibles. El asistente crea una clase para cada interfaz que agregue de la biblioteca de tipos seleccionada.  
  
 **Agregar clase de**  
 Especifica la ubicación de la biblioteca de tipos, desde el que se creó la clase.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Registry**|La biblioteca de tipos está registrada en el sistema. Bibliotecas de tipos registradas aparecen en **bibliotecas de tipos disponibles**.|  
|**Archivo**|La biblioteca de tipos no está necesariamente registrada en el sistema pero está contenida en un archivo. Debe proporcionar la ubicación del archivo en **ubicación**.|  
  
 **Bibliotecas de tipos disponibles**  
 Enumera las bibliotecas de tipos registradas actualmente en el sistema. Seleccione una biblioteca de tipos de esta lista para ver sus interfaces en la **Interfaces** lista.  
  
 Vea "Dentro de COM distribuido: bibliotecas de tipo e integración del lenguaje" en MSDN library para obtener más información sobre el registro de las bibliotecas de tipos.  
  
 **Ubicación**  
 Especifica la ubicación de la biblioteca de tipos. Si hace clic en **archivo** en **Agregar clase desde**, puede proporcionar la ubicación del archivo que contiene la biblioteca de tipos. Para ir a la ubicación del archivo, haga clic en el botón de puntos suspensivos.  
  
 **Interfaces**  
 Enumera las interfaces de la biblioteca de tipos está seleccionado en el **bibliotecas de tipos disponibles** lista.  
  
|Botón de transferencia|Descripción|  
|---------------------|-----------------|  
|**>**|Agrega la interfaz seleccionada en la **Interfaces** lista. Atenuado si no se ha seleccionado ninguna interfaz.|  
|**>>**|Agrega todas las interfaces en la biblioteca de tipos está seleccionada en el **bibliotecas de tipos disponibles** lista.|  
|**<**|Quita la clase seleccionada actualmente en el **clases generadas** lista. Atenuado si no hay ninguna clase está seleccionada actualmente en el **clases generadas** lista.|  
|**<\<**|Quita todas las clases en el **clases generadas** lista. If atenuado el **clases generadas** lista está vacía.|  
  
 **Clases generadas**  
 Especifica los nombres de clase que se generarán a partir de las interfaces agregadas con la  **>**  o  **>>**  botón. Puede hacer clic en esta casilla para seleccionar una clase y, a continuación, utilice el arriba o abajo teclas para desplazarse a través de la lista ver cada nombre de clase en el `Class` cuadro y nombre de archivo en el **archivo** cuadro que genera el asistente al hacer clic en  **Finalizar**. Puede seleccionar solo una clase a la vez en este cuadro.  
  
 Puede quitar una clase, selecciónelo en esta lista y haga clic en  **<** . No es necesario seleccionar una clase en el cuadro de las clases generadas para quitar todas las clases; haciendo clic en  **<<** , quite todas las clases en el **clases generadas** cuadro.  
  
 `Class`  
 Especifica el nombre de la clase seleccionada en el **clases generadas** cuadro que el asistente agrega al hacer clic en **finalizar**. Puede modificar el nombre de la `Class` cuadro.  
  
 **Archivo**  
 Establece el nombre del archivo de encabezado para la nueva clase. De forma predeterminada, este nombre se basa en el nombre que proporcione en **clases generadas**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección, o para anexar la declaración de clase a un archivo existente. Si elige un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le preguntará si para indicar si se debe anexar la declaración de clase para el contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.  
  
## <a name="see-also"></a>Vea también  
 [Clase MFC desde una biblioteca de tipos](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)   
 [Clientes de automatización: Usar bibliotecas de tipos](../../mfc/automation-clients-using-type-libraries.md)

