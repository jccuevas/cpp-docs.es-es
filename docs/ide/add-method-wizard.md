---
title: "Asistente para agregar m&#233;todos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.method.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para agregar métodos [C++]"
  - "métodos [C++], agregar mediante asistentes"
ms.assetid: b9a71b0e-9ecf-40fa-9f86-4200cb23d671
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Asistente para agregar m&#233;todos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este asistente se utiliza para agregar un método a una interfaz.  En función del tipo de proyecto o de interfaz al que se esté agregando el método, el asistente mostrará opciones distintas.  
  
## Nombres  
 **Tipo de valor devuelto**  
 El tipo de datos devuelto por el método.  Se recomienda `HRESULT` para todos los tipos de interfaz, ya que proporciona una manera estándar de devolver errores.  
  
|Tipo de interfaz|Descripción|  
|----------------------|-----------------|  
|Interfaz dual|`HRESULT`.  No se puede cambiar.|  
|Interfaz personalizada|`HRESULT`.  No se puede cambiar.|  
|Interfaz personalizada local|Especifique su propio tipo de valor devuelto o selecciónelo de la lista.|  
|Dispinterface|Especifique su propio tipo de valor devuelto o selecciónelo de la lista.|  
|Dispinterface de controles ActiveX de MFC|Si implementa un método estándar, el tipo de valor devuelto utilizará el valor apropiado y no se podrá cambiar.  Si selecciona un método de la lista **Nombre de método** y, después de activar **Seleccione el tipo de método**, hace clic en **Personalizado**, seleccionará un tipo de valor devuelto de la lista.|  
  
 **Nombre del método**  
 Permite establecer el nombre del método.  
  
|Tipo de interfaz|Descripción|  
|----------------------|-----------------|  
|Interfaz dual ATL, interfaz personalizada e interfaz personalizada local|Especifique su propio nombre de método.|  
|Dispinterface de MFC|Especifique su propio nombre de método o seleccione uno de los nombres de método sugeridos en la lista.  Si selecciona un nombre de la lista, el valor apropiado aparecerá en el cuadro **Tipo de valor devuelto** y no se podrá cambiar.|  
|Dispinterface de controles ActiveX de MFC|Especifique el suyo propio o seleccione cualquiera de los métodos estándar [DoClick](../Topic/COleControl::DoClick.md) o [Refresh](../Topic/COleControl::Refresh.md).  Vea [Controles ActiveX de MFC: agregar métodos estándar](../mfc/mfc-activex-controls-adding-stock-methods.md) para obtener más información.|  
  
 **Tipo de método**  
 Esta opción sólo estará disponible para controles ActiveX de MFC.  Si, en lugar de seleccionar un método de la lista, se especifica un nombre de método en el cuadro **Nombre de método**, este cuadro no estará disponible.  
  
 Si selecciona uno de los métodos de la lista **Nombre de método**, elija entre una implementación estándar o una implementación personalizada.  
  
|Tipo de método|Descripción|  
|--------------------|-----------------|  
|**Estándar**|Es el formato predeterminado.  Inserta la implementación estándar del método seleccionado en la lista **Nombre de método**.  Si selecciona **Estándar**, no podrá cambiar **Tipo de valor devuelto**.|  
|**Personalizar**|Inserta una implementación de código auxiliar del método seleccionado en la lista **Nombre de método**.  Con los tipos de métodos personalizados, podrá especificar su propio tipo de valor devuelto o seleccionar uno de la lista **Tipo de valor devuelto**.|  
  
 **Nombre interno**  
 Disponible únicamente para métodos personalizados agregados a una interfaz dispinterface de MFC.  Permite definir el nombre utilizado en el mapa de envíos, el archivo de encabezado \(.h\) y el archivo de implementación \(.ccp\).  De forma predeterminada, este nombre coincidirá con el **Nombre de método**.  El nombre de método podrá cambiarse si se está trabajando con una interfaz dispinterface de MFC o si se está agregando un método personalizado a una interfaz dispinterface de controles ActiveX de MFC.  
  
|Tipo de interfaz|Descripción|  
|----------------------|-----------------|  
|Interfaz dual ATL, interfaz personalizada e interfaz personalizada local|No está disponible|  
|Dispinterface de MFC|De forma predeterminada, se utilizará el nombre de método.  El nombre interno podrá editarse.|  
|Dispinterface de controles ActiveX de MFC|El nombre interno sólo podrá definirse con métodos personalizados.  Los métodos estándar no utilizan nombre interno.|  
  
 **Atributos del parámetro**  
 Permite definir atributos adicionales para el parámetro especificado en **Nombre de parámetro**.  
  
|Atributo de parámetro|Descripción|Combinaciones permitidas|  
|---------------------------|-----------------|------------------------------|  
|**In**|Indica que el parámetro se pasa del procedimiento de llamada al procedimiento llamado.|Sólo **in**<br /><br /> **in** y **out**|  
|**Out**|Indica que el parámetro de puntero se devuelve desde el procedimiento llamado al procedimiento de llamada \(del servidor al cliente\).|Sólo **out**<br /><br /> **in** y **out**<br /><br /> **out** y **retval**|  
|**Retval**|Indica que el parámetro recibe el valor devuelto del miembro.|**retval** y out|  
  
 **Tipo de parámetro**  
 Permite definir el tipo de datos del parámetro.  Selecciónelo en la lista.  
  
 **Nombre de parámetro**  
 Establece el nombre de un parámetro que se va a pasar al método.  Después de escribir el nombre, se debe hacer clic en **Agregar** para agregarlo a la lista de parámetros que se pasarán al método.  Si no se especifica un nombre de parámetro, el asistente omitirá las selecciones de atributos de parámetro \(sólo ATL\) y de **Tipo de parámetro** efectuadas.  
  
 Después de hacer clic en **Agregar**, el nombre de parámetro aparece en la **Lista de parámetros**.  
  
 **Nota** Si especifica un nombre de parámetro y hace clic en **Finalizar** antes de hacer clic en **Agregar**, el parámetro no se agrega al método.  Deberá buscar el método e insertar el parámetro de forma manual.  
  
 **Agregar**  
 Agrega el parámetro especificado en **Nombre de parámetro**, así como su tipo y sus atributos de parámetro, a la **Lista de parámetros**.  Debe hacer clic en **Agregar** para agregar un parámetro a la lista.  
  
 **Remove**  
 Quita de la lista el parámetro seleccionado en **Lista de parámetros**.  
  
 **Lista de parámetros**  
 Muestra todos los parámetros y sus modificadores y tipos agregados actualmente al método.  A medida que se agregan parámetros, el asistente actualiza la **Lista de parámetros** para mostrar cada parámetro con su modificador y tipo.  
  
## Vea también  
 [Agregar un método](../ide/adding-a-method-visual-cpp.md)   
 [Atributos IDL, Asistente para agregar métodos](../ide/idl-attributes-add-method-wizard.md)