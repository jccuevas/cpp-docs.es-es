---
title: "Asistente para controles ATL | Microsoft Docs"
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
  - "vc.codewiz.class.atl.control.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para controles ATL"
  - "ATL projects, agregar controles"
  - "controles [ATL], agregar a proyectos"
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
caps.latest.revision: 17
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Asistente para controles ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Inserta un control ATL en un proyecto ATL \(o un proyecto MFC compatible con ATL\).  Puede usar este asistente para insertar uno de estos tres tipos de controles:  
  
-   Control estándar  
  
-   Control compuesto  
  
-   Control DHTML  
  
 Asimismo, se puede especificar un control mínimo, quitando las interfaces de la lista [Interfaces](../../atl/reference/interfaces-atl-control-wizard.md), que se proporcionan como predeterminadas para los controles en la mayoría de los contenedores.  Se pueden establecer las interfaces con las que se desea que sea compatible el control en la página **Interfaces** del asistente.  
  
## Comentarios  
 El script de registro generado por este asistente registrará sus componentes COM bajo HKEY\_CURRENT\_USER en lugar de HKEY\_LOCAL\_MACHINE.  Para modificar este comportamiento, defina la opción **Registrar componente para todos los usuarios** del Asistente para ATL.  
  
## Nombres  
 Especifique el nombre del objeto, la interfaz y las clases que se agregarán al proyecto.  A excepción de **Nombre corto**, todos los demás cuadros se pueden cambiar de manera independiente.  Si cambia el texto de **Nombre corto**, el cambio repercutirá en los nombres de todos los demás cuadros de esta página.  Si cambia el nombre de **Coclase** en la sección COM, el cambio repercutirá en el cuadro **Tipo**, pero el nombre **Interfaz** y **ProgID** no variarán.  El comportamiento de nomenclatura está diseñado para que todos los nombres sean fácilmente identificables al crear los controles.  
  
> [!NOTE]
>  **Coclase** es modificable sólo en controles sin atributos.  Si su proyecto tiene atributos, no podrá editar **Coclase**.  
  
### C\+\+  
 Suministra información de la clase de C\+\+ creada para implementar el objeto.  
  
 **Nombre corto**  
 Define el nombre abreviado del objeto.  El nombre que suministre determinará los nombres de clase y de **Coclase**, los nombres de archivo \(.CPP y .H\), el nombre de la interfaz y los nombres **Tipo**, salvo que modifique estos campos de forma individual.  
  
 **Clase**  
 Establece el nombre de la clase que implementará el objeto.  Este nombre se basa en el nombre suministrado en **Nombre corto**, precedido por 'C', el prefijo habitual en un nombre de clase.  
  
 **Archivo .H**  
 Establece el nombre del archivo de encabezado para la clase del nuevo objeto.  De forma predeterminada, este nombre se basa en el nombre que indique en **Nombre corto**.  Haga clic en el botón de los puntos suspensivos para guardar el nombre de archivo en la ubicación que desee o para anexar la declaración de la clase a un archivo existente.  Si selecciona un archivo ya existente, el asistente no lo guardará en la ubicación seleccionada hasta que seleccione **Finalizar**.  
  
 El asistente no sobrescribe ningún archivo.  Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar** el asistente le preguntará si desea anexar la declaración de la clase al contenido del archivo.  Haga clic en **Sí** para anexar el archivo; haga clic en **No** para regresar al asistente y especificar otro nombre de archivo.  
  
 **Archivo .cpp**  
 Establece el nombre del archivo de implementación para la clase del nuevo objeto.  De forma predeterminada, este nombre se basa en el nombre que indique en **Nombre corto**.  Haga clic en el botón de los puntos suspensivos para guardar el nombre de archivo en la ubicación que desee.  El archivo no quedará guardado en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.  
  
 El asistente no sobrescribe ningún archivo.  Si selecciona el nombre de un archivo que ya existe, al hacer clic en **Finalizar**, el asistente solicitará que especifique si la implementación de la clase debe anexarse al contenido del archivo.  Haga clic en **Sí** para anexar el archivo; haga clic en **No** para regresar al asistente y especificar otro nombre de archivo.  
  
 **Con atributos**  
 Indica si el objeto usa atributos o no.  Si va a agregar un objeto a un proyecto ATL con atributos, esta opción estará activada y no se podrá modificar.  Es decir, sólo se pueden agregar objetos con atributos a un proyecto que sea compatible con atributos.  
  
 Solamente puede agregar objetos con atributos a un proyecto ATL que use atributos.  Si selecciona esta opción en un proyecto ATL que no acepta atributos, el asistente le pedirá que especifique si desea agregar al proyecto la compatibilidad con atributos.  
  
 De forma predeterminada, cualquier objeto que agregue después de configurar esta opción se designará como con atributos \(la casilla estará activada\).  Puede desactivar la casilla para agregar objetos que no usen atributos.  
  
 Para obtener más información, vea [Configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [Aspectos prácticos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md).  
  
### COM  
 Proporciona información acerca de la funcionalidad COM de un objeto.  
  
 **Coclase**  
 Establece el nombre de la clase componente que contiene una lista de las interfaces que acepta el objeto.  
  
> [!NOTE]
>  Si crea el proyecto mediante atributos, o si indica en esta página del asistente que el control utiliza atributos, no puede cambiar esta opción, ya que ATL no incluye el atributo **coclase**.  
  
 **Interfaz**  
 Establece el nombre de la interfaz correspondiente al objeto.  De forma predeterminada, los nombres de interfaz llevan el prefijo "I".  
  
 **Tipo**  
 Define la descripción del objeto que aparecerá en el Registro.  
  
 **Id. de programa**  
 Establece el nombre que pueden usar los contenedores en lugar del CLSID del objeto.  Este campo automáticamente no se rellena.  Si no rellena este campo manualmente, el control puede no estar disponible para otras herramientas.  Por ejemplo, los controles ActiveX que se generan sin un `ProgID` no están disponibles en el cuadro de diálogo **Insertar control ActiveX**.  Para obtener más información sobre el cuadro de diálogo, vea [Insertar control ActiveX \(Cuadro de diálogo\)](../../mfc/insert-activex-control-dialog-box.md).  
  
## Vea también  
 [ATL Control](../../atl/reference/adding-an-atl-control.md)   
 [Adding Functionality to the Composite Control](../../atl/adding-functionality-to-the-composite-control.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)