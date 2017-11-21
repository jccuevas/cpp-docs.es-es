---
title: "Asistente para componentes de páginas de Active Server ATL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.asp.overview
dev_langs: C++
helpviewer_keywords:
- ASP components, creating in ATL
- ATL Active Server Page Component Wizard
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 021740039044a43972cb51390ecf5cc1babdafe1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="atl-active-server-page-component-wizard"></a>Asistente para componentes de páginas Active Server ATL
Este asistente inserta en el proyecto de un componente de páginas Active Server (ASP). Microsoft Internet Information Services (IIS) usa componentes ASP como parte de su arquitectura de desarrollo de páginas Web.  
  
 Con este asistente, puede especificar que el componente de subprocesamiento del modelo y su compatibilidad con la agregación. También puede indicar la compatibilidad con la interfaz de información de errores, puntos de conexión y el cálculo de referencias de subprocesamiento libre.  
  
## <a name="remarks"></a>Comentarios  
 A partir de Visual Studio 2008, el script de registro generado por este asistente registrará sus componentes COM bajo **HKEY_CURRENT_USER** en lugar de **HKEY_LOCAL_MACHINE**. Para modificar este comportamiento, establezca la **registrar componente para todos los usuarios** opción del Asistente para ATL.  
  
## <a name="names"></a>Nombres  
 Especifique los nombres de objeto, interfaz y clases que se agrega al proyecto. Excepto para **nombre corto**, todos los demás cuadros pueden modificarse independientemente de las otras. Si cambia el texto para **nombre corto**, el cambio se reflejará en los nombres de todos los demás cuadros de esta página.  
  
 Si cambia la **coclase** nombre en la sección COM, el cambio se refleja en el **tipo** y **ProgID** cuadros, pero la **interfaz** nombre no cambia. Este comportamiento de nomenclatura está diseñado para que todos los nombres fácilmente identificables automáticamente a medida que desarrolla el control.  
  
### <a name="c"></a>C++  
 Proporciona información sobre la clase de C++ creada para el objeto.  
  
 **Nombre corto**  
 Establece el nombre de raíz para el objeto. El nombre que utilice determinará la `Class` y **coclase** nombres, el **archivo .cpp** y **archivo .h** nombres, el **interfaz**nombre, el **tipo** nombres y la **ProgID**, a menos que cambie estos campos individualmente.  
  
 **archivo .h**  
 Establece el nombre del archivo de encabezado para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que se proporciona en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección, o para anexar la declaración de clase a un archivo existente. Si selecciona un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le preguntará si para indicar si se debe anexar la declaración de clase para el contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.  
  
 **Clase**  
 Establece el nombre de la clase que se va a crear. Este nombre se basa en el nombre que se proporciona en **nombre corto**, precedido por 'C', el prefijo habitual en un nombre de clase.  
  
 **archivo .cpp**  
 Establece el nombre del archivo de implementación para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que se proporciona en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección. El archivo no se guarda en la ubicación seleccionada hasta que haga clic **finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le preguntará si para indicar si se debe anexar a la implementación de la clase para el contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.  
  
 **El atributo**  
 Indica si el objeto utiliza atributos. Si va a agregar un objeto a un proyecto ATL con atributos, esta opción está activada y no están disponibles para cambiar. Es decir, puede agregar solo los objetos con atributos a un proyecto creado con el soporte técnico de atributo.  
  
 Si selecciona esta opción para un proyecto ATL que no tiene compatibilidad atributo, el asistente le pide que especifique si desea agregar compatibilidad con atributos al proyecto.  
  
 De forma predeterminada para los proyectos sin atributos, cualquier objeto que agregue después de establecer esta opción se designará como con atributos (la casilla de verificación está seleccionada). Puede desactivar esta casilla para agregar un objeto que no utiliza atributos.  
  
 Vea [configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [mecanismos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.  
  
### <a name="com"></a>COM  
 Proporciona información acerca de la funcionalidad de COM para el objeto.  
  
 **(Coclase)**  
 Establece el nombre de la clase de componente que contiene una lista de interfaces que admite el objeto. Si su proyecto o este objeto utiliza atributos, no se puede cambiar esta opción, ya que ATL no incluye el **coclase** atributo.  
  
 **ype**  
 Establece la descripción del objeto que va a aparecer en el registro para la coclase.  
  
 **Interface**  
 Establece la interfaz que se crea para el objeto. Esta interfaz contiene los métodos personalizados.  
  
 **Id. de programa**  
 Establece el nombre que se pueden usar los contenedores en lugar del CLSID del objeto.  
  
## <a name="see-also"></a>Vea también  
 [Componentes de páginas Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)

