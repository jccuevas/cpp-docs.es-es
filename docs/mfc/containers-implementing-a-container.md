---
title: 'Contenedores: Implementar un contenedor | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3693cb7d52a048045f4745b69b45cacc4defc75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="containers-implementing-a-container"></a>Contenedores: Implementar un contenedor
En este artículo se resume el procedimiento para implementar un contenedor y apunta a otros artículos que proporcionan que explicaciones más detalladas acerca de la implementación de contenedores. También se muestran algunas características OLE opcionales que desea implementar y los artículos que describen estas características.  
  
#### <a name="to-prepare-your-cwinapp-derived-class"></a>Para preparar la clase derivada de CWinApp  
  
1.  Inicializar las bibliotecas OLE mediante una llamada a **AfxOleInit** en el `InitInstance` función miembro.  
  
2.  Llame a `CDocTemplate::SetContainerInfo` en `InitInstance` para asignar el menú y el Acelerador de recursos que usa cuando un elemento incrustado está activado en contexto. Para obtener más información acerca de este tema, consulte [activación](../mfc/activation-cpp.md).  
  
 Estas características se proporcionan automáticamente cuando usa el Asistente para aplicaciones MFC para crear una aplicación de contenedor. Vea [crear un programa EXE de MFC](../mfc/reference/mfc-application-wizard.md).  
  
#### <a name="to-prepare-your-view-class"></a>Para preparar la clase de vista  
  
1.  Realizar un seguimiento de los elementos seleccionados al mantener un puntero o su propia lista de punteros si admite selección múltiple, los elementos seleccionados. Su `OnDraw` función debe dibujar todos los elementos OLE.  
  
2.  Invalidar `IsSelected` para comprobar si el elemento pasado a la está seleccionado actualmente.  
  
3.  Implemente un **OnInsertObject** controlador de mensaje para mostrar el **Insertar objeto** cuadro de diálogo.  
  
4.  Implemente un `OnSetFocus` controlador para transferir el foco de la vista a una OLE activo en contexto incrustado elemento de mensaje.  
  
5.  Implemente un `OnSize` el controlador de mensajes para informar a un OLE incrustados elemento que sea necesario para cambiar el rectángulo para reflejar el cambio del tamaño de la vista contenedora.  
  
 Dado que la implementación de estas características varía en gran medida de una aplicación a la siguiente, el Asistente para aplicaciones proporciona solo una implementación básica. Probablemente tendrá que personalizar estas funciones para que la aplicación funcione correctamente. Para obtener un ejemplo de esto, consulte la [contenedor](../visual-cpp-samples.md) ejemplo.  
  
#### <a name="to-handle-embedded-and-linked-items"></a>Para controlar los elementos vinculados e incrustados  
  
1.  Derivar una clase de [COleClientItem](../mfc/reference/coleclientitem-class.md). Objetos de esta clase representan los elementos que se han incrustado en o vinculado en el documento OLE.  
  
2.  Invalidar **OnChange**, `OnChangeItemPosition`, y `OnGetItemPosition`. Estas funciones controlan el ajuste de tamaño, posición y modificar los elementos vinculados e incrustados.  
  
 El Asistente para aplicaciones derivará la clase automáticamente, pero es probable que deba reemplazar **OnChange** y las demás funciones mostradas con ella en el paso 2 del procedimiento anterior. Las implementaciones de esqueleto deben personalizarse para la mayoría de las aplicaciones, dado que estas funciones se implementan de forma diferente de una aplicación a la siguiente. Para obtener ejemplos de esto, vea los ejemplos MFC [DRAWCLI](../visual-cpp-samples.md) y [contenedor](../visual-cpp-samples.md).  
  
 Debe agregar un número de elementos a la estructura de menús de la aplicación contenedora para admitir OLE. Para obtener más información al respecto, consulte [menús y recursos: adiciones de contenedor](../mfc/menus-and-resources-container-additions.md).  
  
 También puede admitir algunas de las siguientes características en la aplicación contenedora:  
  
-   Activación en contexto al editar un elemento incrustado.  
  
     Para obtener más información, consulte [activación](../mfc/activation-cpp.md).  
  
-   Creación de elementos OLE arrastrando y colocando una selección desde una aplicación de servidor.  
  
     Para obtener más información, consulte [arrastrar y colocar (OLE)](../mfc/drag-and-drop-ole.md).  
  
-   Vínculos a objetos incrustados o aplicaciones de servidor/contenedor de combinación.  
  
     Para obtener más información, consulte [contenedores: características avanzadas](../mfc/containers-advanced-features.md).  
  
## <a name="see-also"></a>Vea también  
 [Contenedores](../mfc/containers.md)   
 [Contenedores: Elementos de cliente](../mfc/containers-client-items.md)

