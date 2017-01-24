---
title: "Apariencia, Asistente para controles ATL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.control.misc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para controles ATL, apariencia"
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Apariencia, Asistente para controles ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Insertar aquí el resumen de "Resultados de la búsqueda".  
  
 Utilice esta página del asistente para identificar opciones adicionales de los elementos de usuario para el control.  Esta página está disponible para los controles identificados como **Controles estándar** en **Tipo de control**, en la página [Opciones, Asistente para controles ATL](../../atl/reference/options-atl-control-wizard.md).  
  
## Lista de UIElement  
 **Presentación**  
 Establece la apariencia del control dentro de su contenedor.  
  
-   **Opaco**: establece el bit `VIEWSTATUS_OPAQUE` en la enumeración [VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201) y dibuja el rectángulo entero del control que se pasó al método [CComControlBase::OnDraw](../Topic/CComControlBase::OnDraw.md).  El control se presenta completamente opaco, y ninguno de sus contenedores es visible más allá de sus límites.  
  
     Esta configuración ayuda al contenedor a dibujar el control más rápidamente.  Si no se selecciona esta opción, el control puede contener partes transparentes.  
  
     Sólo un control opaco puede tener un fondo sólido.  
  
-   Establece el bit `VIEWSTATUS_SOLIDBKGND` en la enumeración `VIEWSTATUS`.  El fondo del control aparece como un color sólido sin ninguna trama.  
  
     Esta opción sólo está disponible si también está seleccionada la opción **Opaco**.  
  
 **Agregar control basado en**  
 Establece que el control estará basado en un tipo de control de Windows agregando un miembro de datos [CContainedWindow](../Topic/CContainedWindow.md) a la clase que implementa el control.  También agrega un mapa de mensajes y funciones de controlador de mensajes para controlar los mensajes de Windows relacionados con el control.  Elija en la lista el tipo de control de Windows que desea crear, en su caso.  
  
-   `Button`  
  
-   `ListBox`  
  
-   `SysAnimate32`  
  
-   `SysListView32`  
  
-   `ComboBox`  
  
-   `RichEdit`  
  
-   `SysDateTimePick32`  
  
-   `SysMonthCal32`  
  
-   `ComboBoxEx32`  
  
-   `ScrollBar`  
  
-   `SysHeader32`  
  
-   `SysTabControl32`  
  
-   `Edit`  
  
-   `Static`  
  
-   `SysIPAddress32`  
  
-   `SysTreeView32`  
  
 **Estados varios**  
 Establece opciones adicionales de apariencia y comportamiento del control.  
  
-   **No visible en tiempo de ejecución**: establece que el control sea invisible en tiempo de ejecución.  Se pueden usar controles invisibles para realizar operaciones en segundo plano, como activar eventos a intervalos de tiempo específicos.  
  
-   **Actúa como botón**: establece el bit `OLEMISC_ACTSLIKEBUTTON` en la enumeración [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) para permitir que un control actúe como un botón.  Si el contenedor marcó el sitio cliente del control como botón predeterminado, seleccionar esta opción permite que el control de botón se muestre como botón predeterminado dibujándose a sí mismo con un marco más grueso.  Para obtener más información, consulte [CComControlBase::GetAmbientDisplayAsDefault](../Topic/CComControlBase::GetAmbientDisplayAsDefault.md).  
  
-   **Actúa como etiqueta**: establece el bit `OLEMISC_ACTSLIKELABEL` en la enumeración `OLEMISC` para permitir que un control reemplace la etiqueta nativa del contenedor.  El contenedor determina qué hacer con este marcador, en su caso.  
  
 **Otros**  
 Establece opciones adicionales de comportamiento del control.  
  
-   **DC normalizado**: establece que el control cree un contexto de dispositivo normalizado cuando se le llame para que se dibuje a sí mismo.  Esta acción estandariza la apariencia del control, pero hace que el dibujado sea menos eficiente.  
  
-   **Sólo ventana**: especifica que el control no puede carecer de ventana.  Si no se activa esta opción, el control será automáticamente "sin ventana" en contenedores que admitan objetos sin ventana, y con ventana en contenedores que no admitan objetos sin ventana.  Al activar esta opción se fuerza a que el control tenga ventana, incluso en contenedores compatibles con los objetos sin ventana.  
  
-   **Insertable**: seleccione esta opción para que su control aparezca en el cuadro de diálogo **Insertar objeto** de aplicaciones como Word y Excel.  El control podrá insertarse a continuación en cualquier aplicación que admita objetos incrustados a través de este cuadro de diálogo.  
  
## Vea también  
 [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md)   
 [SUBEDIT Sample: Superclasses a Standard Windows Control](http://msdn.microsoft.com/es-es/30e46bdc-ed92-417c-b6b8-359017265a7b)