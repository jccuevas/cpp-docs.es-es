---
title: Asistente para agregar eventos
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.event.overview
helpviewer_keywords:
- Add Event Wizard [C++]
ms.assetid: bdd2a7bb-13d5-44d7-abc9-e785ba4e05ce
ms.openlocfilehash: e8e78dce3f3f4ec9412be910cde5e0468ce533bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50510778"
---
# <a name="add-event-wizard"></a>Asistente para agregar eventos

Este asistente agrega un evento a un proyecto de control ActiveX de MFC. Puede especificar un evento propio, personalizar un evento estándar habitual o seleccionarlo de una lista de eventos estándar.

- **Nombre del evento**

   Establece el nombre que usan los clientes de Automation para solicitar un evento de la clase. Escriba un nombre o seleccione uno en la lista.

- **Tipo de evento**

   Indica el tipo de evento que se va a agregar. Solo está disponible si se selecciona de la lista **Nombre del evento**.

   |Opción|Descripción|
   |------------|-----------------|
   |**Estándar**|Especifica que un evento estándar, como un clic de botón, se implementará para esta clase. Los eventos estándar se definen en la biblioteca Microsoft Foundation Class (MFC).|
   |**Custom**|Especifica que se va a proporcionar una implementación propia del evento.|

- **Nombre interno**

   Establece el nombre de la función miembro que envía el evento. Solo está disponible para los eventos personalizados. El nombre se basa en **Nombre del evento**. Se puede cambiar el nombre interno si se quiere proporcionar un nombre distinto al **Nombre del evento**.

- **Tipo de parámetro**

   Establece el tipo para el **Nombre de parámetro**. Seleccione el tipo de la lista.

- **Nombre del parámetro**

   Establece el nombre de un parámetro que se va a pasar a través del evento. Después de escribir el nombre, debe hacer clic en **Agregar** para agregarlo a la lista de parámetros.

   Después de hacer clic en **Agregar**, el nombre del parámetro aparece en la **Lista de parámetros**.

   > [!NOTE]
   > Si proporciona un nombre de parámetro y después hace clic en **Finalizar** antes de hacer clic en **Agregar**, el parámetro no se agrega al evento. Debe buscar el método e insertar el parámetro de forma manual. **Lista de parámetros**

- **Add**

   Agrega el parámetro especificado en **Nombre del parámetro**, y su tipo, a la **Lista de parámetros**. Debe hacer clic en **Agregar** para agregar un parámetro a la lista.

- **Remove**

   Quita de la lista el parámetro seleccionado en **Lista de parámetros**.

- **Lista de parámetros**

   Muestra todos los parámetros y sus tipos agregados actualmente al método. A medida que se agregan los parámetros, el asistente actualiza **Lista de parámetros** para mostrar cada uno con su tipo.

## <a name="see-also"></a>Vea también

[Agregar un evento](../ide/adding-an-event-visual-cpp.md)