---
title: Asistente para páginas de propiedades ATL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.ppg.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17c5d863ef14aeddcd66f813449b514360f657a4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359787"
---
# <a name="atl-property-page-wizard"></a>Asistente para páginas de propiedades ATL
Este asistente [agrega una página de propiedades en un proyecto ATL](../../atl/reference/adding-an-atl-property-page.md) o a un proyecto MFC con compatibilidad con ATL. Una página de propiedades ATL proporciona una interfaz de usuario para establecer las propiedades (o llamar a los métodos) de uno o más objetos COM.  
  
## <a name="remarks"></a>Comentarios  
 A partir de Visual Studio 2008, el script de registro generado por este asistente registrará sus componentes COM bajo **HKEY_CURRENT_USER** en lugar de **HKEY_LOCAL_MACHINE**. Para modificar este comportamiento, establezca la **registrar componente para todos los usuarios** opción del Asistente para ATL.  
  
## <a name="names"></a>Nombres  
 Especifique los nombres de objeto, interfaz y clases que se agrega al proyecto. Excepto para **nombre corto**, todos los demás cuadros pueden modificarse de forma independiente. Si cambia el texto para **nombre corto**, el cambio se reflejará en los nombres de todos los demás cuadros de esta página. Si cambia la **coclase** nombre en la sección COM, el cambio se refleja en el **tipo** y **ProgID** cuadros. Este comportamiento de nomenclatura está diseñado para que todos los nombres fácilmente identificables automáticamente a medida que desarrolla su página de propiedades.  
  
> [!NOTE]
>  **Coclase** es editable en sólo los proyectos sin atributos. Si su proyecto tiene atributos, no se puede editar **coclase**.  
  
### <a name="c"></a>C++  
 Proporciona información sobre la clase de C++ creada para implementar el objeto.  
  
|||  
|-|-|  
|Término|de esquema JSON|  
|**Nombre corto**|Establece el nombre abreviado para el objeto. El nombre que proporcione determina la clase y **coclase** nombres, el archivo (**.cpp** y **. h**), los nombres de la **tipo** nombre y el  **Id. de programa**, a menos que cambie estos campos individualmente.|  
|**archivo .h**|Establece el nombre del archivo de encabezado para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que se proporciona en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección, o para anexar la declaración de clase a un archivo existente. Si selecciona un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **finalizar** en el asistente.<br /><br /> El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le preguntará si para indicar si se debe anexar la declaración de clase para el contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.|  
|**Clase**|Establece el nombre de la clase que implementa el objeto. Este nombre se basa en el nombre que se proporciona en **nombre corto**, precedido por 'C', el prefijo habitual en un nombre de clase.|  
|**archivo .cpp**|Establece el nombre del archivo de implementación para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que se proporciona en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección. El archivo no se guarda en la ubicación seleccionada hasta que haga clic **finalizar** en el asistente.<br /><br /> El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le preguntará si para indicar si se debe anexar a la implementación de la clase para el contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.|  
|**El atributo**|Indica si el objeto utiliza atributos. Si va a agregar un objeto a un proyecto ATL con atributos, esta opción está seleccionada y no disponible para cambios, es decir, puede agregar solo objetos con atributos a un proyecto creado con el soporte técnico de atributo.<br /><br /> Puede agregar un objeto con atributos solo a un proyecto ATL que utiliza atributos. Si selecciona esta opción para un proyecto ATL que no tiene compatibilidad atributo, el asistente le pide que especifique si desea agregar compatibilidad con atributos al proyecto.<br /><br /> De forma predeterminada, cualquier objeto que agregue después de establecer esta opción se designará como con atributos (la casilla de verificación está seleccionada). Puede desactivar esta casilla para agregar un objeto que no utiliza atributos.<br /><br /> Vea [configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [mecanismos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.|  
  
### <a name="com"></a>COM  
 Proporciona información acerca de la funcionalidad de COM para el objeto.  
  
 **(Coclase)**  
 Establece el nombre de la clase de componente que contiene una lista de interfaces que admite el objeto.  
  
> [!NOTE]
>  Si crea el proyecto mediante atributos, o si se indican en esta página del asistente que la página de propiedades utiliza atributos, no se puede cambiar esta opción, ya que ATL no incluye el `coclass` atributo.  
  
 **Type**  
 Establece la descripción del objeto que va a aparecer en el registro  
  
 **Id. de programa**  
 Establece el nombre que se pueden usar los contenedores en lugar del CLSID del objeto.  
  
## <a name="see-also"></a>Vea también  
 [Opciones, Asistente para páginas de propiedades ATL](../../atl/reference/options-atl-property-page-wizard.md)   
 [Cadenas, Asistente para páginas de propiedades ATL](../../atl/reference/strings-atl-property-page-wizard.md)   
 [Ejemplo: Implementar una página de propiedades](../../atl/example-implementing-a-property-page.md)

