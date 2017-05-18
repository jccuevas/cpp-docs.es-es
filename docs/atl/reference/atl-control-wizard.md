---
title: Asistente para controles ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
caps.latest.revision: 17
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: 586ac14878ccd6908d025d706b72f3c9856d1b39
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="atl-control-wizard"></a>Asistente para controles ATL
Inserciones en un proyecto ATL (o un proyecto MFC con compatibilidad ATL) un control ATL. Puede usar a este asistente para insertar uno de los tres tipos de controles:  
  
-   Control estándar  
  
-   Control compuesto  
  
-   Control DHTML  
  
 Además, puede especificar un control mínimo, quitando las interfaces de la [Interfaces](../../atl/reference/interfaces-atl-control-wizard.md) lista, que se proporcionan como valores predeterminados para los controles en la mayoría de los contenedores. Puede establecer las interfaces que desea admitir para el control de la **Interfaces** página del asistente.  
  
## <a name="remarks"></a>Comentarios  
 El script de registro generado por este asistente registrará sus componentes COM bajo HKEY_CURRENT_USER en lugar de HKEY_LOCAL_MACHINE. Para modificar este comportamiento, establezca la **registrar componente para todos los usuarios** opción del Asistente para ATL.  
  
## <a name="names"></a>Nombres  
 Especifique los nombres para el objeto, interfaz y clases que se agregarán al proyecto. Excepción de **nombre corto**, todos los demás cuadros pueden cambiarse por separado. Si cambia el texto de **nombre corto**, el cambio se reflejará en los nombres de todos los demás cuadros de esta página. Si cambia la **coclase** nombre en la sección COM, el cambio se refleja en el **tipo** cuadro, pero la **interfaz** nombre y **ProgID** no cambian. El comportamiento de nomenclatura está diseñado para que todos los nombres fácilmente identificables que desarrollar el control.  
  
> [!NOTE]
>  **Coclase** es editable en sólo los controles sin atributos. Si su proyecto tiene atributos, no puede editar **coclase**.  
  
### <a name="c"></a>C++  
 Proporciona información para la clase de C++ creada para implementar el objeto.  
  
 **Nombre corto**  
 Establece el nombre abreviado del objeto. El nombre que proporcione determina la clase y **coclase** nombres, el archivo (. CPP y. H) nombres de, el nombre de la interfaz y el **tipo** nombres, a menos que cambie estos campos individualmente.  
  
 **(Clase)**  
 Establece el nombre de la clase que implementa el objeto. Este nombre se basa en el nombre que proporcione en **nombre corto**, precedido por 'C', el prefijo habitual en un nombre de clase.  
  
 **archivo .h**  
 Establece el nombre del archivo de encabezado para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que proporcione en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección, o para anexar la declaración de clase a un archivo existente. Si selecciona un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **finalizar**.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le pedirá que especifique si la declaración de clase debe anexarse al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.  
  
 **archivo .cpp**  
 Establece el nombre del archivo de implementación para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que proporcione en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección. El archivo no se guarda en la ubicación seleccionada hasta que haga clic **finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le pedirá que especifique si la implementación de la clase debe anexarse al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.  
  
 **Con atributos**  
 Indica si el objeto utiliza atributos. Si va a agregar un objeto a un proyecto ATL con atributos, esta opción está activada y no disponible para cambios. Es decir, puede agregar objetos con atributos solo a un proyecto creado con compatibilidad con atributos.  
  
 Puede agregar un objeto con atributos sólo a un proyecto ATL que utiliza atributos. Si selecciona esta opción para un proyecto ATL que no tiene el atributo admite, el asistente le pide que especifique si desea agregar compatibilidad con atributos al proyecto.  
  
 De forma predeterminada, cualquier objeto que agregue después de establecer esta opción se designará como con atributos (la casilla de verificación). Puede desactivar esta casilla para agregar un objeto que no utilice atributos.  
  
 Consulte [configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [aspectos prácticos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.  
  
### <a name="com"></a>COM  
 Proporciona información acerca de la funcionalidad de COM para el objeto.  
  
 **(Coclase)**  
 Establece el nombre de la clase de componente que contiene una lista de interfaces compatibles con el objeto.  
  
> [!NOTE]
>  Si crea el proyecto mediante atributos, o si indica en esta página del asistente que el control utiliza atributos, no puede cambiar esta opción, ya que ATL no incluye el **coclase** atributo.  
  
 **(Interfaz)**  
 Establece el nombre de la interfaz para el objeto. De forma predeterminada un nombre de interfaz llevan el prefijo "I".  
  
 **ype**  
 Establece la descripción del objeto que va a aparecer en el registro  
  
 **Id. de programa**  
 Establece el nombre que se pueden usar los contenedores en lugar del CLSID del objeto. Este campo no se rellena automáticamente. Si no rellena este campo manualmente, el control no esté disponible para otras herramientas. Por ejemplo, los controles ActiveX que se generan sin un `ProgID` no están disponibles en la **insertar ActiveX Control** cuadro de diálogo. Para obtener más información acerca del cuadro de diálogo, vea [cuadro de diálogo Insertar Control ActiveX](../../windows/insert-activex-control-dialog-box.md).  
  
## <a name="see-also"></a>Vea también  
 [Control ATL](../../atl/reference/adding-an-atl-control.md)   
 [Agregar funcionalidad al Control compuesto](../../atl/adding-functionality-to-the-composite-control.md)   
 [Fundamentos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)


