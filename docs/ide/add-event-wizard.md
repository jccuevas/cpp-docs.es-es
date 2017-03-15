---
title: "Asistente para agregar eventos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.event.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para agregar eventos [C++]"
ms.assetid: bdd2a7bb-13d5-44d7-abc9-e785ba4e05ce
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Asistente para agregar eventos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este asistente agrega un evento a un proyecto de control ActiveX de MFC.  Puede especificar su propio evento, personalizar un evento estándar habitual o seleccionar eventos estándar en una lista.  
  
 **Nombre del evento**  
 Define el nombre que usan los clientes de automatización para solicitar un evento a la clase.  Escriba un nombre o selecciónelo en la lista.  
  
 **Tipo de evento**  
 Indica el tipo de evento que se va a agregar.  Solo está disponible si lo selecciona en la lista **Nombre de evento**.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Estándar**|Especifica que se implementa para esta clase un evento estándar; por ejemplo, un clic en un botón.  Los eventos estándar están definidos en la biblioteca MFC \(Microsoft Foundation Class\).|  
|**Personalizar**|Especifica que se suministra una implementación del evento definida por el usuario.|  
  
 **Nombre interno**  
 Define el nombre de la función miembro que envía el evento.  Sólo está disponible para eventos personalizados.  El nombre está basado en **Nombre del evento**.  Puede cambiar el nombre interno si desea suministrar un nombre diferente del especificado por **Nombre del evento**.  
  
 **Tipo de parámetro**  
 Establece el tipo del **Nombre de parámetro**.  Selecciónelo en la lista.  
  
 **Nombre de parámetro**  
 Define el nombre de un parámetro que se pasa a través del evento.  Después de escribir el nombre, deberá hacer clic en **Agregar** para agregarlo a la lista de parámetros.  
  
 Después de hacer clic en **Agregar**, el nombre de parámetro aparece en la **Lista de parámetros**.  
  
> [!NOTE]
>  Si especifica un nombre de parámetro y hace clic en **Finalizar** antes de hacer clic en **Agregar**, el parámetro no se agrega al evento.  Debe buscar el método e insertar el parámetro de forma manual. **Lista de parámetros**  
  
 **Agregar**  
 Agrega el parámetro especificado en **Nombre de parámetro**, así como su tipo, a la **Lista de parámetros**.  Debe hacer clic en **Agregar** para agregar un parámetro a la lista.  
  
 **Remove**  
 Quita de la lista el parámetro seleccionado en **Lista de parámetros**.  
  
 **Lista de parámetros**  
 Muestra todos los parámetros, junto con sus tipos, agregados para el método.  A medida que agregue parámetros, el asistente los irá actualizando en la **Lista de parámetros**, donde se muestran junto con su tipo.  
  
## Vea también  
 [Agregar un evento](../ide/adding-an-event-visual-cpp.md)