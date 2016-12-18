---
title: "Agregar clase (Cuadro de di&#225;logo) | Microsoft Docs"
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
  - "vc.addclass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Agregar clase (cuadro de diálogo)"
ms.assetid: 916259b8-8e5f-4267-bd10-313483beba67
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar clase (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El cuadro de diálogo **Agregar clase** contiene plantillas que permiten:  
  
-   Abrir a un asistente para código correspondiente, si está disponible. Para obtener más información, vea [Agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md).  
  
 o bien  
  
-   Crear automáticamente una nueva clase propia agregando el código fuente y los archivos adecuados al proyecto.  
  
 Puede acceder al cuadro de diálogo **Agregar clase** desde el menú **Proyecto**, el **Explorador de soluciones** o la [Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
> [!NOTE]
>  Cuando intente agregar una clase que no es adecuada para el proyecto actual, recibirá un mensaje de error. Haga clic en **Aceptar** para volver al cuadro de diálogo **Agregar clase**.  
  
## Plantillas de Agregar clase  
 Hay cuatro categorías de plantillas de **Agregar clase**: .NET, ATL, MFC y genérica. Al seleccionar una plantilla en el panel **Plantillas**, el texto que describe la selección aparecerá debajo de los paneles **Categorías** y **Plantillas**.  
  
### .NET  
  
|Plantilla|Asistente|  
|---------------|---------------|  
|Servicio Web ASP.NET|No disponible|  
|Clase de componente \(.NET\)|No disponible|  
|Clase de instalador \(.NET\)|No disponible|  
|Control de usuario \(.NET\)|No disponible|  
|Windows Form \(.NET\)|No disponible|  
  
### ATL  
  
|Plantilla|Asistente|  
|---------------|---------------|  
|Agregar compatibilidad de ATL a MFC|No disponible|  
|Componente de páginas Active Server ATL|[Asistente para componentes de páginas Active Server ATL](../atl/reference/atl-active-server-page-component-wizard.md)|  
|Control ATL|[Asistente para controles ATL](../atl/reference/atl-control-wizard.md)|  
|Cuadro de diálogo ATL|[Asistente para cuadros de diálogo ATL](../atl/reference/atl-dialog-wizard.md)|  
|Componente COM\+ 1.0 ATL|[Asistente para componentes ATL COM\+ 1.0](../atl/reference/atl-com-plus-1-0-component-wizard.md)|  
|Consumidor OLEDB ATL|[Asistente para consumidores OLE DB ATL](../atl/reference/atl-ole-db-consumer-wizard.md)|  
|Proveedor OLEDB ATL|[Asistente para proveedores OLE DB ATL](../atl/reference/atl-ole-db-provider-wizard.md)|  
|Página de propiedades ATL|[Asistente para páginas de propiedades ATL](../atl/reference/atl-property-page-wizard.md)|  
|Objeto simple ATL|[Asistente para objetos simples ATL](../atl/reference/atl-simple-object-wizard.md)|  
|Proveedor de eventos WMI|Asistente para el proveedor de eventos WMI|  
|Proveedor de instancias WMI|Asistente para el proveedor de instancias WMI|  
  
### MFC  
  
|Plantilla|Asistente|  
|---------------|---------------|  
|MFC \(clase\)|[Asistente para agregar clases MFC](../mfc/reference/mfc-add-class-wizard.md)|  
|Clase MFC de un control ActiveX|[Asistente para agregar clases a partir de un control ActiveX](../ide/add-class-from-activex-control-wizard.md)|  
|Clase MFC de TypeLib|[Asistente para agregar clases de la biblioteca de tipos](../mfc/reference/add-class-from-typelib-wizard.md)|  
|Consumidor ODBC MFC|[Asistente para consumidores ODBC MFC](../mfc/reference/mfc-odbc-consumer-wizard.md)|  
  
### Clases genéricas  
  
|Plantilla|Asistente|  
|---------------|---------------|  
|Clase genérica de C\+\+|[Asistente de clases genéricas de C\+\+](../ide/generic-cpp-class-wizard.md)|  
  
## Vea también  
 [Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una variable miembro](../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función virtual](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Controlador de mensajes de MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Explorar la estructura de clases](../ide/navigating-the-class-structure-visual-cpp.md)