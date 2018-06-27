---
title: Agregar clase de Asistente de Typelib | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.class.typelib
dev_langs:
- C++
helpviewer_keywords:
- Add Class from TypeLib Wizard [MFC]
- COM interfaces, adding classes
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc26f74de76205041228ce92e29309af1ce8959f
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951681"
---
# <a name="add-class-from-typelib-wizard"></a>Asistente para agregar clases de la biblioteca de tipos
Use este asistente para agregar una clase MFC desde una biblioteca de tipos disponibles. El asistente crea una clase para cada interfaz que agregue de la biblioteca de tipos seleccionada.  
  
 **Agregar clase de**  
 Especifica la ubicación de la biblioteca de tipos, desde la que se crea la clase.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Registry**|La biblioteca de tipos se registra en el sistema. Las bibliotecas de tipos registradas se enumeran en **Bibliotecas de tipos disponibles**.|  
|**Archivo**|La biblioteca de tipos no está necesariamente registrada en el sistema pero se incluye en un archivo. Debe proporcionar la ubicación del archivo en **Ubicación**.|  
  
 **Bibliotecas de tipos disponibles**  
 Enumera las bibliotecas de tipos registradas actualmente en el sistema. Seleccione una biblioteca de tipos de esta lista para ver sus interfaces en la **Interfaces** lista.  
  
 Vea "Dentro de COM distribuido: bibliotecas de tipo e integración del lenguaje" en MSDN library para obtener más información sobre el registro de las bibliotecas de tipos.  
  
 **Ubicación**  
 Especifica la ubicación de la biblioteca de tipos. Si hace clic en **Archivo** en **Agregar clase desde**, puede proporcionar la ubicación del archivo que contiene la biblioteca de tipos. Para ir a la ubicación del archivo, haga clic en el botón de puntos suspensivos.  
  
 **Interfaces**  
 Enumera las interfaces de la biblioteca de tipos está seleccionado en el **bibliotecas de tipos disponibles** lista.  
  
|Botón de transferencia|Descripción|  
|---------------------|-----------------|  
|**>**|Agrega la interfaz seleccionada actualmente en la lista **Interfaces**. Atenuado si no se ha seleccionado ninguna interfaz.|  
|**>>**|Agrega todas las interfaces en la biblioteca de tipos está seleccionada en el **bibliotecas de tipos disponibles** lista.|  
|**<**|Quita la clase seleccionada actualmente en la lista **Clases generadas**. Atenuado si no hay ninguna clase está seleccionada actualmente en el **clases generadas** lista.|  
|**<\<**|Quita todas las clases de la lista **Clases generadas**. If atenuado el **clases generadas** lista está vacía.|  
  
 **Clases generadas**  
 Especifica los nombres de clase que se van a generar a partir de las interfaces agregadas con el botón **>** o **>>**. Puede hacer clic en esta casilla para seleccionar una clase y, a continuación, utilice el arriba o abajo teclas para desplazarse a través de la lista ver cada nombre de clase en el **clase** cuadro y nombre de archivo en el **archivo** cuadro que el asistente genera cuando se Haga clic en **finalizar**. Solo se puede seleccionar una clase a la vez en este cuadro.  
  
 Puede quitar una clase si la selecciona en esta lista y hace clic en **<**. No es necesario seleccionar una clase en el cuadro de las clases generadas para quitar todas las clases; haciendo clic en **<<**, quite todas las clases en el **clases generadas** cuadro.  
  
 **Clase**  
 Especifica el nombre de la clase seleccionada en el cuadro **Clases generadas** que el asistente agrega al hacer clic en **Finalizar**. Puede modificar el nombre de la **clase** cuadro.  
  
 **Archivo**  
 Establece el nombre del archivo de encabezado para la clase nueva. De forma predeterminada, este nombre se basa en el que se proporcione en **Clases generadas**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija, o bien para anexar la declaración de clase a un archivo existente. Si elige un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la declaración de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.  
  
## <a name="see-also"></a>Vea también  
 [Clase MFC desde una biblioteca de tipos](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)   
 [Clientes de automatización: Usar bibliotecas de tipos](../../mfc/automation-clients-using-type-libraries.md)

