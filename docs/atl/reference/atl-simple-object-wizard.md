---
title: Asistente para objetos simples ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.simple.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding objects
- ATL Simple Object Wizard
ms.assetid: f7f85741-9aad-4543-a917-a29b996364da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d2af751a136416934f378b41bed11b1aa74ad80
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883497"
---
# <a name="atl-simple-object-wizard"></a>Asistente para objetos simples ATL
Este asistente inserta en el proyecto de un objeto COM mínima. Utilice esta página del Asistente para especificar los nombres que identifican los archivos para el objeto y su funcionalidad COM y la clase de C++.  
  
 Use la [opciones](../../atl/reference/options-atl-simple-object-wizard.md) admiten la página de este asistente para especificar el modelo de subprocesos del objeto, su agregación, y si admite interfaces duales y automatización. También puede indicar la compatibilidad con la interfaz de la información de errores, puntos de conexión, soporte técnico para Internet Explorer y el cálculo de referencias de subprocesamiento libre.  
  
## <a name="remarks"></a>Comentarios  
 A partir de Visual Studio 2008, el script de registro generado por este asistente registrará sus componentes COM en **HKEY_CURRENT_USER** en lugar de **HKEY_LOCAL_MACHINE**. Para modificar este comportamiento, establezca el **registrar componentes para todos los usuarios** opción del Asistente para ATL.  
  
## <a name="names"></a>Nombres  
 Especifique los nombres para el objeto, interfaz y clases que se agregarán al proyecto. Excepto para **nombre corto**, todos los demás cuadros se pueden editar independientemente de los demás. Si cambia el texto para **nombre corto**, el cambio se refleja en los nombres de todos los demás cuadros de esta página. Si cambia el **coclase** nombre en la sección de COM, el cambio se refleja en el **tipo** y **ProgID** cuadros, pero la **interfaz** nombre no cambia. Este comportamiento de nomenclatura está diseñado para que todos los nombres fácilmente identificables por usted a medida que desarrolla el control.  
  
> [!NOTE]
>  **Coclase** es editable en sólo los proyectos sin atributos. Si su proyecto tiene atributos, no puede editar **coclase**.  
  
## <a name="c"></a>C++  
 Proporciona información sobre la clase de C++ creada para el objeto.  
  
 **Nombre corto**  
 Establece el nombre abreviado para el objeto. El nombre que proporcione determina la `Class` y `Coclass` nombres, el **archivo .cpp** y **archivo .h** nombres, el **interfaz** nombre, el **Tipo** nombres y el **ProgID**, a menos que cambie estos campos individualmente.  
  
 **Archivo .h**  
 Establece el nombre del archivo de encabezado para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el nombre que se proporciona en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija, o bien para anexar la declaración de clase a un archivo existente. Si selecciona un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la declaración de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.  
  
 **Clase**  
 Establece el nombre de la clase que se va a crear. Este nombre se basa en el nombre que se proporciona en **nombre corto**, precedidos por 'C', el prefijo habitual para un nombre de clase.  
  
 **Archivo .cpp**  
 Establece el nombre del archivo de implementación para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el nombre que se proporciona en **nombre corto**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija. El archivo no se guarda en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la implementación de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.  
  
 **Con atributos**  
 Indica si el objeto utiliza atributos. Si va a agregar un objeto a un proyecto ATL con atributos, esta opción está activada y no está disponible para cambiar. Es decir, puede agregar solo los objetos con atributos a un proyecto creado con el soporte técnico de atributo.  
  
 Puede agregar un objeto con atributos sólo a un proyecto ATL que utiliza atributos. Si selecciona esta opción para un proyecto ATL que no es compatible con atributos, el asistente le pedirá que especifique si desea agregar compatibilidad para el proyecto.  
  
 De forma predeterminada, cualquier objeto que agregue después de establecer esta opción se designará como con atributos (la casilla de verificación está seleccionada). Puede desactivar esta casilla para agregar un objeto que no utiliza atributos.  
  
 Consulte [configuración de la aplicación, Asistente para proyectos ATL](../../atl/reference/application-settings-atl-project-wizard.md) y [mecanismos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.  
  
## <a name="com"></a>COM  
 Proporciona información sobre la funcionalidad de COM para el objeto.  
  
 **Coclase**  
 Establece el nombre de la clase de componente que contiene una lista de interfaces que admite el objeto.  
  
> [!NOTE]
>  Si crea el proyecto mediante atributos, o si se indican en esta página del asistente que el objeto utiliza atributos, no se puede cambiar esta opción ya que ATL no incluye el `coclass` atributo.  
  
 **Type**  
 Establece la descripción del objeto que va a aparecer en el registro  
  
 **Interface**  
 Establece la interfaz que crea para el objeto. Esta interfaz contiene los métodos personalizados.  
  
 **Id. de programa**  
 Establece el nombre que se pueden usar los contenedores en lugar del CLSID del objeto.  
  
## <a name="see-also"></a>Vea también  
 [Objeto simple ATL](../../atl/reference/adding-an-atl-simple-object.md)

