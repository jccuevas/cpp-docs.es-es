---
title: "Contenedores: Implementar un contenedor | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones [OLE], contenedor OLE"
  - "contenedores OLE, implementar"
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Contenedores: Implementar un contenedor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se resume el procedimiento para implementar un contenedor y le apunta a otros casos que proporcionan explicaciones más detalladas sobre implementar contenedores.  También enumera algunas características opcionales OLE que quizá desee implementar y casos que describen estas características.  
  
#### Para preparar la clase CWinApp\-derivada  
  
1.  Inicialice las bibliotecas VIEJAS llamando a **AfxOleInit** en la función miembro de `InitInstance` .  
  
2.  Llame a `CDocTemplate::SetContainerInfo` en `InitInstance` para asignar el menú y los recursos de aceleradores utilizaban cuando un elemento incrustado es en contexto elevado.  Para obtener más información sobre este tema, vea [Activación](../mfc/activation-cpp.md).  
  
 Estas características se proporcionan automáticamente cuando se utiliza el Asistente para aplicaciones MFC para crear una aplicación contenedora.  Vea [Crear un programa MFC EXE](../mfc/reference/mfc-application-wizard.md).  
  
#### Para preparar la clase de vista  
  
1.  Supervise los elementos seleccionados que mantiene un puntero, o la lista de punteros si admite la selección múltiple, elementos seleccionados.  La función de `OnDraw` debe dibujar todos los elementos de OLE.  
  
2.  Reemplace `IsSelected` para comprobar si el último elemento cuando está seleccionado.  
  
3.  Implemente un controlador de mensajes **OnInsertObject** para mostrar el cuadro de diálogo de **Insertar objeto** .  
  
4.  Implemente un controlador de mensajes `OnSetFocus` para transferir el foco de la vista en un elemento insertado OLE activo en contexto.  
  
5.  Implemente un controlador de mensajes `OnSize` para informar a un elemento insertado OLE que necesita cambiar su rectángulo para reflejar el cambio de tamaño de la vista que contiene.  
  
 Dado que la implementación de estas características varía considerablemente de una aplicación a otra, el asistente para aplicaciones sólo proporciona una implementación básica.  Tendrá que probablemente personalizar estas funciones para obtener la aplicación para funcionar correctamente.  Para obtener un ejemplo, vea el ejemplo de [CONTENEDOR](../top/visual-cpp-samples.md) .  
  
#### Administrar elementos incrustados y vinculados  
  
1.  Derive una clase de [COleClientItem](../mfc/reference/coleclientitem-class.md).  Los objetos de esta clase representan los elementos que se han insertado en o se han vinculado al documento OLE.  
  
2.  Reemplazo **OnChange**, `OnChangeItemPosition`, y `OnGetItemPosition`.  Estas funciones controlan el tamaño, posición, y modificando elementos insertados y vinculados.  
  
 El asistente para aplicaciones derivará la clase para usted, pero probablemente necesitará invalidar **OnChange** y otro funciona mencionado con él en el paso 2 del procedimiento anterior.  Las implementaciones necesitan esquemáticas personalizar para la mayoría de las aplicaciones, ya que estas funciones se implementan de manera diferente de una aplicación a otra.  Para obtener ejemplos de esto, vea los ejemplos [DRAWCLI](../top/visual-cpp-samples.md) y [CONTENEDOR](../top/visual-cpp-samples.md)MFC.  
  
 Debe agregar varios elementos a la estructura de menú de la aplicación contenedora para admitir OLE.  Para obtener más información al respecto, vea [Menús y recursos: Adiciones de contenedor](../mfc/menus-and-resources-container-additions.md).  
  
 También puede admitir algunas de las siguientes características en la aplicación contenedora:  
  
-   Activación de contexto al editar un elemento incrustado.  
  
     Para obtener más información, vea [Activación](../mfc/activation-cpp.md).  
  
-   Creación de elementos de OLE arrastrando y colocando una selección de una aplicación de servidor.  
  
     Para obtener más información, vea [Arrastrar y colocar \(OLE\)](../mfc/drag-and-drop-ole.md).  
  
-   Vínculos a los objetos incrustados o al contenedor de combinación y a las aplicaciones de servidor.  
  
     Para obtener más información, vea [Contenedores: Características avanzadas](../mfc/containers-advanced-features.md).  
  
## Vea también  
 [Contenedores](../mfc/containers.md)   
 [Contenedores: Elementos de cliente](../mfc/containers-client-items.md)