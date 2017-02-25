---
title: "Asistente para componentes de p&#225;ginas Active Server ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.asp.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ASP components, crear en ATL"
  - "Asistente para componentes de páginas Active Server ATL"
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Asistente para componentes de p&#225;ginas Active Server ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este asistente inserta en el proyecto un componente de páginas Active Server \(ASP\).  Microsoft Internet Information Services \(IIS\) utiliza los componentes ASP como parte de su arquitectura de programación de páginas Web.  
  
 Mediante este asistente, se puede especificar el modelo de subprocesos del componente y su compatibilidad con la agregación.  También es posible indicar la compatibilidad existente con la interfaz de información de errores, los puntos de conexión y el cálculo de referencias de subprocesamiento libre.  
  
## Comentarios  
 A partir de [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)], el script de registro generado por este asistente registrará sus componentes COM bajo **HKEY\_CURRENT\_USER** en lugar de bajo **HKEY\_LOCAL\_MACHINE**.  Para modificar este comportamiento, defina la opción **Registrar componente para todos los usuarios** del Asistente para ATL.  
  
## Nombres  
 Especifique el nombre del objeto, la interfaz y las clases que se agregarán al proyecto.  A excepción de **Nombre corto**, todos los demás cuadros pueden editarse de manera independiente de los demás.  Si cambia el texto de **Nombre corto**, el cambio repercutirá en los nombres de todos los demás cuadros de esta página.  
  
 Si cambia el nombre de **Coclase** en la sección COM, el cambio repercutirá en los cuadros **Tipo** y **ProgID**, pero el nombre de **Interfaz** no variará.  El comportamiento de nomenclatura está diseñado para que todos los nombres sean fácilmente identificables al crear los controles.  
  
### C\+\+  
 Proporciona información sobre la clase de C\+\+ creada para el objeto.  
  
 **Nombre corto**  
 Establece el nombre raíz del objeto.  El nombre que utilice determinará los nombres de `Class` y **Coclase**, los nombres de los archivos **.cpp** y **.h**, el nombre de **Interfaz** y los nombres de **Tipo** y **ProgID**, a menos que cambie estos campos individualmente.  
  
 **Archivo .H**  
 Establece el nombre del archivo de encabezado para la clase del nuevo objeto.  De forma predeterminada, este nombre se basa en el nombre que indique en **Nombre corto**.  Haga clic en el botón de los puntos suspensivos para guardar el nombre de archivo en la ubicación que desee o para anexar la declaración de la clase a un archivo existente.  Si selecciona un archivo ya existente, el asistente no lo guardará en la ubicación seleccionada hasta que seleccione **Finalizar** en el asistente.  
  
 El asistente no sobrescribe ningún archivo.  Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar** el asistente le preguntará si desea anexar la declaración de la clase al contenido del archivo.  Haga clic en **Sí** para anexar el archivo; haga clic en **No** para regresar al asistente y especificar otro nombre de archivo.  
  
 **Clase**  
 Establece el nombre de la clase que se creará.  Este nombre se basa en el nombre suministrado en **Nombre corto**, precedido por 'C', el prefijo habitual en un nombre de clase.  
  
 **Archivo .cpp**  
 Establece el nombre del archivo de implementación para la clase del nuevo objeto.  De forma predeterminada, este nombre se basa en el nombre que indique en **Nombre corto**.  Haga clic en el botón de los puntos suspensivos para guardar el nombre de archivo en la ubicación que desee.  El archivo no quedará guardado en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.  
  
 El asistente no sobrescribe ningún archivo.  Si selecciona el nombre de un archivo que ya existe, al hacer clic en **Finalizar**, el asistente solicitará que especifique si la implementación de la clase debe anexarse al contenido del archivo.  Haga clic en **Sí** para anexar el archivo; haga clic en **No** para regresar al asistente y especificar otro nombre de archivo.  
  
 **Con atributos**  
 Indica si el objeto usa atributos o no.  Si va a agregar un objeto a un proyecto ATL con atributos, esta opción estará activada y no se podrá modificar.  Es decir, sólo se pueden agregar objetos con atributos a un proyecto que sea compatible con atributos.  
  
 Si selecciona esta opción en un proyecto ATL que no acepta atributos, el asistente le pedirá que especifique si desea agregar al proyecto la compatibilidad con atributos.  
  
 Para los objetos sin atributos, cualquier objeto que agregue después de establecer esta opción se designará como poseedor de atributos de forma predeterminada \(la casilla aparece activada\).  Puede desactivar la casilla para agregar objetos que no usen atributos.  
  
 Para obtener más información, vea [Configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [Aspectos prácticos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md).  
  
### COM  
 Proporciona información acerca de la funcionalidad COM de un objeto.  
  
 **Coclase**  
 Establece el nombre de la clase componente que contiene una lista de las interfaces que acepta el objeto.  Si su proyecto o este objeto utilizan atributos, no se puede modificar esta opción, ya que ATL no incluye el atributo **Coclass**.  
  
 **Tipo**  
 Establece la descripción del objeto que aparecerá en el Registro para la coclase.  
  
 **Interfaz**  
 Establece la interfaz que se creará para nuestro objeto.  Esta interfaz contiene nuestros métodos personalizados.  
  
 **Id. de programa**  
 Establece el nombre que pueden usar los contenedores en lugar del CLSID del objeto.  
  
## Vea también  
 [ATL Active Server Page Component](../../atl/reference/adding-an-atl-active-server-page-component.md)