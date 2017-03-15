---
title: ATL COM + 1.0 de componente Asistente | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding components
- ATL COM+ 1.0 Component Wizard
ms.assetid: 11670681-8671-4122-96a4-2e52f8dadce0
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 2729975c5e823965f4f5c16d5bfe317ce10a3670
ms.lasthandoff: 02/24/2017

---
# <a name="atl-com-10-component-wizard"></a>Asistente para componentes ATL COM+ 1.0
Use este asistente para agregar un objeto al proyecto que admita servicios COM + 1.0, incluidas las transacciones.  
  
 Puede especificar si el objeto admite interfaces dobles y la automatización. También puede indicar la compatibilidad para la interfaz de información de errores, control de objetos mejorado, las transacciones y asincrónica message Queue Server.  
  
## <a name="remarks"></a>Comentarios  
 A partir de [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)], el script de registro generado por este asistente registrará sus componentes COM bajo **HKEY_CURRENT_USER** en lugar de **HKEY_LOCAL_MACHINE**. Para modificar este comportamiento, establezca la **registrar componente para todos los usuarios** opción del Asistente para ATL.  
  
## <a name="names"></a>Nombres  
 Especifique los nombres para el objeto, interfaz y clases que se agregarán al proyecto. Con la excepción de **nombre corto**, todos los demás cuadros pueden editarse independientemente de las otras. Si cambia el texto de **nombre corto**, el cambio se reflejará en los nombres de todos los demás cuadros de esta página. Si cambia la **coclase** nombre en la sección COM, el cambio se refleja en el **tipo** y **ProgID** cuadros, pero la **interfaz** nombre no cambia. El comportamiento de nomenclatura está diseñado para que todos los nombres fácilmente identificables que desarrollar el control.  
  
 **Nombre corto**  
 Establece el nombre abreviado del objeto. El nombre que utilice determinará el `Class` y `Coclass` nombres, el **archivo .cpp** y **archivo .h** nombres, el **interfaz** nombre, el **tipo** nombres y el **ProgID**, a menos que cambie estos campos individualmente.  
  
 **archivo .h**  
 Establece el nombre del archivo de encabezado para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que proporcione en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección, o para anexar la declaración de clase a un archivo existente. Si elige un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le pedirá que especifique si la declaración de clase debe anexarse al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.  
  
 **(Clase)**  
 Establece el nombre de la clase que se va a crear. Este nombre se basa en el nombre que proporcione en **nombre corto**, precedido por 'C', el prefijo habitual en un nombre de clase.  
  
 **archivo .cpp**  
 Establece el nombre del archivo de implementación para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que proporcione en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección. El archivo no se guarda en la ubicación seleccionada hasta que haga clic **finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le pedirá que especifique si la implementación de la clase debe anexarse al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.  
  
 **Con atributos**  
 Indica si el objeto utiliza atributos. Si va a agregar un objeto a un proyecto ATL con atributos, esta opción está activada y no disponible para cambios. Es decir, puede agregar objetos con atributos solo a un proyecto creado con compatibilidad con atributos.  
  
 Si selecciona esta opción para un proyecto ATL que no tiene el atributo admite, el asistente le pide que especifique si desea agregar compatibilidad con atributos al proyecto.  
  
 Cualquier objeto que agregue después de establecer esta opción se designará como con atributos (la casilla de verificación está seleccionada) de forma predeterminada. Puede desactivar esta casilla para agregar un objeto que no utilice atributos.  
  
 Consulte [configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [aspectos prácticos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.  
  
### <a name="com"></a>COM  
 Proporciona información acerca de la funcionalidad de COM para el objeto.  
  
 **(Coclase)**  
 Establece el nombre de la clase de componente que contiene una lista de interfaces compatibles con el objeto.  
  
> [!NOTE]
>  Si crea el proyecto mediante atributos, o si indica en esta página del asistente que el componente COM + 1.0 utiliza atributos, no puede cambiar esta opción, ya que ATL no incluye el `coclass` atributo.  
  
 **ype**  
 Establece la descripción del objeto que va a aparecer en el registro  
  
 **(Interfaz)**  
 Establece la interfaz que se crea para el objeto. Esta interfaz contiene nuestros métodos personalizados.  
  
 **Id. de programa**  
 Establece el nombre que se pueden usar los contenedores en lugar del CLSID del objeto.  
  
## <a name="see-also"></a>Vea también  
 [Componente ATL COM + 1.0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)


