---
title: Asistente para agregar eventos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.event.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Event Wizard [C++]
ms.assetid: bdd2a7bb-13d5-44d7-abc9-e785ba4e05ce
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 62ecbe7dece323ce5e99fbe32b3b936fe3661362
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="add-event-wizard"></a>Asistente para agregar eventos
Este asistente agrega un evento a un proyecto de control ActiveX de MFC. Puede especificar su propio evento, puede personalizar un evento estándar habitual o puede seleccionar de una lista de eventos estándar.  
  
 **Nombre del evento**  
 Establece el nombre utilizado por los clientes de automatización para solicitar un evento de la clase. Escriba un nombre o seleccione uno de la lista.  
  
 **Tipo de evento**  
 Indica el tipo de evento para agregar. Disponible solo si se selecciona en el **nombre del evento** lista.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Existencias**|Especifica que un evento estándar, como un clic del botón, se implementará para esta clase. Eventos estándar se definen en la biblioteca (Microsoft Foundation Classes).|  
|**Custom**|Especifica que va a proporcionar su propia implementación del evento.|  
  
 **Nombre interno**  
 Establece el nombre de la función miembro que envía el evento. Disponible solo para los eventos personalizados. El nombre se basa en **nombre del evento**. Puede cambiar el nombre interno si desea proporcionar un nombre distinto al **nombre del evento**.  
  
 **Tipo de parámetro**  
 Establece el tipo para el **nombre de parámetro**. Seleccione el tipo de la lista.  
  
 **Nombre de parámetro**  
 Establece el nombre de un parámetro que se pasa a través del evento. Después de escribir el nombre, debe hacer clic en **agregar** para agregarlo a la lista de parámetros.  
  
 Una vez que pulses **agregar**, el nombre del parámetro aparece en **lista de parámetros**.  
  
> [!NOTE]
>  Si especifica un nombre de parámetro y, a continuación, haga clic en **finalizar** antes de hacer clic **agregar**, entonces, el parámetro no se agrega al evento. Debe buscar el método e insertar el parámetro manualmente. **Lista de parámetros**  
  
 **Add**  
 Agrega el parámetro especificado en **nombre de parámetro**y su tipo, a **lista de parámetros**. Debe hacer clic en **agregar** para agregar un parámetro a la lista.  
  
 **Remove**  
 Quita el parámetro seleccionado en **lista de parámetros** en la lista.  
  
 **Lista de parámetros**  
 Muestra todos los parámetros y sus tipos agregados actualmente al método. A medida que agregue parámetros, el asistente actualiza **lista de parámetros** para mostrar cada parámetro con su tipo.  
  
## <a name="see-also"></a>Vea también  
 [Agregar un evento](../ide/adding-an-event-visual-cpp.md)