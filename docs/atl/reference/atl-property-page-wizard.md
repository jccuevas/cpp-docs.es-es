---
title: "Asistente para p&#225;ginas de propiedades ATL | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.ppg.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL projects, agregar páginas de propiedades"
  - "Asistente para páginas de propiedades ATL"
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Asistente para p&#225;ginas de propiedades ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este asistente [agrega una página de propiedades a un proyecto ATL](../../atl/reference/adding-an-atl-property-page.md) o a un proyecto MFC compatible con ATL.  Una página de propiedades ATL proporciona una interfaz de usuario para configurar las propiedades \(o llamar a los métodos\) de uno o varios objetos COM.  
  
## Comentarios  
 A partir de [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)], el script de registro generado por este asistente registrará sus componentes COM bajo **HKEY\_CURRENT\_USER** en lugar de bajo **HKEY\_LOCAL\_MACHINE**.  Para modificar este comportamiento, defina la opción **Registrar componente para todos los usuarios** del Asistente para ATL.  
  
## Nombres  
 Especifique el nombre del objeto, la interfaz y las clases que se agregarán al proyecto.  A excepción de **Nombre corto**, todos los demás cuadros pueden editarse de manera independiente.  Si cambia el texto de **Nombre corto**, el cambio repercutirá en los nombres de todos los demás cuadros de esta página.  Si cambia el nombre de **Coclase** en la sección COM, el cambio se refleja en los cuadros **Tipo** y **ProgID**.  Este comportamiento de los nombres se ha diseñado para permitir una fácil identificación de los nombres cuando se desarrolla una página de propiedades.  
  
> [!NOTE]
>  **Coclase** es modificable sólo en proyectos sin atributos.  Si su proyecto tiene atributos, no podrá editar **Coclase**.  
  
### C\+\+  
 Suministra información de la clase de C\+\+ creada para implementar el objeto.  
  
|||  
|-|-|  
|Término|Definición|  
|**Nombre corto**|Define el nombre abreviado del objeto.  El nombre que suministre determinará el nombre de clase y de **Coclase**, los nombres de archivo \(**.cpp** y **.h**\), y el nombre de **Tipo** y el nombre de **ProgID**, salvo que modifique estos campos de forma individual.|  
|**Archivo .H**|Establece el nombre del archivo de encabezado para la clase del nuevo objeto.  De forma predeterminada, este nombre se basa en el nombre que indique en **Nombre corto**.  Haga clic en el botón de los puntos suspensivos para guardar el nombre de archivo en la ubicación que desee o para anexar la declaración de la clase a un archivo existente.  Si selecciona un archivo ya existente, el asistente no lo guardará en la ubicación seleccionada hasta que seleccione **Finalizar** en el asistente.<br /><br /> El asistente no sobrescribe ningún archivo.  Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar** el asistente le preguntará si desea anexar la declaración de la clase al contenido del archivo.  Haga clic en **Sí** para anexar el archivo; haga clic en **No** para regresar al asistente y especificar otro nombre de archivo.|  
|**Clase**|Establece el nombre de la clase que implementará el objeto.  Este nombre se basa en el nombre suministrado en **Nombre corto**, precedido por 'C', el prefijo habitual en un nombre de clase.|  
|**Archivo .cpp**|Establece el nombre del archivo de implementación para la clase del nuevo objeto.  De forma predeterminada, este nombre se basa en el nombre que indique en **Nombre corto**.  Haga clic en el botón de los puntos suspensivos para guardar el nombre de archivo en la ubicación que desee.  El archivo no quedará guardado en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.<br /><br /> El asistente no sobrescribe ningún archivo.  Si selecciona el nombre de un archivo que ya existe, al hacer clic en **Finalizar**, el asistente solicitará que especifique si la implementación de la clase debe anexarse al contenido del archivo.  Haga clic en **Sí** para anexar el archivo; haga clic en **No** para regresar al asistente y especificar otro nombre de archivo.|  
|**Con atributos**|Indica si el objeto usa atributos o no.  Si agrega un objeto a un proyecto ATL con atributos, esta opción está seleccionada y no disponible para cambios, es decir, sólo puede agregar objetos con atributos a los proyectos creados con ellos.<br /><br /> Solamente puede agregar objetos con atributos a un proyecto ATL que use atributos.  Si selecciona esta opción en un proyecto ATL que no acepta atributos, el asistente le pedirá que especifique si desea agregar al proyecto la compatibilidad con atributos.<br /><br /> De forma predeterminada, cualquier objeto que agregue después de configurar esta opción se designará como con atributos \(la casilla estará activada\).  Puede desactivar la casilla para agregar objetos que no usen atributos.<br /><br /> Para obtener más información, vea [Configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [Aspectos prácticos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md).|  
  
### COM  
 Proporciona información acerca de la funcionalidad COM de un objeto.  
  
 **Coclase**  
 Establece el nombre de la clase componente que contiene una lista de las interfaces que acepta el objeto.  
  
> [!NOTE]
>  Si crea el proyecto mediante atributos, o si indica en esta página del asistente que la página de propiedades utiliza atributos, no puede cambiar esta opción, ya que ATL no incluye el atributo `coclass`.  
  
 **Tipo**  
 Define la descripción del objeto que aparecerá en el Registro.  
  
 **Id. de programa**  
 Establece el nombre que pueden usar los contenedores en lugar del CLSID del objeto.  
  
## Vea también  
 [Opciones, Asistente para páginas de propiedades ATL](../../atl/reference/options-atl-property-page-wizard.md)   
 [Cadenas, Asistente para páginas de propiedades ATL](../../atl/reference/strings-atl-property-page-wizard.md)   
 [Example: Implementing a Property Page](../../atl/example-implementing-a-property-page.md)